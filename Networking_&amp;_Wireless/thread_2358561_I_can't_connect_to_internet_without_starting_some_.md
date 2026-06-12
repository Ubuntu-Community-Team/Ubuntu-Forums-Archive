---
title: "I can't connect to internet without starting some programs"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by cirelli94 on 2017-04-14
[FONT=arial]I just installed XUbuntu 17.04, for using it as a little home theater/kodi etc.. But I have a little problem!
I can't acces to internet if I don't start Mozilla Firefox! Wifi is connected, so I can even ssh to this pc, but for example I can't ping from the local console to google, and some other programs, like Kodi, can't access internet! But if I start a search via Mozilla, everything start working!
What should I do?

Thanks for your help[/FONT]

---

### Post by wildmanne39 on 2017-04-14
What version of network manager are you using? please do:
> dpkg -s network-manager | grep Version
post the results here.
Thanks

---

### Post by wildmanne39 on 2017-04-14
It is a bug in network manager, their has been an updated version of network manager released that should fix the issue, but we may have to update another application as well. 

Go [here](https://launchpad.net/ubuntu/+source/network-manager/1.4.4-1ubuntu3) and download network-manager_1.4.4.orig.tar.xz then drag and drop it on your Ubuntu Desktop, then right click and select extract here.
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms
cd Desktop/NetworkManager-1.4.4
./configure && make && make install
```
Watch for errors, warnings are okay.
Reboot

---

### Post by cirelli94 on 2017-04-15
> dpkg -s network-manager | grep Version
Version: 1.4.4-1ubuntu3


I had to install:
>  intltool
gio-unix
libglib2.0-dev
libdbus-glib-1-dev
   libgudev-1.0-dev
libnl-3-dev
uuid-dev
libnss3-dev
libndp-dev
libreadline-dev
libncurses-dev

at in the end, after a 30 minutes of error / install new package etc.. It is compiling!
I did `sudo make install` at the end because I thought that was right... 
But this do not solve my problem! I installed another distro, I needed it urgently. Thanks by the way

---

### Post by wildmanne39 on 2017-04-15
> I installed another distro, I needed it urgently
Did that solve your issue?

---

