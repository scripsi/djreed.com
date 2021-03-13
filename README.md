# djreed.com

This is the [djreed.com](https://djreed.com) website development repository.

The website is a single page virtual business card that links to my other sites and accounts. It is written in pure HTML and CSS. A GitHub Action deploys the website to hosting automatically whenever I use `git push` from my local copy.

This file just reminds me how things are configured and what to do to run the site.

## Developing content

Just edit the index.html file and test locally in a web browser.

The background svg was created in Inkscape, text edited to remove unnecessary styling and then url-encoded on [this site](https://yoksel.github.io/url-encoder/)

The font is subsetted and embedded in the CSS. If you change the text you will have to update the subset. Make sure you have [fonttools](https://github.com/fonttools/fonttools) installed:

```shell
sudo apt install fonttools
```

 Edit the `dev/font/buildfont` script with the new subset and run it. then copy and paste the text from `dev/font/djreed-font.b64.txt` into `index.html`

## Committing content

``` shell
git add .
git commit -m "commit message"
git push
```

## Github Action

The website is copied to the web hosting by a GitHub Action.

The action is configured in `.github/workflows/deploy-to-hosting.yml`, and it is only triggered on a push to the `main` branch of the repository.

The settings are stored in the GitHub repository's settings -> secrets menu. Use the `New Repository Secret` button to add the following secrets:

* HOST - the sftp host to upload the website to
* USERNAME - the username to use for sftp
* PASSWORD - the password to use for sftp
* PORT - the port to use for sftp - usually 22
