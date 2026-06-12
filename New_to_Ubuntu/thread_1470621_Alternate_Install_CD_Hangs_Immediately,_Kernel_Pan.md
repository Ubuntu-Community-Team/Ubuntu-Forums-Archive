---
title: "Alternate Install CD Hangs Immediately, Kernel Panic - not syncing"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by jmgmd on 2010-05-03
Trying to install a bare-bones ubuntu desktop on an ancient Compaq 1245 laptop (333 mHz, 160 mb, 3.2 GB hd), and after hitting install I get nothing but a flashing cursor and eventually this message:

udevam settle - timeout of 180 seconds reached, the event queue contains:
  /sys/devices/pci0000:00/0000:00:14.0/host1/target1:0/01/:0:0:0/b;pcl/sr0 (775)
[  186.065590] Kernel panic - not syncing: Attempted to kill init!

I've gone into the BIOS and made sure to disable all possible hangups (turned off power saving, etc.), run a memtest with the ubuntu cd and found no errors, and burned two different cd's to make sure it wasn't a problem with the disk image or burn.  The hard drive was wiped of Windows 98 using DBAN so there's nothing on there now, I know the size should be sufficient for what I am trying to do but am unsure of how it might be affecting the install beyond that.  (When I power on I get a message at the boot menu: "Partition table corrupted or doesn't exist, Error 0270: Real time clock error feature is disabled.  Run Phidisk for information. File: create new. Partition: Consult manual."  I have been assuming that because I am starting from scratch partitioning isn't necessary.)

I apologize for just effectively throwing all this stuff up on the wall, this is the first time I've tried to install ubuntu (actually any os) and while I've tried to read up on the install troubleshooting as best I can, it's all a bit beyond me right now.  I've looked into other lightweight linux distros but I'd really like to give Ubuntu a shot first, and am a bit disappointed that every option I try on the alternate cd (server, CLI, desktop, using acpi=off, noapic, nolapic) doesn't get anywhere.  Any help or suggestions whatsoever would be very much appreciated.

---

### Post by nhasian on 2010-05-03
yes that is quite an ancient computer, and does not meet the minimum requirements for ubuntu.  please try lubuntu instead:

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by jmgmd on 2010-05-03
Thanks, lubuntu does seem more realistic for older hardware (and newer users like me unfamiliar with piecemeal installations) but in my case with my memory so low - under 192 mb - I think it would be the same issue as with any ubuntu, namely that I wouldn't be able to use the GUI installer and would be back to the alternate install cd.       

I tried antiX and got it successfully installed - I saw it mentioned that it uses an older kernel than ubuntu.  Just on first glance, it seems like a pretty promising option for an old machine - nice look and low memory usage (30 mb w/o anything open).

---

