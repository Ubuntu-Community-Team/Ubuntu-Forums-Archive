---
title: "Bluetooth Help PLEASE"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by itsme_n8 on 2008-04-14
Hi all.  I'm trying to get my Insignia Bluetooth Wireless Headset Model number NS-BTHDST to work on my Lenovo Thinkpad T61p running Ubuntu 7.10 (64 bit).  I would like to get this to work, however I cannot.  I get this error when I try to connect the headset:  
Couldn't display "obex://[00:1c:ef:19:6f:fa]".
Check if the service is available.

I have tried updating my system, and have tried to install Blueman, as this seemed very highly recommended from what I've been reading, however I can't install that.  When I try I get the following:

blueman:
  Depends: bluez-utils (>=3.20) but 3.19-0ubuntu3 is to be installed
___________________________________________________________________
bluez-utils:
  Depends: libc6 (>=2.7-1) but 2.6.1-1ubuntu10 is to be installed

however there is no 2.7.1 listed to upgrade libc6 to.  WTF?


I've tried the following from another thread  [http://www.uluga.ubuntuforums.org/showthread.php?t=640343]("http://www.uluga.ubuntuforums.org/showthread.php?t=640343")
```
sudo apt-get install gnome-vfs-obexftp
```

That did nothing.
That post also made reference to: [http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html]("http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html"), however as that is related to pairing a keyboard/mouse, so I opted not to do it.

Please help, this is one of the few things I need to wrap up so I wont need to use Windows anymore.  If I've missed something stupid fine... please point it out... I just want this to work.

I'm a Linux noob, so please speak slowly :)

---

