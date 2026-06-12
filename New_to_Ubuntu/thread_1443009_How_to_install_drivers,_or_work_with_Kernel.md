---
title: "How to install drivers, or work with Kernel?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by mina299 on 2010-03-30
Hey, all!  I'm not new to Ubuntu, but I have never tried to modify it or add drivers, and now that I have to, I'm lost!

I have searched through many threads and can't find what I need.  As a novice, this is all gibberish to me.  If there is a thread that I missed that explains everything, please link me to it. :)  I even downloaded the introductory pocket guide from the beginners pages and read through almost all of it and could not find anything that helped me.

Right, so I am trying to get an older Logitech webcam working (came with a CD: Quick Cam Express, Logitech v5.2.1).  I am using Ubuntu 9.04.

I would love to install the drivers via this disc; however, it obviously doesn't even begin to allow that.  If there is something I can try, please let me know - I have already tried to look for **help with drivers**, and a more promising thread was this:

[http://ubuntuforums.org/showthread.php?t=53755&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=53755&highlight=Logitech+QuickCam)

However I look at it, I can't even get started, because I don't know how to access Kernel.  I don't know how to access anything outside of the menus on the bar.  Can anyone break this down for me?  I don't mean to be a noob, and everyone starts somewhere.  I'm sure within a few months I'll have this all under my belt and I'll be customizing this thing inside-out and backwards.

Any help is very,* very* much appreciated.  Thank you in advance. :P

~The Noobcake.

---

### Post by Paqman on 2010-03-30
> **mina299 said:**
> 
However I look at it, I can't even get started, because I don't know how to access Kernel.  I don't know how to access anything outside of the menus on the bar.

The commands given in that guide need to be pasted into a terminal window. You can find the terminal at Applications > Accessories. Just paste them on one line at a time. The first time you try to enter a command starting with "sudo" it will prompt for a password, just type in the password you use to log in. You won't get any indication on screen when you hit the keys, this is normal.

---

### Post by lavinog on 2010-03-30
The cd that came with the cam is for windows only.
Linux should have the drivers built in already.

please type the following command in the terminal while the cam is connected:
```
lsusb
```
and post it here.

You might be just looking for webcam software...in which case use the add/remove menu item and search for webcam.  Cheese might work with your cam, give it a try to test your cam out.

also what are you wanting to do with your camera?

---

### Post by Dunchillin on 2010-05-05
Hi guys,
I'm having the same issues getting a new logitech C250 to run.  I have followed the instructions in the linked thread as best I could and it *has *made the camera work in some places, such as Cheese, but not in others such as Camorama.  I also tried a test in a video chat forum but it (the site) couldn't find a camera signal on my system.

When I typed the above suggestion into terminal I get:

> Bus 003 Device 004: ID 046d:0804 Logitech, Inc. 
Bus 003 Device 003: ID 03f0:7111 Hewlett-Packard 
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can't find the add/remove menu!    When I try to open Camorama I get an error message: > Could not connect to /dev/video0 Please check connection

Any help appreciated.  I really have spent the last 2 days trawling through other threads trying to find a solution, cos I know how everyone hates the same questions getting asked over and over, but I can't find one!  I've also been through the logitech linux support pages and downloaded v4l-dvb drivers...but then have no idea what to do with them once they were downloaded!  The command instructions given on the same site didn't seem to do anything.

Thanks

---

### Post by lavinog on 2010-05-05
> **Dunchillin said:**
> Hi guys,
Can't find the add/remove menu!    When I try to open Camorama I get an error message: 

It is called ubuntu software center in lucid

---

