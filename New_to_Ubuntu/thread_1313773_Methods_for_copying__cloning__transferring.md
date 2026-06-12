---
title: "Methods for copying / cloning / transferring ?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Innernet on 2009-11-04
From a perfectly working but small hard drive; what methods can be used to transfer all data, settings, drivers, bookmarks, programs, languages, files... to a larger hard drive ?

Using the same version,
-Into a (larger) blank hard drive ?
-Into a (larger) drive with already freshly loaded same version Ubuntu ?

The donor as master IDE, the recipient as slave IDE

In order to transfer identical functionality ?

Am quitting from 9.10 back to 7.10 :(  Too many hurdles to keep/transfer my settings.  (Video, Compiz, audio, mainboard drivers unapplicable)

---

### Post by fancypiper on 2009-11-04
That's a great leap in releases, that's for sure!

Here is how I do it.

# Copy Directories using tar
# [http://www.linuxdevcenter.com/pub/a/linux/lpt/18_16.html](http://www.linuxdevcenter.com/pub/a/linux/lpt/18_16.html)
cd /source/directory
tar cf - . | (cd /destination/directory && tar xBfp -)

Source and destination directories must pre-exist.

---

### Post by kyuubi777 on 2009-11-04
you might try reinstalling the os on the big hdd while the small one is plugged in .. i've rebooted ubuntu many times and during installation it gives me option to import details from my windows os on my sda3 partition (i've always brushed by this and ignored it)and if it only imports details you can always access the other hdd filesystem after you boot up linux and just pull the home directory over 
hope this helps.. not sure of it myself, but eh..

---

### Post by Innernet on 2009-11-04
Thanks.  Am not confident to have the skills or 'tonsills':rolleyes: to do it those ways;  any other idiot-proof method for an absolute beginner, or a step by step guide ?

---

### Post by fancypiper on 2009-11-04
If you simply want to transfer what is on a small drive to an empty larger drive, the simplest way I know of to do it is with the dd command

dd if=/dev/<small drive> of=/dev/<large drive>
I think those drives are recognised as this in Ubuntu 7.10:
dd if=/dev/hda of=/dev/hdb

[Linux Power Tools]("http://linuxdevcenter.com/pub/q/UnixPower")

Do you use a partitioning scheme with a separate /home partition?  That really makes changing distros/doing fresh installs much easier and less hassle with config files.

---

### Post by Innernet on 2009-11-04
Both hard drives (small good and newly loaded large) were selected as single partition, full disc.

Will start studying your links.
Thanks

---

### Post by Innernet on 2009-11-08
Hi all.
Just wanted to report success.

Downloaded Live Gparted, burned onto a CD.
Donor hard drive as master, recipient as slave, CDROM as secondary.  Booted from it.

Ended with a perfect clone in a larger size hard drive, kept all identical settings, drivers, files, programs, languages, functionality... ALL. :D

This helped too:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

