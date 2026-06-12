---
title: "usb partition q"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by neil_1 on 2011-03-14
just a question
can i make a partition on my usb (install live ubuntu as well as bt4) ?
if so how ?:confused:

edit:
i currently have bt4 live on my usb

---

### Post by neil_1 on 2011-03-21
:bump:
no one at all ?

---

### Post by HermanAB on 2011-03-21
Howdy,

You make partitions with fdisk and create a filesystem on a partition with mkfs. The below is for illustrative purposes only.  using these utilities, you can format the wrong partition and totally **** up your system.  

Read the man pages first. Don't complain to me if your cows produce sour milk, your goat has a five legged kid or your system bursts into fire and burns your house down...

Something like this:
Plug stick in.
When he automounter pops up something, don't mount it.

Run dmesg to see what the name of the stick is:
$ dmesg
It will be something like /dev/sdb

Make a partition:
$ sudo fdisk /dev/sdb
n
p
enter
enter
w

Make file system:
$ sudo mkfs.vfat /dev/sdb1

---

### Post by Hedgehog1 on 2011-03-21
> **HermanAB said:**
> Read the man pages first. Don't complain to me if your cows produce sour milk, your goat has a five legged kid or your system bursts into fire and burns your house down...


HermanAB - You are just too funny.  *I need to remember this disclaimer!*

neil_1,

There is a tool for this, and here is the page for multi-boot of LiveCD's:

[boot-multiple-iso-from-usb]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/")

This ***MIGHT*** reduce the chances of your system bursting into flames...  :D

***The Hedge***

:KS

---

### Post by neil_1 on 2011-03-21
lol @ HermanAB 
thanks guys ,
but what about persistance ?
wont the 2 os's get confused ?

---

### Post by Hedgehog1 on 2011-03-22
> **neil_1 said:**
> lol @ HermanAB 
thanks guys ,
but what about persistance ?
wont the 2 os's get confused ?

That one you might have to test yourself and let us all know.  :D

You can do a real dual boot by installing bt4 (real install) on the USB, and then do a real install of Ubuntu.  Then you could dual boot from the USB, grub menu and all.

A true dual boot does take more space on the USB.  But it also means you can update the OSes.  Just a thought.

***The Hedge***

:KS

---

### Post by neil_1 on 2011-03-24
tried the way you and hermanab showed me and it worked 
then i tried for persistence and both the os's had a boot eror lol :/
i think they got confused with whose is  the casper-rw :(
anyways thanks :)

---

