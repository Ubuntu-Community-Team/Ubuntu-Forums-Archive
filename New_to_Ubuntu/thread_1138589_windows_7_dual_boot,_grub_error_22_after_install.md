---
title: "windows 7 dual boot, grub error 22 after install"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2009-04-26
Just installed ubuntu 9.04. Installed from the live CD.
On reboot, after the GRUP loading bit I get "ERROR 22"

Any idea whats causing this and how to resolve it.

My System is
Gigabyte MA790FX-DS5
Athlon X2 5600+
2GB Corsair PC 3200
XFX GFFX 9800 GT 512 

WDR 74GB   (windows 7)
WDC 320GB  (Storage)
WDC 750GB  (50GB Ubuntu, 700GB Storage)

---

### Post by cariboo on 2009-04-26
Use [thread=224351]this[/thread] howto, to repair grub.

---

### Post by bigmonmulgrew on 2009-04-26
no change
For clarity I thinks its also worth pointing out that I installed windows first and ubuntu second

---

### Post by Sealbhach on 2009-04-26
This might be because you're using Windows 7? Take a look at this link here:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

.

---

### Post by bigmonmulgrew on 2009-04-26
thats pretty much the same as the guide to reinstalling grub when you installed ubuntu the windows.
Still cant boot. with Error 22
Don't think 7 would be an issue.

Noticed in menu.lst though that its detected as Vista

---

### Post by bigmonmulgrew on 2009-04-26
might also be worth pointing out that i dont even get a list of OSs

---

### Post by bigmonmulgrew on 2009-04-26
sorted eventually.

I setup grub on my ubuntu drive and then set the bios to boot from that drive instead.
Grub also seems to pickup your first boot drive as hd0 regardless of which slot its in so I had to change the bit that boots windows.
Also found out that I have to boot from partition 0 (windows system area) and not partition 1 (windows partition C:)
so basically changed hd(0,1) to hd(1,0)

cheers for the help guys

---

### Post by Sealbhach on 2009-04-26
Cool, glad it worked out. yeah, in Linux, 0 is often the first, rather than 1.

.

---

