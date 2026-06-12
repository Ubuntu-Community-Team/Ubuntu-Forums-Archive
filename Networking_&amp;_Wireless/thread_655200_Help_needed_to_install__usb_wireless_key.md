---
title: "Help needed to install  usb wireless key"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by FunkyBluffMan on 2008-01-01
Hi,

I have a SAFECOM 54MBps Wireless USB key ([http://safecom.cn/code/sub/category.asp?subcatid=41&prdid=370#](http://safecom.cn/code/sub/category.asp?subcatid=41&prdid=370#)) that I want to install. I did see on the manufactures site that they had linux drivers. However, I relatively new to linux/ubuntu and not sure how to install these new drivers. 

On my Windose XP I have it setup to use WPA am I right in thinking that the standard linux drivers do not support WPA?

I currently have Ubuntu 6.06 LTS desktop edition. 

Many thanks for the great support provided.

---

### Post by howto on 2008-01-01
No need to download anything as ubuntu already ships with this driver.

Open a command prompt from your menus Applications -> Accessories -> Terminal

Then type -->  sudo modprobe zd1211rw

That should load the driver for that chipset and to check that it has you can issue the iwconfig command without parameters. You should now be able to use the Network Manager tool to finish configuring the device.

HTH

---

### Post by FunkyBluffMan on 2008-01-01
when I typed ```
sudo modprobe zd1211rw
``` into the terminal I got the following error message **FATAL: Module zd1211rw not found.**.
I downloaded ubuntu straight from this site I have kernel 2.6.15

---

### Post by howto on 2008-01-01
You would have far fewer problems if you downloaded and installed the latest Ubuntu release.

It's codename is gutsy 7.10

This release has the driver for your nic and many many enhancements.

---

### Post by kevdog on 2008-01-01
Im not certain but Im betting the drivers you are talking about are distributed as source code that you will need to compile!  In this case you will need to download the source and compile the driver (this really isnt that hard as long as you have installed the build-essential and linux-headers-`uname -r` packages since these are required to compile from source).  Ive personally never compiled the drivers you speak off, however have lots of experience compiling other drivers and such.  I can help you if you want.  -- again another option would be to use the gutsy kernel or upgrade your kernel to gutsy (this does not require a reinstallation) -- or simply start fresh (wipe everything) and install gutsy from disk.  Your choice!

---

### Post by FunkyBluffMan on 2008-01-02
Hi Kevdog,

Is there any difference in  navigation/GUI icons etc in the gutsy version?
Its just that I'm starting to learn Linux and have found myself an Apress book for Ubuntu novice to pro which refers to this version. If not and its just enhancements then is there an easy way to download and upgrade straight from 6.06 - 7.10 or do I have to download the iso burn to cd and then reinstall/upgrade?

Thanks for your support.

---

