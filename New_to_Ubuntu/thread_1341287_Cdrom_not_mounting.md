---
title: "Cdrom not mounting?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by mikee55 on 2009-11-29
Hello all, I just installed my CD writer alongside my DVD writer, to give the DVD a rest, (I'm on my third), but it doesn't mount, why?

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c19e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14030   112695943+  83  Linux
/dev/sda2           14031       14593     4522297+   5  Extended
/dev/sda5           14031       14593     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2b4fcec


blkid says nothing?

I've tried searching. The Icon comes up in Places/Computer and thats it.

Mike  :)

---

### Post by Redmage913 on 2009-11-29
Does it show up on your BIOS? If it can't show up there, you won't be able to use it at all, from what i know.

---

### Post by Buuntu on 2009-11-29
You might have to add something along the lines of this to your /etc/fstab file:
```
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```
Make sure /dev/scd1 is set according to your cd drive and /media/cdrom1 is where you want to mount it.

This will make your CD drive mount automatically at boot up.

---

### Post by mikee55 on 2009-11-29
Hi there, Yes its in Bios, Buuntu, can you explain further please?

Mike:)

---

### Post by mikee55 on 2009-11-29
Bump:)

---

### Post by mikee55 on 2009-11-29
Help!!

---

### Post by Buuntu on 2009-11-29
Relax... Yes I can: 
/etc/fstab is a file which has the devices that are automounted at startup.  By simply adding the line I specified before, the device /dev/cdrom1 (yes I changed it :P) will be automounted at startup with some additional options (don't worry about those yet) to /media/cdrom1.  What I was saying is to add the line I specified to the end of the /etc/fstab file, save, and exit.  Cdrom1 might be different, so could you please post the output from this command?
```
ls /dev/cdr*
```

Also, can you post what's in /etc/fstab here too?

If you are still confused - try reading this: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by choyak on 2009-11-29
Mine is extremely bizarre the DVDRW refuses to mount except if I put in a movie then start Ubuntu.  The device mounts and the movie shows on the desktop, if no movie, then I get unmounted CD.  This is how I did this.  SOMEHOW I broke the kernel 2.6.31-302-ec2.  When I boot, I get 'error you need to load the kernel first' (bummer).  I can boot with the selection for the kernel 2.6.31-15-generic.  That is what I am using now.  I am wondering if the CD mount refusal is associated with the broken latest kernel.  How can I play with grub2 to get the kernel to boot properly??

---

### Post by mikee55 on 2009-11-30
Hello again,

lounge-pc@lounge-pc-desktop:~$ ls /dev/cdr*
/dev/cdrom  /dev/cdrom1  /dev/cdrw  /dev/cdrw1
lounge-pc@lounge-pc-desktop:~$ 

lounge-pc@lounge-pc-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
lounge-pc@lounge-pc-desktop:~$ 

Sorry the late reply, been too bed!:)

Mike

---

### Post by mikee55 on 2009-11-30
Bump:)

---

### Post by ukripper on 2009-11-30
post output of this command:
```
gedit /etc/fstab
```

and 
```
ls -al /dev/cd*
```

---

### Post by Buuntu on 2009-11-30
```
gksudo gedit /etc/fstab
```
**Then add the below line to the end of the file, save, and exit
```
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by mikee55 on 2009-11-30
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5e1f0219-f203-41f3-9243-56519a273bc0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b5385936-32e4-411c-afff-19e39934013e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

Still not doing, I put an Album in, and the icon disappeared ???

Mike:)

---

### Post by ukripper on 2009-11-30
can you post output of this:
```
ls -al /media
```

---

### Post by mikee55 on 2009-11-30
Thankyou

lounge-pc@lounge-pc-desktop:~$ ls -al /media
total 20
drwxr-xr-x  5 root      root      4096 2009-11-30 14:28 .
drwxr-xr-x 21 root      root      4096 2009-11-25 18:53 ..
drwx------  1 lounge-pc lounge-pc 4096 2009-06-21 21:14 768C58CB8C58880F
lrwxrwxrwx  1 root      root         6 2001-01-01 00:20 cdrom -> cdrom0
drwxr-xr-x  2 root      root      4096 2001-01-01 00:20 cdrom0
lrwxrwxrwx  1 root      root         7 2001-01-01 00:20 floppy -> floppy0
drwxr-xr-x  2 root      root      4096 2001-01-01 00:20 floppy0
lounge-pc@lounge-pc-desktop:~$ 



Mike:)

---

### Post by ukripper on 2009-11-30
you need to create cdrom1 directory before mounting it from fstab.

in terminal:
```
sudo mkdir /media/cdrom1
```

now to mount your fstab entries run this:
```
sudo mount -a
```

if it mounts then your cdrom will mount ok on reboot.

---

### Post by ukripper on 2009-11-30
Edit: Double post

---

### Post by mikee55 on 2009-11-30
Did that, rebooted, lost internet and decided to reinstall see if that helped?????

Back to square 1.......................................|


Mike

---

### Post by Buuntu on 2009-11-30
make the directory /media/cdrom1 do what I said and restart again - there is no reason why that should crash your system so I'm guessing something else did

---

