---
title: "I'm an Idiot... AKA: Unbacked up Files..."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by underparnv on 2009-01-12
Hey everyone,

So I have problems. Mostly with my self, but I'm hoping there are some people out there smarter than I that can help me fix my problem.

I was running Windows XP on my laptop for about three years and had accumulated quite a few pictures in that amount of time. About every year I would back these pictures up to CD and would store them away for safe keeping.  About four weeks ago I decided to switch to Ubuntu full time.

Before installation I didn't back up anything. The only reason I can think I did such a thing was that I was excited to use Ubuntu full time and I was about to go on vacation. In all honesty, that's a lame excuse. I should have known better...but still didn't do it.

Bottom line is that I have lost about a year's worth of photos. I'm wondering if there is a way to get back at those pictures...When I installed Ubuntu it did ask to format the drive, and I clicked yes, so I'm assuming everything is gone. However, I watch a lot of Forensic Files on Discovery Channel so I know that the CIA, FBI, etc., can get at data on a formatted drive...right?  :P

Any and all help would be very much appreciated; both from me and my wife who is already missing our Maui pictures 

Thank you,

underparnv

---

### Post by oilchangeguy on 2009-01-12
this may help:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by jrusso2 on 2009-01-12
Of course there is always a way.  Depends on what you want to spend.  A Data recovery person charges start about $500.

You could just buy some recovery software and try yourself.  The more you use the PC during this period though the harder recovery becomes you might overwrite some of the photos.

---

### Post by soulster on 2009-01-12
There are quite a few software products out there that claim to recover files from formatted drives.  The majority of these run on Windows (see [http://www.recovermyfiles.com/](http://www.recovermyfiles.com/) or [http://www.ontrackdatarecovery.com/data-recovery-software/](http://www.ontrackdatarecovery.com/data-recovery-software/)), so I'm not sure they'd be much help unless you can connect your drive to a windows computer as a secondary device and use it that way.

You best bet, IMO is to Google something like "formatted file recovery" or "Linux formatted file recovery" and find the best software solution.

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
>  Any and all help would be very much appreciated; both from me and my wife who is already missing our Maui pictures  

Glad to read you like Ubuntu.

See here : [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

And instead of making backups once a year, I suggest making backups every half a year to start with ;-)

---

### Post by underparnv on 2009-01-12
You all are the best!

I'm going to try out TestDisk and PhotoRec as soon as I can get internet access on the laptop (am at work with no wireless...), which will be this evening. I will be sure to report my findings...or lack thereof.

**albinootje**
Ya think?!?!  :)  I'm also looking at backup solutions for Ubuntu...and have found a couple already!  :P

Thank you again!!

---

### Post by wolfen69 on 2009-01-12
> **albinootje said:**
> Glad to read you like Ubuntu.

See here : [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

And instead of making backups once a year, I suggest making backups every half a year to start with ;-)

i back up every 2-3 days. i never worry. then i back up the back up. :)

---

### Post by DGortze380 on 2009-01-12
Data Recovery 101 ... 

1) STOP MOUNTING THE DISK.

That means use a live cd that won't automount. I like Knoppix.

2) Don't do anything until you IMAGE THE DRIVE.

You can do this with a variety of tools. I suggest the dd command as it will do a bit for bit copy of the whole drive.

3) BACK UP AND WORK FROM THE IMAGE, NOT THE DISK

If anything goes wrong during the recovery, you can go back and try again!

---

### Post by DGortze380 on 2009-01-12
To ensure you actually do need to do any recovery... can you please verify:

1) During the install, did you choose: 1) 'Guided - Use Entire Disk' or 2) 'Guided - Use Largest Free Space'

2) Please post the output of: df -l

---

### Post by mapes12 on 2009-01-12
I can see you have received lots of help with your problem and here's another resource just in case: [http://www.runtime.org/](http://www.runtime.org/)

---

### Post by underparnv on 2009-01-12
> **DGortze380 said:**
> To ensure you actually do need to do any recovery... can you please verify:

1) During the install, did you choose: 1) 'Guided - Use Entire Disk' or 2) 'Guided - Use Largest Free Space'

2) Please post the output of: df -l

1.) I believe I selected 'Guided - Use Entire Disk'

2.) Seen below:

```
Filesystem	1k-blocks	Used		Available	Use%	Mounted on
/dev/sda1	56300668	25855532	27585168	49%	/
tmpfs		  240360	       0	  240360	 0%	/lib/init/rw
varrun		  240360	     204	  240156	 1%	/var/run
varlock		  240360	       0	  240360	 0%	/var/lock
udev		  240360	    2740	  237620	 2%	/dev
tmpfs		  240360	     608	  239752	 1%	/dev/shm
lrm		  240360	    2000	  238360	 1%	/lib/modules/2.6.27-9-ge
neric/volatile
```

---

### Post by DGortze380 on 2009-01-12
> **underparnv said:**
> 1.) I believe I selected 'Guided - Use Entire Disk'


I agree, based on that output, it looks like you've formatted the entire disk. Not a difficult fix, testdisk is a good utility, but I do suggest you work on an image, not the actual drive.

Good Luck!

---

### Post by underparnv on 2009-01-12
> **DGortze380 said:**
> I agree, based on that output, it looks like you've formatted the entire disk. Not a difficult fix, testdisk is a good utility, but I do suggest you work on an image, not the actual drive.

Good Luck!

Man you guys/gals are fast!!!  :P

Does this mean I should boot from the Live CD that I have for Ubuntu?

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
> Man you guys/gals are fast!!!  :P

Does this mean I should boot from the Live CD that I have for Ubuntu?

I also recommend first making a complete disk-image to some usb-disk, with dd.
After that you can freely try to recover on your real hard disk, since you'll have the exact backup.

And yes, boot from the Ubuntu installation cdrom.
That will work from cdrom and RAM only, and you can install testdisk and other software in RAM too during that "live session".

---

### Post by underparnv on 2009-01-12
> **albinootje said:**
> I also recommend first making a complete disk-image to some usb-disk, with dd.

Noob question forthcoming: What is "dd"?

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
> Noob question forthcoming: What is "dd"?

dd is a low-level disk copy program, included in almost every Linux distribution by default

```

$ ls -la /bin/dd 
-rwxr-xr-x 1 root root 50820 2008-06-27 02:31 /bin/dd

```

Here's an example how to use it, let's assume your hard disk is /dev/sda.
And let's assume your external usb-disk is /dev/sdb, and is mounted with the partition /dev/sdb1 at /media/disk :
```

sudo dd if=/dev/sda of=/media/disk/dd-copy-of-hard-disk

```
After it's finished you should have an exact copy of your whole disk.

---

### Post by lswest on 2009-01-12
> **underparnv said:**
> Noob question forthcoming: What is "dd"?

It's a unix utility to handle raw data and do basic things such as copying.  It copies at a low-level, making it useful for creating images of disks.

see: [http://en.wikipedia.org/wiki/Dd_(Unix)](http://en.wikipedia.org/wiki/Dd_(Unix))

beaten by seconds...

---

### Post by underparnv on 2009-01-12
> **lswest said:**
> It's a unix utility to handle raw data and do basic things such as copying.  It copies at a low-level, making it useful for creating images of disks.

see: [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

beaten by seconds...

This forum is so freaking awesome!!  :P

Thanks a ton!!  Working on copying that image from a LiveCD now!

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
> This forum is so freaking awesome!!  :P


/me kneels down on both knees.. and whispers :

... Thy Wish, Master ?

:)

---

### Post by underparnv on 2009-01-12
> **albinootje said:**
> /me kneels down on both knees.. and whispers :

... Thy Wish, Master ?

:)

Ok...here is where I am at:

I downloaded and created an ISO disk of Ubuntu Rescue Remix.  How do I run photorec and save the results to a USB drive?

I am looking in the media folder and see usb then usb0 thru usb7, but the one text file I have on the drive isn't showing up in any of those sub folders. Therefore, I don't know where to tell photorec where to save the files that it locates...

Any pointers?  :D

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
> Ok...here is where I am at:

I downloaded and created an ISO disk of Ubuntu Rescue Remix.  How do I run photorec and save the results to a USB drive?

I am looking in the media folder and see usb then usb0 thru usb7, but the one text file I have on the drive isn't showing up in any of those sub folders. Therefore, I don't know where to tell photorec where to save the files that it locates...


Ouch.. can you post the complete output of the following, while the usb disk is attached :
```

sudo update-usbids
lsusb
sudo fdisk -l
mount

```

And, by the way, is your usb-stick large enough to hold a raw copy of your hard disk ?

---

### Post by underparnv on 2009-01-12
> **albinootje said:**
> Ouch.. can you post the complete output of the following, while the usb disk is attached :
```

sudo update-usbids
lsusb
sudo fdisk -l
mount

```

And, by the way, is your usb-stick large enough to hold a raw copy of your hard disk ?

Output of sudo update-usbids
```
sudo: update-usbids: command not found
```

:P

I assume that is because I'm running from the Live CD of Ubuntu Rescue Remix...right?

USB drive is 120GB and the hard drive I'm trying to get data from is only 40GB...so should be alright there  :)

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
> Output of sudo update-usbids
```
sudo: update-usbids: command not found
```

:P

I assume that is because I'm running from the Live CD of Ubuntu Rescue Remix...right?

Quite possible, yes, I don't know that cdrom, does it have a GUI, or is it text based only ?
According to [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) it's text based.

Please boot from the Ubuntu installation cdrom instead, because then you can have a GUI, which makes it much easier to copy and paste large amounts of text, and makes it easier to work with usb disks and usb sticks, and use the Internet with a web-browser.
> 

USB drive is 120GB and the hard drive I'm trying to get data from is only 40GB...so should be alright there  :)

Good :)
Please try this :

```

sudo apt-get update
sudo apt-get install usbutils
sudo update-usbids
lsusb
sudo fdisk -l
mount

```

Those are all commands per one line, hit <enter> after each line.

---

### Post by underparnv on 2009-01-12
> **albinootje said:**
> Quite possible, yes, I don't know that cdrom, does it have a GUI, or is it text based only ?

Text based only.

> **albinootje said:**
> Please try this :

```

sudo apt-get update
sudo apt-get install usbutils
sudo update-usbids
lsusb
sudo fdisk -l
mount

```

Those are all commands per one line, hit <enter> after each line.

That one will have to wait unfortunately since I don't have internet access on the laptop right now...

Will try that this evening though!

Thanks!

---

### Post by underparnv on 2009-01-12
I was, however, able to get the output of lsusb from within the Ubuntu LiveCD.  It is below:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0917:0524 SmartDisk Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Does that help any?

---

### Post by underparnv on 2009-01-12
Ok...so "sudo fdisk -l" and "mount" do run.  Each of the outputs are below:

**sudo fdisk -l**
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 secrots/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start      End      Blocks   Id  System
/dev/sda1   *		1     7121    57199401   83  Linux
/dev/sda1            7122     7296     1405687+   5  Extended
/dev/sda5            7122     7296     1405656   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 secrots/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47592c40

   Device Boot      Start      End      Blocks   Id  System
/dev/sdb1               1    19457   156288321    c  W95 FAT32 (LBA)
```

**mount:**
```
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusect1 on /sys/fs/fuse/connections type fusect1 (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
```

---

### Post by albinootje on 2009-01-12
> **underparnv said:**
> 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 secrots/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47592c40

   Device Boot      Start      End      Blocks   Id  System
/dev/sdb1               1    19457   156288321    c  W95 FAT32 (LBA)[/code]

OK, thanks.
Your usb disk is 160 Gb big ? Or does your computer have two disks ? I think you mentioned that it's a laptop, no ? Then it's very unlikely it has two disks onboard.

Can you do the following :
```

sudo mkdir /media/usb-disk
sudo mount /dev/sdb1 /media/usb-disk -t vfat

```
And then browse to /media/usb-disk inside your file manager (Nautilus, -> Places -> Home -> File System -> Media -> usb-disk)

Beware.. FAT32 has a 4 Gb file size limitations, with that you cannot make a dd image.
How full is the usb-disk ? 
Would you mind creating another partition on the usb disk and make that a Linux ext3 or NTFS partition ?

---

### Post by underparnv on 2009-01-14
Ok...so I was able to run PhotoRec and retrieve ***some*** of the photos. Is there anyway I can dig deeper into what is in there???

The reason being...the Maui pictures didn't make it...at least not that PhotoRec has found...

I'm about to give Drive Savers a call to see if they could do anything more...

Thanks!

---

