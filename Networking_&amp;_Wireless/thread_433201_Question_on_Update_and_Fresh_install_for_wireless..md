---
title: "Question on Update and Fresh install for wireless."
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by victory2007 on 2007-05-04
Hi all,

I am in a bit of a pickle.  I updated to feisty via update manager and got my wireless working great.  So i decided to do a fresh install from the cd to clean a few things up.  After I did the install from the cd and do the same procedures to get my wireless card to work when i just did update manger, the card will not respond.  I have a broadcom card.  I have found many great post and topics but non of them have see to worked for me from a fresh install.  Any ideas.

Thanks

---

### Post by Floppyjoe on 2007-05-04
What version is your card?
```
lspci
```
Are you using ndiswrapper or not?
If Yes, Have you blaclisted the native bcm43xx driver?
```
sudo gedit /etc/modprobe.d/blacklist
```
add the words:
```
blacklist bcm43xx
```
If you are using ndiswrapper.


If you are using Feisty make sure you enable roaming mode in Sytem/Administration/Network for your wireless adapter.

---

### Post by victory2007 on 2007-05-04
I tried all of what you sugested before.  Roaming is setup but there is still no sign of the card working.

---

### Post by Floppyjoe on 2007-05-04
So what version is the card?
Are you using Ndiswrapper?
Are you using the bcm43xx driver with firmware?

---

### Post by victory2007 on 2007-05-05
It is revision 2.  I have tried both ndiswrapper and bcm43xx driver.  Seperatly of course.  I am still tinkering and retrying every thing.

---

### Post by Candace on 2007-05-05
Hi, 
These links work from a fresh Ubuntu 7.04 install on an HP dv2000 with wireless card Broadcom 1390 WLAN PCI. They might be worth a try. Or you can skim them and see what you are missing from them. They are very easy to follow though.
1. [http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505)
2. [http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

---

