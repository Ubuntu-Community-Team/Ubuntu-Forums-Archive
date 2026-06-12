---
title: "[SOLVED] Multiboot Box Help"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by QenBirQeni on 2008-12-17
Hey guys,

I want to install multiple distros in one box without using virtualization. I would like to have this setup:

[INDENT]sda1 - swap
sda2 - small ext3 (hope to put standalone grub here)
sda3 - extended partition
sda5 - logical partition - Debian
sda6 - logical partition - Slackware
sda7 - logical partition - Ubuntu
sda8 - logical partition - Gentoo
sda9 - logical - data storage[/INDENT]

How can I approach this? Can I use sda2 for GRUB only to chainload the rest of the OS? Do I have to install a bootloader for each OS in their respective "/"? I was able to install GRUB on sda2, but I wasn't able to boot into any of the OS. I installed a bootloader in "/" for each OS.

My GRUB on sda2

```
title     Debian on /dev/sda5
chainloader (hd0,4) + 1

title     Slackware on /dev/sda6
chainloader (hd0,5) + 1

title     Ubuntu on /dev/sda7
chainloader (hd0,6) + 1

title     Gentoo on /dev/sda8
chainloader (hd0,7) + 1
```


Reiterating, it did not work for me. Where am I messing up?

I'd appreciate any help on this.

Regards 

Qeni

---

### Post by adult swim on 2008-12-17
while im not sure if your setup will work, i see one error in the way youve done it so far.  you need to separate the root from chainloader
```
title     Debian on /dev/sda5
root		(hd0,4)
chainloader	+1

title     Slackware on /dev/sda6
root		(hd0.5)
chainloader	+1

title     Ubuntu on /dev/sda7
root		(hd0,6)
chainloader	+1

title     Gentoo on /dev/sda8
root		(hd0,7)
chainloader	+1
```

---

### Post by jessdog9001 on 2008-12-17
Edit: It looks like you don't need a kernel entry for each if you installed the bootloader in the root for each distro! Sorry for any confusion...

---

### Post by red_team316 on 2008-12-17
QenBirQeni:
Read this, it's exactly what you are looking for. It's the best information I have ever seen on the subject of multibooting. I am using a similar setup to what you lined out in the first post and the link below will fill in the blanks for you.

and yes, for each OS install, just point the bootloader to install on that particular partition(i.e. /dev/sda12 or whatever)

**How to boot 145+ Operating Systems**
[http://www.justlinux.com/forum/showthread.php?p=861282](http://www.justlinux.com/forum/showthread.php?p=861282)

---

### Post by QenBirQeni on 2008-12-17
Thank you guys. I did a search and after messing with GRUB I finally figured out that spacing matters. Also, I used the installers to place each OS's bootloader to their repective first superslots of the root partition. I feel less stupid now.):P

---

