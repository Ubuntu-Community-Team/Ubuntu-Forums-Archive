---
title: "Where can I find wifi drivers"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by jacatone on 2015-01-04
Ubuntu doesn't seem to find wifi connections. The hardware drivers it lists are as follows. Does anyone know where I can download the .deb files using a Windows machine? Thanks.


"This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware."

---

### Post by Hadaka on 2015-01-04
Hi, check the sticky at the top of this page, for how to locate your driver,
if you need help with it, let us know,
thanks,

---

### Post by jacatone on 2015-01-04
This is what "Additional drivers" listed. It's a Broadcom wireless card.

---

### Post by Hadaka on 2015-01-05
ok, "aditional drivers" has nothing to do with what driver you need
for the card you have, so,,open a terminal crtrl/alt/t and copy and 
paste this command,
```
lspci -nn | egrep '0200|0280'
```
post the output
thanks

---

### Post by jacatone on 2015-01-05
Here's the result:

"ubuntu@ubuntu:~$ lspci -nn | egrep '0200|0280'
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)"

---

### Post by praseodym on 2015-01-05
Install the missing firmware:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by jacatone on 2015-01-05
Does this require an internet connection?

---

### Post by praseodym on 2015-01-05
Yes, but here is the direct link:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

---

### Post by Hadaka on 2015-01-05
Hi, please remove the incorrect dirver the install gives you,
```
sudo apt-get remove --purge bcmwl-kernel-source
```
you dont need internet for that. Is your wired connection now working?
if yes,,,then run praseodym's instructions
thanks

---

### Post by jacatone on 2015-01-05
I've never had any luck installing tar balls, is there a .deb file somewhere?

---

### Post by Hadaka on 2015-01-06
Here is another method,,
be sure to get the zip file first,,
[URL="http://ubuntuforums.org/showthread.php?t=2098717"]http://ubuntuforums.org/showthread.php?t=2098717

#post #7
[/URL]

---

