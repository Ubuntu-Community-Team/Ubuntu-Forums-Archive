---
title: "My DVD drives aren't recognized"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by bamend on 2010-07-04
For some reason my two dvd drives are not mounting on startup.  Here's my fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdc7 :
UUID=d2e3493a-58fa-4ab0-a87c-0c1f574f5f7f	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sdc8 :
UUID=65c4a2ef-e152-4118-80ed-7923e2732c8a	/home	ext3	defaults	0	2
#Entry for /dev/sda5 :
UUID=84a290e6-91a9-4725-961b-ff7ea8761a0e	/home/bamend/nd	ext3	defaults	0	2
#Entry for /dev/sdb7 :
UUID=F29455F29455B9B5	/media/Alex	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdb5 :
UUID=EE1CA7881CA74A83	/media/Bob	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdc1 :
UUID=961C83B11C838B47	/media/C:\	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdb9 :
UUID=15827D39E90D1D61	/media/Cathy	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdc5 :
UUID=E8D844EED844BD16	/media/Data	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdb8 :
UUID=EC3087F93087C8D2	/media/Data1	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdb6 :
UUID=40209E87209E8416	/media/Mojo	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdc6 :
UUID=247882FF7882CF4C	/media/Trey	ntfs-3g	defaults,locale=en_US.utf8	0	0
UUID=B234A18B34A15361	/media/C:	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdc9 :
UUID=9f121f33-f3a2-4eef-b617-b126368bde66	none	swap	sw	0	0

My lshw results for cdrom's is 
      *-cdrom
             description: DVD writer
             product: DVD RW DW-Q28A
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /mnt
             version: KYS2
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,relatime,utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /mnt
                configuration: mount.fstype=udf mount.options=ro,relatime,utf8 state=mounted

and the other isn't listed.  any help would be appreciated

---

### Post by cariboo on 2010-07-04
Cdrom drives are no longer listed in /etc/fstab, they use udev to mount when a disc is detected.

---

### Post by mc4man on 2010-07-04
The drive should be showing up in lshw, fstab or not.

Best to start by booting to the bios setup and make sure it's being detected.

If so, try booting up with media with a filesytem inserted in the missing drive, a dvd movie  or data disk would be fine , and see if the drive is detected.

It may be of some value to take a look at this - is the missing drive listed?

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

On another note - does the drive that is detected have an issue?
Asking because you've mounted the media in it to /mnt, with no mountpoint created or specified.
The default now is for media to be mounted to /media/<volume label>, is that not happening?

( while fstab entries are no longer used I've seen no reason yet why they still can't be used, (nor have been informed of one).
There can be some advantages to having a static, defined mountpoint for dvd/cd media

---

