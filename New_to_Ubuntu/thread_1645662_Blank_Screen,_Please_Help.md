---
title: "Blank Screen, Please Help"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Save-vs-DM on 2010-12-14
So I've  been trying to get compiz to work on my netbook (Inspiron Mini 10) according to this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

I got the drivers working fine but when I did this:

**Compiz**

 
sudo gedit /etc/X11/xorg.confand add the following option:  
Option "ExaNoComposite" "true"


It completely bricked things.  So I think I managed to uninstall compiz in the recovery console and then I used the failsafe xorg.conf file.  Now I can get past the load screen but things are completely blank.

Please help!

Also, here's the result of lspci | grep VGA

00:20.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

Edit: This is the Netbook Remix of 10.10

---

