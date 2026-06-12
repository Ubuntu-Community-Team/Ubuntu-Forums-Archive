---
title: "Install .deb files"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by dedikcr on 2009-12-15
I'm trying to install some software and I get errors.
For example I try to install RSSOwl from [http://www.getdeb.net/updates/Ubuntu/all?page=13](http://www.getdeb.net/updates/Ubuntu/all?page=13).
The system starts to download the packages information, but at the end it says "Could not find 'rssowl' "
It happen the same with other software from getdeb.net.
I didn't try any other site

---

### Post by Tibuda on 2009-12-15
This is because getdeb have changed how it works. They don't have .deb files to download anymore, but now they have their own repository. See [http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install):
> Use the following instructions:
1. Install the [getdeb]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb") package.
2. Or configure the repository manually:
Go to System-Administration-Software Sources, Third-Party Software tab, Add:
```
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```
Add the repository GPG key, open a terminal window and type:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```
3. Click the "Install this now" button below the screenshot of the desired application.
hide this from showing in the future

---

### Post by philinux on 2009-12-15
[http://www.rssowl.org/](http://www.rssowl.org/)

---

