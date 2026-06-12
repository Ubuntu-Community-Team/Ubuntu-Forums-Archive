---
title: "Dell Inspiron 1501"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2013-11-21
I am deleting vista from this laptop for a friend but under lubuntu and xubuntu 13.10  32bit. I can't get ethernet or wireless to connect. I need a solution fast so I can finish setup and since I can't connect I can't install anything except by transferring it from a usb to the laptop thanks

---

### Post by ajgreeny on 2013-11-21
More details please on the chipset of the wireless adapter with the output of ```
sudo lshw -c network
``` which will help us help you.

---

### Post by cmcanulty on 2013-11-21
I spent all day and am really disappointed as I wanted them on linux not crappy vista but finally gave up on getting any internet and reinstalled vista. Not a very good result for ubuntu as I am fairly experienced but had to cut my losses. I thought Ethernet would be a no brainer and was willing to work and tweak for wireless but with nothing it was too hard. After I bragged about how good ubuntu is. And both lubuntu and xubuntu booted fast (it has 2GB ram) but no beginner could ever get this working.

---

### Post by Hadaka on 2013-11-22
Hi, if you are feeling ambitious, try this...more than
likely you answered YES to additional drivers. Dont do
that this time. That loads the wl driver,probably not the one
you want....so..please do..Reload OS...then..
just in case..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
you "should" now have a wired connection...*If yes then BOOT
and do from the wired connection connected to the internet..
```
sudo apt-get upates
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```..BOOT
hopefully you have both wired and wireless now.
yes??

---

### Post by cmcanulty on 2013-11-22
Thanks if it was my machine I would do but these people are beginners and could never cope with doing that in future so I put rotten vista back on. Linux should do kernel fixes for these issues rather than the endless screwing with the looks.One future linux ubuntu user gone.

---

