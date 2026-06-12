---
title: "Wubi And Kubuntu 8.04"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by shiloh pappy on 2009-02-03
How do I install Kubuntu 8.04 using Wubi?

---

### Post by halitech on 2009-02-03
I believe if you put the cd in while windows is running it will ask if you want to install it

---

### Post by shiloh pappy on 2009-02-03
Thanks I know about the install from the CD.  I want to dual boot with Window XP & Kubuntu 8.04 until I get used to Linux and then will just have Linux.  So I will have to use Wubi - - well since I'm completely new to Linux/Wubi I think that's what I'm suppose use to dual boot.

---

### Post by halitech on 2009-02-03
you don't have to use wubi but it does make it easier for initial setups

---

### Post by abn91c on 2009-02-03
defrag windows first, insert the cdrom in windows then click on the "install inside windows" button(thats Wubi)

---

### Post by shiloh pappy on 2009-02-04
Thanks I got it installed with dual boot.  Another question when I boot into Kunbuntu 8.04.1 it doesn't find my wireless network.  I tried with Network Manager to get it to find it and connect with no luck.  How do I get connected.

---

### Post by halitech on 2009-02-05
internal PCI card or usb external device? Does it find the device and is not finding any networks or is the device itself not being found? Also, any security on the router?

---

### Post by shiloh pappy on 2009-02-05
It is and internal PCI Card .. ****Network controller: Broadcom Corporation BCM4306 802.11 b/g Wireless Lan.

Device isn't being found nor any network.  No security on router which is a linksys G

---

### Post by halitech on 2009-02-07
open a terminal and post the output of
```
lspci
```and
```
lshw -C network
```

you probably need to install the B43 firmware. check here for more info

[http://ubuntuforums.org/showthread.php?t=1062350&highlight=b43](http://ubuntuforums.org/showthread.php?t=1062350&highlight=b43)

---

