---
title: "Recover data from CDROM (cannot mount it)"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by daniel3ub on 2010-09-18
Hi, people.

I have a couple of old CDROMs that I need to read the data from.

The problem is that Ubuntu tries to auto mount the media and after a few seconds it recognizes the CD as a blank CD.

Then I've tried ```
ddrescue -b 2048 --no-split /dev/cdrom rescue/ddrescueIMG ddrescueLOG
```  (as seen here: [http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue))

I returns me ```
ddrescue: cannot open input file: No medium found
``` if I run the above command while the system is trying to mount the CD. After it is (wrongly) identified as a blank CD, the above command executes for hours, saying:

```
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    4096 B,  errors:       1
Current status
rescued:         0 B,  errsize:    641 TB,  current rate:        0 B/s
   ipos:   641276 GB,   errors: 1195172050,    average rate:        0 B/s
   opos:   641276 GB
```

note the "rescued: 0B".

Please, what can I do to recover this CD?

Thanks a lot!

---

### Post by jtarin on 2010-09-18
What is the data type on the CD? Were these made on the same machine? Have your tried to copy with an application such as K3B or Gnome Baker?

---

### Post by scorchgeek on 2010-09-18
If the CD needs to be unmounted, do
```
sudo umount /dev/cdrom 
```.

But many CDROMs are not on /dev/cdrom. Can you post the output of ```
mount
``` after the "blank" CD has been mounted? (Or you could look at the list yourself and find the listing that looks like a CDROM.)

---

### Post by JustinR on 2010-09-18
Try Dvdisaster, its in the software center. It doesn't need a CD to be mounted to retrieve data off of it.

---

### Post by jtarin on 2010-09-18
> **scorchgeek said:**
> If the CD needs to be unmounted, do
```
sudo umount /dev/cdrom 
```.

But many CDROMs are not on /dev/cdrom. Can you post the output of ```
mount
``` after the "blank" CD has been mounted? (Or you could look at the list yourself and find the listing that looks like a CDROM.)Actually ```
eject -n
``` will give more useful info

---

### Post by scorchgeek on 2010-09-18
> Actually
```
eject -n
```
will give more useful info


Thanks, never heard of that. Do that instead. :D

---

### Post by daniel3ub on 2010-09-19
> **jtarin said:**
> What is the data type on the CD? Were these made on the same machine? Have your tried to copy with an application such as K3B or Gnome Baker?

The CD was burned in a Win (probably 98) machine. The data is mostly jpg and tiff images, with some Corel Draw and MP3 files, and even maybe some AVI and MPEG.

Tried to copy it with Brasero with no joy. It tells me "No disk to copy" and considers it as a blank disk.

K3B tells me "The source disk is empty" and finishes with error ```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-19-generic
Devices
-----------------------
TSSTcorp CD/DVDW TS-L632M 0A17 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

```

Thanks for your kind help, anyway.

---

### Post by daniel3ub on 2010-09-19
> **scorchgeek said:**
> But many CDROMs are not on /dev/cdrom. Can you post the output of ```
mount
``` after the "blank" CD has been mounted? (Or you could look at the list yourself and find the listing that looks like a CDROM.)

```
..~/ > mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-19-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /media/Outros type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
none on /proc/bus/usb type usbfs (rw,devgid=1001,devmode=666)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel)
```

Couldn't figure out which one is the CD :(

---

### Post by daniel3ub on 2010-09-19
> **JustinR said:**
> Try Dvdisaster, its in the software center. It doesn't need a CD to be mounted to retrieve data off of it.

As the dvdisaster's manual says: "So if you have a defective medium but never created ecc data for it - sorry, your data is probably lost." and "So if you have a defective medium but never created ecc data for it - sorry, your data is probably lost."

Thanks for the try, anyway.

---

### Post by jtarin on 2010-09-19
Your cdrom drive is /dev/sr0

---

### Post by daniel3ub on 2010-09-19
> **jtarin said:**
> Actually ```
eject -n
``` will give more useful info

```
..~/ > eject -n
eject: le périphérique est `/dev/sr0'
..~/ > ddrescue -r 10 /dev/sr0 /media/Outros/backups/ddrescueIMG ddrescueLOG -v


About to copy 2048 Bytes from /dev/sr0 to /media/Outros/backups/ddrescueIMG
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512 bytes
Max_retries: 10    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    2048 B,  errors:       4
Current status
rescued:         0 B,  errsize:    2048 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       4,    average rate:        0 B/s
   opos:         0 B
```

Still nothing.

Any other ideas, please?
I'd really like to copy this CD to somewhere...

---

### Post by atjesse on 2010-11-09
Dvdisaster works fine for me.. Thanks a lot!!

---

