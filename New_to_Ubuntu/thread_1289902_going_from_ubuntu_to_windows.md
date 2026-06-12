---
title: "going from ubuntu to windows"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by rubenator on 2009-10-12
sadly enough..  i need to install windows xp on my old laptop which is currently runing ubuntu.... i love linux but i need xp to run some software not available for ubuntu... and i dont think my laptop can support sun virtualbox.... (1.0 ghz, 256 RAM)
i tried to boot from my windows xp cd... after a while i get the message  


"ql1240.sys corrupt"

any ideas??   i need the help...

---

### Post by Hospadar on 2009-10-12
Sounds like your windows cd is bad, try burning a new one.

Also just in general I'd suggest booting off an ubuntu live cd and using gparted to move around and resize the partitions the way you want them to end up, then install windows into the free space you created [in gparted].

After installing windows you'll probably need to restore grub if you want to get back to linux.  You can find info on how to do that in the community docs link in my sig.

---

### Post by Ravernomina on 2009-10-12
> **rubenator said:**
> sadly enough..  i need to install windows xp on my old laptop which is currently runing ubuntu.... i love linux but i need xp to run some software not available for ubuntu... and i dont think my laptop can support sun virtualbox.... (1.0 ghz, 256 RAM)
i tried to boot from my windows xp cd... after a while i get the message  


"ql1240.sys corrupt"

any ideas??   i need the help...

Did you try WINE? It runs Windows Programs Natively so no emulation is needed.

---

### Post by lorddresefer on 2009-10-12
yeah I would say burn a new windows Cd.   try using a slower burn rate like 8x or less.   it takes a while but usually ensures a good burn.  and for good measure, check the md5 sum and make sure its all good

---

### Post by PrePenguin on 2009-10-12
Bad Disk or bad Ram.. Check the media you are booting from for defects also set the cd/dvd player as first boot option in bios.. You need to fdisk if you can also.

---

### Post by OlsenCNC on 2009-10-12
Sounds like a bad Installation CD to me too.

---

### Post by 123456789123456789123456 on 2009-10-12
one of the sure ways to restore grub is with the super grub disk, which can be downloaded.  You may also want to look into a program called crossover linux.  It is a program that uses wine, in some ways, but you can install most xp, vista, 2000, 98, and 95 applications natively on Ubuntu.  It works great, you can install the program by the actual windows based install cd for each application, or from the install files, as long as the install files are in *.exe, or *.com extentions.  but in other solutions, I agree with the other last post, doing a dual boot would be better.  You create another partition, of free space, you can format this partition as vfat, or leave it unformated.  When you start to install windows, it will list your partitions, 3 of them be be exact, with the ubuntu partition, swap file partition, and the empty partition.  You choose the empty partiton to install XP on.  You can resize the ubuntu partition, leaving unpartitioned space, and install xp on to a partiton you create with xp disk, to install on.  XP will delete GRUB 1 which is on the MBR(master boot record), and replace it with ntldr(NT Loader) windows xp boot loader.  Use the super grub disk to replace ntldr in MBR with grub.  initialize it so it knows what partition Ubuntu is on.  It should automatically detect xp, and give you the option at boot, which OS you wish to boot with.

---

### Post by deancasino on 2009-10-12
> **rubenator said:**
> sadly enough..  i need to install windows xp on my old laptop which is currently runing ubuntu.... i love linux but i need xp to run some software not available for ubuntu... and i dont think my laptop can support sun virtualbox.... (1.0 ghz, 256 RAM)
i tried to boot from my windows xp cd... after a while i get the message  


"ql1240.sys corrupt"

any ideas??   i need the help...
Dude just get WINE;
[http://www.winehq.org/](http://www.winehq.org/)

Nothing is ever that bad that you need to go back to Windows, unless of course games are your bag, then a separate Win partition is all you need.

---

### Post by crispy_420 on 2009-10-13
I second a bad XP disc. Or is that a third, fourth, etc.

---

