---
title: "Urbuntu shows shows two drives with DMRAID"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by LinuxAlexs on 2009-02-23
Hi there

After about a week of work I've finally managed to install Ubuntu 8.10 (64 bit) onto my machine.

I'm dual booting and I'm using Intel hardware mirrored raid (on board motherboard) with dmraid successfully:

[B]dmraid -s

name   : isw_bjbjjdagf_ARRAY
size   : 488280576
stride : 256
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
dmraid -r
/dev/sdb: isw, "isw_bjbjjdagf", GROUP, ok, 488281248 sectors, data@ 0
/dev/sda: isw, "isw_bjbjjdagf", GROUP, ok, 488281248 sectors, data@ 0[/B]

I'm booting up with grub, and I have 3 NTFS partitions (Windows XP OS's) a Linux Parition and a swap partition...

Now in Ubuntu XWindows, if I goto Places/Computer I see each NTFS partition listed as two drives. Any idea on what I can do about this (I want to only view one drive)? Thanks...

(nb I also have a non raid hard disk that does not have this issue with partitions).

Thanks

---

### Post by LinuxAlexs on 2009-02-23
Well maybe this is some sort of solution here?
[http://ubuntuforums.org/showpost.php?p=2605508&postcount=34](http://ubuntuforums.org/showpost.php?p=2605508&postcount=34)

Assuming this is the right path my two questions are (and please see info I supplied from previous post) which drives do I hide?

... and why is it showing two drives anyway? Obviously I'm worried about hiding the wrong drive!! (isw_bjbjjdagf_ARRAY, sda,sdb)??

Thanks

---

### Post by LinuxAlexs on 2009-03-01
Okerley dokerley I guess I'm just talking to myself....

---

### Post by LinuxAlexs on 2009-03-14
Well no response then - not bad for a first post ;)...
Am I missing out on any detail maybe?

---

