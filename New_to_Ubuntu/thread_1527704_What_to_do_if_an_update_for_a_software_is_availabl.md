---
title: "What to do if an update for a software is available, but not in the repository?"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Rumtscho on 2010-07-09
I am a Calibre user, and despite my shiny new hardware, I have severe performance issues. The change log suggests that they have been addressed in calibre 0.7, but for Lucid, only Calibre 0.6.42 is available, and I don't think it will be updated. The author of Calibre offers a binary installer for some Linux distributions, including Ubuntu. 

Now I don't know what will happen if I use the binary installer. Will it update my current version? Will it break it? Will it replace it? Will it try to install itself in parallel? How big is the risk that something will go wrong? As my library is quite big, I've already spent dozens of hours on sorting books and hunting down the appropriate metadata, and don't want to start from scratch if the installation goes wrong. I've thought of backing up the DB, uninstalling Calibre from apt, then running the binary installer and copying the DB into the new installation. But I don't know if the new version can read the old DB, maybe a proper update process would change the DB structure too. 

So what is the appropriate thing to do when I need newer software but I cannot get it over apt? Is mixing installations a big risk? I am afraid to try, because if I get 0.7 through the binary installer, I don't know if I can uninstall it and install 0.6.42 through apt again.

Edit: i don't know if it is a .deb. I am supposed to run 
```
sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"
                        
``` regardless of my distribution. I know that there are some binary installers which don't use a .deb (e. g. the Aquaria one) so I just don't know what will happen.

---

### Post by jtarin on 2010-07-09
If the new install is packaged as a .deb file then it should be no problem installing and uninstalling it with any of the apt/synaptic tools.

---

### Post by gandaran on 2010-07-09
if it's a .deb file theres no problem, it will just replace the existing install with the updated one.
if its some other type of file it's better to remove the .deb installed first to avoid any possible incompatibility.

---

### Post by steveneddy on 2010-07-09
Installing the ppa for this software is much easier - but you may want to list your OS as the nexr version - but that again is the development version.

Here's the link:

[https://launchpad.net/ubuntu/+source/calibre](https://launchpad.net/ubuntu/+source/calibre)

---

### Post by Rumtscho on 2010-07-11
Figured out how to do it. Made a LiveUSB and tried the upgrade there. After it didn't break, did it on the normal OS too. 

It wasn't a .deb, but it was smart enough to upgrade the existing Calibre. I'm just happy some developers think of the users more than just giving them a wad of source code :)

---

