---
title: "Nvidia restricted drivers crashed wireless and sound dv9000t"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by Elmer Fudd on 2008-01-15
HP dv9000t running 7.10 .  Kernel 2.6.22-14-386

Everything was working fine - then loaded kde4 and the latest nvidia restricted drivers. Sound (82801G (ICH7 Family) High Definition Audio Controller) and wireless (PRO/Wireless 3945ABG Network Connection) went away.. "lshw" shows them  present but "unclaimed". 

I reset the driver in xorg.conf to "nv" and disabled the nvidia restricted drivers and changed to Gnome but no change. eth0 shows up and works with cat5 connection but no sign of eth1 for wireless  

I would reinstall Kubuntu ( the latest iso running live gives me max resolution, wireless and sound) but I am running a dual boot (xpPro) and don't want to lose anything in that partition or my Ubuntu partition. Actually, I would dump the XpPro partition but I still have to run Jeppesen aviation software on it. Haven't tried to get it running under Wine yet.

---

