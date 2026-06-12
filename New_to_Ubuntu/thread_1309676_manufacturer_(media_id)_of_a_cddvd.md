---
title: "manufacturer (media id) of a cd/dvd"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by SirSlipALot on 2009-11-01
Hi All,

I want to determine the manufacturer or media id, and other information like the date of creation, of my cds and dvds using the shell (bash)

$ isoinfo -d -debug -i /dev/cdrom     -> gives some info on the cd

$dvd+rw-mediainfo /dev/sr0    -> apparently only works with dvds

$ cdck      -> also gives a little info on the cdrom

$ qpxtool  -> lots of info.! seems to be GUI only...

$ cdrecord -atip dev=/dev/cdrom   -> gives errors...:
```
$ cdrecord -atip dev=/dev/sr0
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
WARNING: /dev/sr0 seems to be mounted!
wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```so i tried :
1)$ umount /dev/sr0
2)$ cdrecord -debug -atip    -> now it works and i can see the manufacturer !

but now i have a problem: i can't remount the cd-rom
e.g.: $ mount /dev/cdrom
or mount /dev/sr0
hangs for a while and then gives an error:
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab

:(

is there another way of getting the disk manufacturer? or to solve mounting the cd again...

help needed and appreciated...

---

### Post by SirSlipALot on 2009-11-01
??? can't find my thread ...

ok. found it :)

---

### Post by schily on 2009-11-02
Wour problem is that you do not use cdrecord but a broken
fork. This broken fork has problems with hald and it
does not support DVDs.

I recommend you to use a recent original version from:

[ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)  
[http://cdrecord.berlios.de](http://cdrecord.berlios.de) 

Note that the real cdrecord correctly writes DVDs and of course 
reads media information from CDs, DVDs and BluRays.

---

### Post by 1in0 on 2009-11-03
Hi!

i downloaded the latest version of cdrecord from cdrecord.berlios.de

$make worked like a breeze! :D
(first time i successfully compiled a package in linux! thanks! :)

$ cdrecord -version
```

Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.9
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling

```but $ cdrecord -atip dev=/dev/sr0
still gives me errors:
(...)
WARNING: /dev/sr0 seems to be mounted!
(...)


after umount it gives me all the info i need.

maybe something in my system has a problem...

---

### Post by schily on 2009-11-03
Your problem is that you still dod not call
the real cdrecord but the broken fork.

The real cdrecord gives you this response:

OBJ/i386-sunos5-cc/cdrecord -version
Cdrecord-ProDVD-ProBD-Clone 2.01.01a67 (i386-pc-solaris2.11) Copyright (C) 1995-2009 Jörg Schilling

If you call the real cdrecord instead of the fork, it will work.

---

