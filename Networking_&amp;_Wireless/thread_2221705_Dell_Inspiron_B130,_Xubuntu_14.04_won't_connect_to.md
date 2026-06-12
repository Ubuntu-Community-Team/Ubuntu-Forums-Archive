---
title: "Dell Inspiron B130, Xubuntu 14.04 won't connect to wifi"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by devdlp on 2014-05-03
I have a Dell Inspiron B130 and recently install Xubuntu its been working fine thus far except the os wont automatically detect any near wifi connections. For a while i could use the Ethernet cable for internet access but when i decided to add addictional drivers from the software & updates program before i could add any the Ethernet cable stopped working as well so now its impossible for me to connect.. Help Please.

---

### Post by Hadaka on 2014-05-03
Hi, please open a terminal...ctrl/alt/t
and enter..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf

```
boot
then do..
```
sudo modprobe -v b44
```
your wired should now be working
from the wired connection connected to the internet please do
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```
the wireless should now be working

and if all else fails..you can always read the STICKY
**How to install a driver for the Broadcom series of PCI wireless cards**
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

**How to install a driver for the Broadcom series of PCI wireless cards**

---

### Post by devdlp on 2014-12-04
i know it took awhile to get back but i did what you suggested and still have the same problem. To test it i unplugged my ethernet cable and clicked on my wifi icon it still doesnt search for any wifi connections, i also checked the sticky and did what was posted and had zero luck, please help.

---

### Post by Hadaka on 2014-12-04
please post the output of..
```
rfkill list all
lspci -n | egrep '0200|0280'
lsmod | egrep 'wl|b43'
cat /etc/issue
```

---

### Post by devdlp on 2014-12-04
deven@deven-ME051:~$ rfkill list all
deven@deven-ME051:~$ lspci -n | egrep '0200|0280'
02:00.0 0200: 14e4:170c (rev 02)
02:03.0 0280: 14e4:4318 (rev 02)
deven@deven-ME051:~$ lsmod | egrep 'wl|b43'
deven@deven-ME051:~$ cat /etc/issue
Ubuntu 14.04.1 LTS \n \l

---

### Post by Hadaka on 2014-12-04
from a working wired connection please do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

---

### Post by devdlp on 2014-12-04
worked perfectly.

---

### Post by Hadaka on 2014-12-04
Awesome glad it worked for you, I also am using the
B-130 with 1.5 gig ram and 40 gig drive, running 12.04lts
error free. I do however have a fiber optic isp connection.
have fun !!

---

### Post by devdlp on 2014-12-05
It happened again, it worked the first time, when i unplugged the ethernet cable i had wifi now when i plug it back in i still wont get internet access. This is what i did this time araound.

---

