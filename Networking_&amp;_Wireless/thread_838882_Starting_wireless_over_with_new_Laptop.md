---
title: "Starting wireless over with new Laptop"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by sparkyjoe34 on 2008-06-23
Hi Everyone,

I just recently received a new Dell Inspiron 1721 with AMD 64 Athlon X2 and wouldn't you know it....it has a Broadcom wireless card. :( 
Anyway, I was wanting to know what I need to do to get my wireless up and running? Here is my iwconfig:
```
joe@joe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

I know there are more commands that will be needed to figure out what type of wireless card I have but I can't remember what they are. Any help is much appreciated. Thanks guys.

---

### Post by chili555 on 2008-06-24
*sudo lshw -C network* will tell you which Broadcom you have. Search this forum for the zillion posts on how to get it working with either ndiswrapper or fw-cutter.

---

### Post by sparkyjoe34 on 2008-06-24
Thanks for the reply chili555.
Yeah I actually found a post about a Dell Inspiron 1720 which is basically the same as mine that I will try tonight when I get home. Hey what does "lshw -C" stand for? It will help me to remember the command.

---

### Post by issih on 2008-06-24
LiSt HardWare -Class network. Well thats what I think anyway.

ls is pretty much always list, so lsusb is list everything on the usb bus, lspci the pci bus, etc.

and ls all on its own lists files in the current directory.

Simple really :)

---

### Post by chili555 on 2008-06-24
> **issih said:**
> LiSt HardWare -Class network. Well thats what I think anyway.

ls is pretty much always list, so lsusb is list everything on the usb bus, lspci the pci bus, etc.

and ls all on its own lists files in the current directory.

Simple really :)Quite correct. You might also add *lspcmcia.* Some of these can be run with the flag *-v* or *-vv* meaning, be verbose and very verbose; that is, give all the details you can, including some that I don't even know what they mean!

---

