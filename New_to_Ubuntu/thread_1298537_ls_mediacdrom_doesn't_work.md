---
title: "ls /media/cdrom doesn't work"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by SirSlipALot on 2009-10-22
Hi,

I want to catalog my CDs and DVDs using a bash script, but ls /media/cdrom gives me nothing

Ubuntu automatically mounts the cd and I can see the contents using nautilus

This inforamtion might help:

$ eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/sr0'
eject: `/dev/sr0' is mounted at `/media/books-online01'
eject: unmounting device `/dev/sr0' from `/media/books-online01'
eject: `/dev/sr0' is not a multipartition device
eject: trying to eject `/dev/sr0' using CD-ROM eject command
eject: CD-ROM eject command succeeded


$ ls -lisa /dev/cdrom
5077 0 lrwxrwxrwx 1 root root 3 2009-10-04 16:57 /dev/cdrom -> sr0


$ ls -lisa /dev/sr0
1136 0 brw-rw----+ 1 root cdrom 11, 0 2009-10-04 18:57 /dev/sr0

$ mount
...
/dev/sr0 on /media/books-online01 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


/etc/fstab  does not mention the cdrom......


Thanks for any help or clues

---

### Post by OrangeVixen on 2009-10-22
I use 9.04 and it auto mounts to /media/CDROM

---

### Post by SirSlipALot on 2009-10-22
$ ls /media/CDROM
ls: cannot access /media/CDROM: No such file or directory

$ ls -lisa /media/cdrom
892930 0 lrwxrwxrwx 1 root root 6 2009-04-25 17:46 /media/cdrom -> cdrom0
$ ls -lisa /media/cdrom0
total 8
892931 4 drwxr-xr-x  2 root root 4096 2009-04-25 17:46 .
892929 4 drwxr-xr-x 22 root root 4096 2009-10-23 04:23 ..

$ ls -lisa /cdrom
12 0 lrwxrwxrwx 1 root root 11 2009-04-25 17:46 /cdrom -> media/cdrom

Going in circles :)

---

### Post by undecim on 2009-10-23
/media/cdrom is just the default cdrom directory if the cd doesn't have a label. Since your cd has a label, its mounting in its own folder.

If you want to use a bash script, you will need to figure out where it is mounted. give me a few minutes and I will whip up a quick bash snippet to do just that. (unless someone who isn't having to read awk documentation knows how)

---

### Post by undecim on 2009-10-23
Here we go:```
awk '/\/dev\/sr0/ {print $2}' /proc/mounts
```

that will output the mount point of /dev/sr0 (your cdrom) without the trailing /

To use that as an argument of a command, wrap it in `` or $()

for example:```
cp -ar $(awk '/\/dev\/sr0/ {print $2}' /proc/mounts)/* ~/cd-rom_archive/
```

---

### Post by SirSlipALot on 2009-10-23
Thanks undecim!

I don't know yet how, but that does what I need :)

---

### Post by undecim on 2009-10-23
> **SirSlipALot said:**
> Thanks undecim!

I don't know yet how, but that does what I need :)

No problem! I've recently started learning awk, and its a wonder why I haven't  learned it yet, for as much as I love using bash.

A quick explanation of the awk script though: the /\/dev\/sr0/ part searches for lines with /dev/sr0 (just like grep /dev/sr0) and the print $2 prints the second column of all those lines (all this coming from /proc/mounts)

And as of typing this, I've noticed a small flaw... if you have something mounted to a folder including /dev/sr0 (i.e. if /dev/sdc1 is mounted on /media/dev/sr0) then you will get that folder output as well, and potentially copy files you didn't want... Just for the sake of completeness, here is a more concise awk command to do the same thing, but without the flaw:```
awk '{if ($1=="/dev/sr0") print $2}' /proc/mounts
```

btw, if you happen to have a second CD drive, you should be able to use this with the second one to do two disks at a time by changing /dev/sr0 to /dev/sr1

---

