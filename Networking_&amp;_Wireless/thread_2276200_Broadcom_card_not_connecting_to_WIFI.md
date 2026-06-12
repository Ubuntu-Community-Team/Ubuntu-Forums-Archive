---
title: "Broadcom card not connecting to WIFI"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by aaron88 on 2015-04-30
Hi, I am brand new to Linux so my knowledge of what I am doing is very slim. 

I have a Dell Inspiron 13 (originally installed with Windows 8) that I have installed Unbuntu 14.04 using pendrivelinux.com

My Broadcom card is BCM43142 802.11b/g/n [14e4:4365] (rev 01)

Kernel driver in use: bcma-pci-bridge

I do not have access to ethernet on the laptop. 

I have downloaded bcmwl-kernel-source: Broadcom 802.11 Linux STA wireless driver source onto a USB drive.

What do I need to do from here to connect to the wifi?
Thank you for your help.
-Aaron

---

### Post by chili555 on 2015-04-30
You need to install bcmwl-kernel-source. I suggest, that to insure you have the correct version and its dependency dkms, you get the versions on the install USB. Please see here: [http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)

---

### Post by aaron88 on 2015-04-30
[ATTACH=CONFIG]261681[/ATTACH]

I was entering the commands as instructed and this is what came up...not sure what to do with that.

Thank you for your reply, I appreciate any help I can get.

EDIT: Just saw what I did...let me try again

---

### Post by aaron88 on 2015-04-30
[ATTACH=CONFIG]261682[/ATTACH]

Aaaaaand this is what I get....once again not sure what to do with this...

---

### Post by Bucky Ball on 2015-05-01
If you are running 14.04, your machine is well out of date. That release is using the 3.13.0-51 kernel now. You are on the 0-30! Do a complete update/upgrade and try again. Not sure if this your problem, but can't hurt.

If you can get online with a cable, run these in a terminal:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors and welcome to the forums! ;)

* Oh, just noticed you can't get ethernet to the box. Disregard and good luck.

---

### Post by aaron88 on 2015-05-01
Thanks for trying! Any idea why I'm getting the kernel package xxxxxxx not supported error?

---

### Post by chili555 on 2015-05-01
Please try these packages instead: [http://packages.ubuntu.com/utopic/bcmwl-kernel-source](http://packages.ubuntu.com/utopic/bcmwl-kernel-source) and also: [http://packages.ubuntu.com/utopic/dkms](http://packages.ubuntu.com/utopic/dkms)

In the case of bcmwl-kernel-source, be sure to get the package corresponding to your architecture; either 32- or 64-bit. Confirm:```
arch
```I'd delete the packages currently on your desktop, transfer these on a USB key or similar and install as before.

---

### Post by aaron88 on 2015-05-01
Very happy to say that I am replying to you now from Ubuntu and not Windows....thank you so much for all of your help. 

This really is a great community.

---

### Post by Bucky Ball on 2015-05-01
Good to hear you got there. Top effort by all with chili555 to the rescue once again. ;)

Enjoy the OS and the learning curve. ;)

---

### Post by chili555 on 2015-05-01
Glad it's working! Have fun.

---

