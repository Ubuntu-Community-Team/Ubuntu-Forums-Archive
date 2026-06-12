---
title: "hard drive not showing up"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Spencer Caplan on 2009-10-11
I came across an old laptop with Windows XP on it that would not boot because of a corrupted Windows file. I booted up with a live CD of Ubuntu and everything apeared to be working okay, the hard drive showed up with both fdisk and with gparted. I wanted to zero the drive so I went into terminal and...

sudo dd if=/dev/zero of=/dev/sda

It appeared to work so I rebooted the live CD this time planning to install it. Now gparted says that there are no devices detected and sudo fdisk -l does not display anything. What could the issue be? What can I do to fix it, or install Ubuntu?

---

### Post by Spencer Caplan on 2009-10-11
Just to give more information I ran sudo lshw -C disk. It displayed:

*-disk                  
       description: SCSI Disk
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
  *-cdrom
       description: DVD reader
       product: UJDA760 DVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted


I also ran sudo fdisk /dev/sda. It displayed:

Unable to read /dev/sda

I am at a loss. Is there anything that I can do to fix my hard drive issues?

---

### Post by Spencer Caplan on 2009-10-11
Sorry to keep posting, but just to see what would happen I tried running sudo dd if=/dev/zero of=/dev/sda. This time it displayed something much different than the first time.

dd: writing to `/dev/sda': No space left on device
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00137864 s, 0.0 kB/s

What is the problem?

---

### Post by powel212 on 2009-10-11
If it were me I'd pull the Hard drive out and test it in another machine.

As a laptop it will have a 2.5" Drive in it which won't plug directly into a standard ide cable so you will need to buy a 2.5" enclosure for 10 Bucks, and then plug it into another machine's USB port for testing.

I hope that helps.

Powel

---

### Post by mikechant on 2009-10-12
You orignal post said that fdisk displayed nothing, then a later post said that it displayed 'Unable to read /dev/sda'. So did this change? If so, can gparted now see the device? Have you looked in the BIOS setup to see if it's being detected there?

---

### Post by Spencer Caplan on 2009-10-12
> **mikechant said:**
> You orignal post said that fdisk displayed nothing, then a later post said that it displayed 'Unable to read /dev/sda'. So did this change? If so, can gparted now see the device? Have you looked in the BIOS setup to see if it's being detected there?

Well, the exact wording of each fdisk was slightly different. The first one, which displayed nothing, was:

sudo fdisk -l

The second one which displayed "Unable to read /dev/sda" was:

sudo fdisk /dev/sda

---

### Post by Spencer Caplan on 2009-10-13
Any ideas?

---

### Post by lavinog on 2009-10-13
does bios detect the drive?
what brand drive is it?  some manufactures have a live cd for testing the drive.

Edit: Does dmesg report anything about the drive?

---

