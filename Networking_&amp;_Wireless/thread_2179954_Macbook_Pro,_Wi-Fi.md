---
title: "Macbook Pro, Wi-Fi"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by locky2 on 2013-10-10
Hello everyone

I am completely new to ubuntu and recently just installed the os.

I am running ubuntu off of a macbook pro with retina display.

Everything seems to be working fine except the Wi-fi won't pick up any of my wireless networks. I am not sure if I need to install drivers or something.

I am extremely inexperienced with this os so can someone please give me very basic steps on exactly what I need to do to get my Wi-Fi working.

Thank you.

---

### Post by Hadaka on 2013-10-10
Hi, Locky2 and welcome !
More than likely this will get you going
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
```
sudo apt-get update
sudo apt-get upgrade
```
BOOT
Then do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
*iF THAT DID NOT get you going
then..
Please post the output of..
```
uname -a
rfkill list all
lspci -nnk | grep -iA3 net
lsmod
```
thank.

---

### Post by locky2 on 2013-10-11
hello thanks for trying to help me but this did not work.

and just to get thinks right I am typing these codes into the terminal application on ubuntu is this correct? and when I type one code of line in I hit enter and then it executes instead of being able to type the chunk in that is listed in ur codes above is that alright?

Also if it helps i am running ubuntu 13.04

---

### Post by Hadaka on 2013-10-11
yes..from a terminal...ctrl/alt/t with a wired connection
enter the commands...one line at a time. To avoid possible
typo's you may also copy and paste one line at a time.
thanks.

---

