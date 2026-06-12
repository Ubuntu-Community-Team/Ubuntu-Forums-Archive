---
title: "setting display manually."
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Napior on 2010-11-17
Hi everyone. this is my first experience with Linux, and I am trying to turn my old computer into a media server. I have searched the forum, as well as google, and I have been unsuccessful in finding a solution. When I attempt to boot into ubuntu, my screen enters sleep mode. I somehow entered a command prompt, and when i type in root, i get "root: can't figure out DISPLAY, set it manually" 
please help

EDIT: when I restart, the screen no longer sleeps, but I am only able to access this command prompt. it might be terminal. and I still get the same message when I type in root. ATI Radeon 9550 card, and no name monitor

---

### Post by dazman19 on 2010-11-18
I would suggest going to the ATI website.

If you have access to a terminal (CLI) then you can use wget to download files.
 I am assuming you have installed an 32bit version of linux not x64.
so start off with:
> 
wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)

then in the shell, as root run:
> 
sh ./ati-driver-installer-9-3-x86.x86_64.run


follow the setup instructions. Then give the machine a kick and restart it.

This should load your gui. If it doesn't you can try "startx" and see what error you get, and go from there..

IF this does not work you will need to edit the /etc/X11/xorg.conf file manually. I suggest looking at other threads on how to do this, and be prepared to do a bit of reading.

---

### Post by Napior on 2010-11-18
> **dazman19 said:**
> I would suggest going to the ATI website.

If you have access to a terminal (CLI) then you can use wget to download files.
 I am assuming you have installed an 32bit version of linux not x64.
so start off with:

then in the shell, as root run:


follow the setup instructions. Then give the machine a kick and restart it.

This should load your gui. If it doesn't you can try "startx" and see what error you get, and go from there..

IF this does not work you will need to edit the /etc/X11/xorg.conf file manually. I suggest looking at other threads on how to do this, and be prepared to do a bit of reading.

So your first suggestion did not help. however, upon entering "startx" i get "fatal server error: no screens found"

what's strange is that when I boot from the CD, everything works fine, but when I boot from my hard drive I get this problem

---

