---
title: "Will installing the Edubuntu addon disc work with Kubuntu installed?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by eanx on 2009-05-03
And if it does, will it change my desktop appearance? Also how would I uninstall it if I don't like it? 

BTW, I'm installing it in a virtual machine using VirtualBox.

---

### Post by aysiu on 2009-05-04
It may install Gnome, but as long as you're using KDE still the interface should be the same.

To install it, paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install edubuntu-desktop
``` Before you say *yes*, highlight the list of all the packages to be installed and then copy and paste them into a text document.

If you decide later that you don't like Edubuntu, then run the command ```
sudo apt-get remove _____________ && sudo apt-get install kubuntu-desktop
``` where _____________ is the list of all the packages from the text document.

---

### Post by eanx on 2009-05-04
Installing it now, I had some trouble installing guest additions from VirtualBox.

Thanks

---

