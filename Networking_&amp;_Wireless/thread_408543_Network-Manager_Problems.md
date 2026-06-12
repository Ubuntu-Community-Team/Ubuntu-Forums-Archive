---
title: "Network-Manager Problems"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by Sugi on 2007-04-13
I'm pretty much new to linux, though I do have a small history with linux.  So giving direction to me please make them with a lot of details.

I'm trying to download packages, but I got no internet within ubuntu.  So take in mind that I'm downloading everything within my windows boot (im dual booting)

First, I'm trying to install the Network-manager so I can get internet (so i can do updates), but I'm having problems with that.
I've tryed downloading "network-manager_0.6.3-2ubuntu6_i386.deb" and i think it's called "network-manager_0.6.3-0ubuntu6_i386.deb" neither worked.  I get some crappy errer.  Something about the lib file or whatever.  If you need more details, just let me know. >.<


Links that I used for reference:
wireless
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
WPA
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)
asus
[http://ubuntuforums.org/showthread.php?p=2330967](http://ubuntuforums.org/showthread.php?p=2330967)

---

### Post by spd106 on 2007-04-13
The guy in another thread had the same problem, this post lists the dependencies.
[http://ubuntuforums.org/showthread.php?p=2415484&postcount=4](http://ubuntuforums.org/showthread.php?p=2415484&postcount=4)

---

### Post by Sugi on 2007-04-14
Oh, big thanks!!!  This should fully help me!  Thanks again.

---

### Post by Sugi on 2007-04-14
I also tryed the command lines, but I don't have a copy of the reports with me right now.  I''ll update them the next time I can.

> Code:

sudo modprobe ath_pci

lsmod | grep ath

sudo lshw -class network



I installed the 
"ibnl1-pre6
libnm-util0
dhcdbd"
and "network-manager" but I get a new error now.

Status:  Error:.. Network-manager

I didn't install the "linux-restricted-modules-generic package", because I never got that error.

What should I do now???

---

### Post by Sugi on 2007-04-14
I uninstalled "linux-restricted-modules-generic" package hoping to reinstall the package, but by doing this, i couldn't find the same package to reinstall it.  How do I go about reinstalling it?  If I reinstall "linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i386.deb" would that fix the problem?

---

### Post by spd106 on 2007-04-14
You won't need the restricted modules package unless you have an Atheros based wifi card. Network Manager doesn't depend on it.

---

### Post by Sugi on 2007-04-15
......so,  I uninstalled "linux-restricted-modules-generic" and that didn't hurt anything???  The packaged "linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i386.deb" I did install?  Is that oh kay?



I got all the files "ibnl1-pre6, libnm-util0, dhcdbd" install and the "network-manager_0.6.3-2ubuntu6_i386.deb" installed.  I couldn't find the program in my apps.  Where would it be?

Note:  I installed "network-manager_0.6.3-2ubuntu6_i386.deb" not  "network-manager-gnome_0.6.3-2ubuntu6_i386.deb".  The file "network-manager-gnome_0.6.3-2ubuntu6_i386.deb" is what you said to download, but I couldn't get it to work, because the status said there was some problem with the error.  But The  "network-manager_0.6.3-2ubuntu6_i386.deb" package did work, but I can't find it in my ubuntu now.

What now?

---

### Post by spd106 on 2007-04-16
You need to install both packages. Network-manager first, then network-manager-gnome.

Follow the instructions at this wiki page to configure it [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Jouke74 on 2007-04-16
Most packages you are looking for are on the Ubuntu install cd. Open synaptic package manager and check the Ubuntu CDROM in the menu. Then you can install most from CD instead of redownloading the packages. Getting internet to run depends a lot on your hardware, which you did not list.

---

### Post by spd106 on 2007-04-16
Just to clarify, Network Manager and it's dependencies are on the Alternate cd and the DVD, but not the Desktop cd for Ubuntu 6.10 (Edgy). The same goes for Ubuntu 6.06 (Dapper).

---

### Post by Sugi on 2007-04-26
spd106, with the new ubuntu feisty fawn 7.04, it had the network manager within it.  so that solve one problem of getting internet wireless, but only free internet.  I'm currently having with problems with getting internet through wireless networks with keys, but even though i have the corrent keys.  It's not letting me join still.

Jouke74,  Sorry, I have an ASUS G1 Laptop.  I switch over to Feisty Fawn 7.04, but my old p3 is still at the last update. :-/  So, through other post I heard the laptop is really good with linux, but theres some problem with the built-in cam and mic, but I haven't got around to trying that out yet.


I haven't really seen any tutorials on getting into wireless networks with keys.  If there is a really good tutorial, please let me know.

Thanks,
Sugi

---

