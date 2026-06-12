---
title: "How to make a USB Boot disk"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Don1500 on 2009-11-27
OK I have tried to find this answer but to no avail.

I am trying to make a USB thumb drive boot system.
I have a 8 Gig SanDisk, formatted to Fat32 and WITHOUT the SanDisk installed extra stuff. (the U3 virtual CD Drive)

So aside from the "Lost & Found" folder this thumb drive is empty.
I go to "System => Administration => USB Startup disk creator"

And it has two entries for the Sandisk:
Device      Name              Capacity     Free Space
/dev/sdc   SanDisk Cruzer     7.5GB
/dev/sdc1  8.1GB file system  7.5GB          0.0

For the first entry it says to Format the drive. I do this and the system hangs. I go to g-parted and it says the partition is formatted to "Unknown".

If I try the second entry it says there is not enough free space, even though I know there is plenty of free space.

Every once in a while it will allow me to finish set up and go on, but the system hangs with a lost file error about 1/2 way through. 

What am I doing wrong???

---

### Post by Don1500 on 2009-11-27
[IMG]http://home.roadrunner.com/~don1500/Linux_Files/make USB.jpg[/IMG]
[IMG]http://home.roadrunner.com/~don1500/makeUSB.jpg[/IMG]

---

### Post by YosefKaro on 2009-11-27
I ran into a very similar problem and this is one case where I'm glad that I keep Windows on the side 'just in case'.  I plugged in my flash drive while in vista then chose that USB in MyComputer and double clicked on it.  It told me that the drive needed to be formatted, so I chose FAT32 and formatted it, then I was able to use the flash to create a bootup for ubuntu.  Good luck to you :)

-Yos

---

### Post by sgosnell on 2009-11-27
Why not just use gparted to do the formatting while you're in it?

---

### Post by bennachie on 2009-11-27
You don't actually need Windows, you can use GParted to create a new partition from scratch (FAT32 format, any label you like). It may be a two-step process (GParted will want to erase the existing file structure before allowing you actually to create a new partition). USB Disk Creator will work fine with the new partition.

---

### Post by Don1500 on 2009-11-27
> **sgosnell said:**
> Why not just use gparted to do the formatting while you're in it?

I did, under many different formats, and each time it came up the same as I had mentioned above. It either says the drive should be formatted or it is full, and must be formatted. I try to Format and it hangs.

---

### Post by spiderbatdad on 2009-11-27
consider wiping the drive and starting over.

```
dd if=/dev/zero of=/dev/sdc
```
This will take a few minutes. Be very certain of your destination, otherwise you could wipe your hard disk.
I believe you must use fat16 or the syslinux bootloader will fail.
```
sudo mkdosfs -F16 /dev/sdc
```

---

### Post by Don1500 on 2009-11-27
> **spiderbatdad said:**
> consider wiping the drive and starting over.

```
dd if=/dev/zero of=/dev/sdc
```
This will take a few minutes. Be very certain of your destination, otherwise you could wipe your hard disk.


Ayeeeee The HDs gone



just kiddin'.   It's in the works now, I'll let you know how it comes out.

---

### Post by mkvnmtr on 2009-11-27
Hmmm. I tried last night with three seperate USB drives. Had the same problems as you. Finally got installed on each of them. Then none of them would boot. One of them said it could not find the kernel. The others said error. I wish I could help you. I did all that you said you tried and finally got an installation but never a boot.

---

### Post by Don1500 on 2009-11-27
> **Don1500 said:**
> Ayeeeee The HDs gone



just kiddin'.   It's in the works now, I'll let you know how it comes out.

Almost had it there.
Dumped the reive like you said, re formatted through the set-up USB program and I got a "good" indication. Set it for 4GB space and said go;
after about 10 minutes of actually looking like it was working I got this:

```

An uncaught exception was raised
{Errno 5} Input/Output Error 
```


Tried formating to two 3.5GB partitions at Fat 16. Started loading then:
```

An uncaught exception was raised
{Errno 5} Input/Output Error 
```

---

### Post by mkvnmtr on 2009-11-27
Stick with it. I am thinking I might have to try many times to get one to work. I do not feel like it tonight but shortly I will give it another go. In the mean time I am watching this thread. Maybe someone knows hot to make it work. Also maybe we should look to see if a bug has been reported and there is a work around.

---

### Post by utnubuuser on 2009-11-27
look for a hidden trash folder maybe.  Isn't there an issue with fat32 only dealing with smaller file-systems?
have you tried making a smaller -2gig- parttion to install on, then resizing once you've completed the install?
I've found I've no problems installing on 2gig and smaller flash-drives, but the larger drives don't work as well, --- that's just a personal experience though.

---

### Post by bennachie on 2009-11-27
Fat16 is good for up to 2GB, you'll need Fat32 beyond that. If you don't need the persistence feature, Unetbootin would do the job for you with less hassle. All the other major distros now seem to have moved to Hybrid ISOs, which dispense with the need for this kind of messing around.

---

### Post by spiderbatdad on 2009-11-27
this shouldn't be too hard. I'll confess i haven't done this on ubuntu, but recently make a bootable usb for slackware. The process should be very similar. Obtain boot.img.gz for karmic: [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/)

Plug in your usb stick. Become root with sudo -i, or you may need to modify permissions of the drive to 666

Unmount the usb drive ```
umount /dev/sdc1
``` or whatever your device drive is.

```
zcat boot.img.gz > /dev/sdc 
```this should write boot.img.gz to the usb stick. Remount your usb drive and copy the iso to a root partition.

---

### Post by Don1500 on 2009-11-27
> **Don1500 said:**
> Almost had it there.
Dumped the reive like you said, re formatted through the set-up USB program and I got a "good" indication. Set it for 4GB space and said go;
after about 10 minutes of actually looking like it was working I got this:

```

An uncaught exception was raised
{Errno 5} Input/Output Error 
```


Tried formating to two 3.5GB partitions at Fat 16. Started loading then:
```

An uncaught exception was raised
{Errno 5} Input/Output Error 
```


Sometimes you just want to shoot yourself!! The Live CD I was using for this was corrupt! Stuck in another and it worked first time!](*,):oops:

---

### Post by jimbo99 on 2009-12-05
You are using the live CD for a reason?  It won't work from your install?

---

### Post by Bartender on 2009-12-05
I found it easier to set up the USB with the Ubuntu LiveCD in the tray.  I didn't boot from the LiveCD.  I booted up in Linux, then plugged in the thumb drive, then dropped the LiveCD in the tray, then started the utility.

---

