---
title: "Can't Install Ralink RT3290 Driver on Ubunto 18.10"
date: 2018-11-12
forum: Networking &amp; Wireless
---

### Post by hamood95 on 2018-11-12
HI all

I am trying to install WIFI driver.
When trying to install [firmware-misc-nonfree]("https://packages.debian.org/stretch/firmware-misc-nonfree")[ ]("https://packages.debian.org/stretch/firmware-misc-nonfree")package I get this error: 
> 
ham@ubuntu:~$ sudo  apt-get install firmware-misc-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firmware-misc-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

 
The Ethernet works out of the box but not the WIFI.

the report I did is **[here]("http://paste.ubuntu.com/p/VjQSwhpxjH/")**.

---

### Post by jeremy31 on 2018-11-12
You appear to be using Ubuntu in a VM and the VM is not allowing Ubuntu access to your PCI wifi card.  You will need a USB wireless device if you wish to control it from a VM guest OS

---

### Post by hamood95 on 2018-11-12
[CENTER]oh really
I thought that is possible

Thanks for your help anyway.
[/CENTER]

---

