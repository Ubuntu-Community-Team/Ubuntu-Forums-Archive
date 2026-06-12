---
title: "fresh install / error code"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by WillWhy on 2011-08-26
I have ubuntu 8.04 as my primary (only) OS and would like to do a fresh install of 10.04. I'm very new to linux and don't know where to start.

I have tried loading the iso file onto a thumb drive and booting from the thumb drive but the system ignores the usb drive and loads to the user screen.

Am I supposed to delete my current install first? or
Format the thumb drive in some special way to make it recognizable as a bootable source?

SIDE NOTE
The only reason I'm doing this is to not only have the newest LTS but also to get rid of this error -

E: /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.5_all.deb: subprocess pre-installation script returned error exit status 1

That error prevents me from installing new.

---

### Post by wildmanne39 on 2011-08-26
Hi, you need to make the drive bootable, you can put ubuntu on your usb drive by using start up disk creator if it is installed in 8.04 or follow the directions on the ubuntu download site.

Also in bios when you start your computer you need to set it to boot the usb drive first.

---

### Post by JC Cheloven on 2011-08-26
> **WillWhy said:**
> (...)
SIDE NOTE
The only reason I'm doing this is to not only have the newest LTS but also to get rid of this error -

E: /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.5_all.deb: subprocess pre-installation script returned error exit status 1

That error prevents me from installing new.

In addition to wildmanne's answer to you main question, you should be given the option to update from good old Hardy Heron 8.04 to new lts Lucid Lynx 10.04 when you check for software updates. The error above you report shouldn't prevent the system from that (well, I can't think of a reason for it to prevent updating; I wonder if your "prevents me from installing new" bit is about that).
So, have you tried to simply click on system - check for updates ?

---

