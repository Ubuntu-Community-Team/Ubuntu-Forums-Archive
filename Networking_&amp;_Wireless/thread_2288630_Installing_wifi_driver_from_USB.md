---
title: "Installing wifi driver from USB"
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by styx4 on 2015-07-28
Spoiler for those with no patience: I have three days experience with Linux.):P



For those brave enough to read on, I'll keep it short...


I'm trying to install a Broadcom wireless driver from a USB. It is not working. When I look at the Additional drivers tab,
it appears but says in small great text that the driver is not working. When I try to install it, I doesn't install. I guess it
was right! If anyone can point me in the right direction, I would appreciate it.

P.S. Wired connection to the internet is out of the question (no ethernet port (yes I am using macbook pro please do not judge)).

---

### Post by PaulW2U on 2015-07-28
*Thread moved to **Networking & Wireless**.* 

Welcome to the forums styx4,

I've also reset your fonts to default. Please don't use over-size fonts.

---

### Post by Hadaka on 2015-07-28
Hi, the mcbook usually is the b43 driver. since you have no internet
we will make this as easy as possible. Please open a terminal ctrl/alt t
then copy and paste the following..
```
lspci -n | grep 14 |awk '{print$3}'
```
post the output so we may determine your correct driver.
thanks

---

### Post by styx4 on 2015-07-28
> **Hadaka said:**
> Hi, the mcbook usually is the b43 driver. since you have no internet
we will make this as easy as possible. Please open a terminal ctrl/alt t
then copy and paste the following..
```
lspci -n | grep 14 |awk '{print$3}'
```
post the output so we may determine your correct driver.
thanks

--------------------

8086:9c31
8086:9c14
14e4:1570
14e4:43a0
1b4b:9183

--------------------
None of that looks familiar but I have seen the 14e4:43a0 before. Isn't that the wireless card used for most Macbooks? Thanks for
the help by the way.

---

### Post by Hadaka on 2015-07-28
hi, follow the instructions in post #4 here
[URL="http://ubuntuforums.org/showthread.php?t=2247401"]http://ubuntuforums.org/showthread.php?t=2247401
~OR.. The chili555 fix..
[/URL][TABLE]
[TR]
[TD="class: votecell"]          

              [/TD]
                [TD="class: answercell"]      If you have the installation USB, insert it and and drill down to  pool > restricted > b > bcmwl and drag bcmwl-kernel-source to  your desktop. Do the same with pool > main > d > dkms and drag  dkms to you desktop. Then install:
```


  cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i bcmwl*.deb
sudo modprobe wl
```
good luck

  

     
[/TD]
[/TR]
[/TABLE]
[URL="http://ubuntuforums.org/showthread.php?t=2247401"]
[/URL]
good luck.

---

### Post by styx4 on 2015-07-29
So I i followed the links, downloaded the packages, downloaded the driver and I received errors when installing the bcmwl driver. These are the
ones I could see.

-----------------------

ERROR (dkms apport): kernel package linux-headers-3.16.0-30-generic is not supported
Error! Bad return status for module build on kernel: 3.16.0-30-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.233.141+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.

-----------------------


EDIT: I found the issue! I was using a kernel that did not posses the most recent patches. Did some more digging and found the right
file for installation. Everything is working like a charm! Thank you so much for pointing me in the right direction with those links.

---

### Post by Hadaka on 2015-07-29
Glad you got it sorted out !
be sure to do an update to get all the latest goodies.
```
sudo apt-get update
```

---

