---
title: "No internet connection (Ubuntu 12.04.3)"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by King Dude on 2013-11-10
So my friend and I decided to swap the operating system on his computer, switching the OS from Windows to Linux. But now his laptop cannot connect to the internet, not even via a wired connection. I'm pretty sure it's because I don't have a driver to the network card, but it's a catch 22 since I can't get the driver until I connect to the internet.

The computer is an Acer Aspire 5560 series (model No. MS2319).

Please help, because time is of the importance.

---

### Post by papibe on 2013-11-10
Hi King Dude.

Let's try to get the wired connection working.

Is is possible for you to post output from some commands? I think you would need a USB stick to redirect their output to a file.
```
sudo lshw -C network

lspci -nnk | grep -iA2 eth

ifconfig

route -n

nm-tool

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by Hadaka on 2013-11-10
Hi, Aspire "usually" has broadcom cards..try this
you wont need a interet connection for the first comand..
open a terminal  ctrl/alt/t and enter..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
BOOT
you "should" now have wired working.
from a wired connection..connected to the intrernet
open a terminal  ctrl/alt/t and enter..
```
sudo apt-get update
sudo apt-get upgrade
```
then finally enter.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
BOOT
you should now have wireless

---

### Post by King Dude on 2013-11-11
> **Hadaka said:**
> Hi, Aspire "usually" has broadcom cards..try this
you wont need a interet connection for the first comand..
open a terminal  ctrl/alt/t and enter..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
BOOT
you "should" now have wired working.
from a wired connection..connected to the intrernet
open a terminal  ctrl/alt/t and enter..
```
sudo apt-get update
sudo apt-get upgrade
```
then finally enter.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
BOOT
you should now have wireless
Didn't seem to work. I still can't connect via a wired connection.

---

### Post by frankx on 2013-12-29
Hadaka,

Many, many thanks.
I worked hours on trying to make an internet connection on my Dell Inspiron E1505 with a Broadcom BCM4311 nic, and Linksys Wireless-G router using a fresh install of Ubuntu Studio 12.04 LTS. However, when I found and used your suggestions here, it worked instantly. 
Again, thanks so much. Your reply is well appreciated. :p :KS:D

---

