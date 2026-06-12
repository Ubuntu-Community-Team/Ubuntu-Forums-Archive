---
title: "Boot timeout failure?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by heaslip on 2010-05-25
I'm running 9.10 dual boot with Windows XP. But 9.10 won't boot today.  Its been Ok since installed a month ago.  The message reads: "Gave up  waiting for root device". Then: "Alert!  /dev/disk/by-uuid/98104/c2e..............."and so it goes...."....does  not exist. Dropping to a shell!"

Well it existed this morning! What have I done wrong? Anyone tell me  what this means and how to fix it?

---

### Post by Ozymandias_117 on 2010-05-25
Boot to a live CD, mount your Linux partition, then post the results of these commands:
```
sudo fdisk -l
```
```
sudo cat /etc/fstab
```

Edit: If you can tell which is your Linux partition from fdisk -l then post the output of ```
sudo blkid /dev/*linux_partition*
```

---

### Post by heaslip on 2010-05-25
the Live CD doesn't recognise my existing partition as 9.10 and wants to partition my Windows partition to create another new partiton for 9.10. Should I proceed?

---

### Post by Don1500 on 2010-05-25
> **heaslip said:**
> the Live CD doesn't recognise my existing partition as 9.10 and wants to partition my Windows partition to create another new partiton for 9.10. Should I proceed?

Do you want to erase your windows?

I didn't think so. Boot to live CD, open system=>administration=>gparted and take a look there to see if your linux partition is ok. 

you can also use system=>administration=>Disk Utility to look at your disk/partitions. A screen shot of this might come in handy for troubleshooting. (I attached a screenshot of mine so you can see what it would look like.)

---

### Post by heaslip on 2010-05-25
Reply to Ozymandias_117: Results of first two commands:
   root@ubuntu:/home/ubuntu# sudo fdisk -1
  fdisk: invalid option -- '1'
   
  Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
         fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
         fdisk -s PARTITION           Give partition size(s) in blocks
         fdisk -v                     Give fdisk version
  Here DISK is something like /dev/hdb or /dev/sda
  and PARTITION is something like /dev/hda7
  -u: give Start and End in sector (instead of cylinder) units
  -b 2048: (for certain MO disks) use 2048-byte sectors
  root@ubuntu:/home/ubuntu# sudo cat /etc/fstab
  aufs / aufs rw 0 0
  tmpfs /tmp tmpfs nosuid,nodev 0 0
  /dev/sda5 swap swap defaults 0 0
  /dev/sda7 swap swap defaults 0 0


Reply to Don 1500:
I checked the Disk Utility. My 360GB linux partition is shown but described as "Unrecognised" and "unknown or unused". Everything else is at it should be. I can access the windows patrition from Live Disk and all other media, but not the "unrecognised" its decribed as "dev/sda6" and type is Linux (0x83). Gparted shows it as "ext4" with 16.6 GiB used. I'm no wiser but I hope this means something?

---

### Post by Ozymandias_117 on 2010-05-25
Sorry, the fdisk is a lower case L, not the number 1. Also, we need the /etc/fstab on the partition we're trying to fix. Sorry for the confusion.

---

### Post by Don1500 on 2010-05-26
> **heaslip said:**
> 

Reply to Don 1500:
I checked the Disk Utility. My 360GB linux partition is shown but described as "Unrecognised" and "unknown or unused". Everything else is at it should be. I can access the windows patrition from Live Disk and all other media, but not the "unrecognised" its decribed as "dev/sda6" and type is Linux (0x83). Gparted shows it as "ext4" with 16.6 GiB used. I'm no wiser but I hope this means something?

Using Gparted can you re-format that linux partition (sda6) as .ext4, and try to reinstall Ubuntu there. You may also divide that partition into one 50gb and one 290gb partitions. When you install Ubuntu put your root files (/) on the 50gig and your home files (/home) on the 290gig. This could save you if your root dies or when you update Ubuntu next time. Just don't format the drive during installation and all your files are safe.

There is something bothering me, how many partitions do you have on this drive? How big is it? When responding select "Go Advanced" and use "Manage Attachments" below to add a screen shot of "Disk Utility" with this drive highlighted.

---

### Post by heaslip on 2010-05-29
I can't seem to add a screenshot because i can't find "system" and "disk utility" in the attachment browser menu.

/dev/sda6 is my Linux partition and it is ext4. But it is described as "not mounted". I thought that was the problem. I have tried to mount it using "sudo mount /dev/sda6 mnt" (from Community documentation) but that command didn't do it.

According to Disk Utility: 

sda is 750GB hard disk

sda1 is windows xp  (371 GB)

sda2 is 379 GB unrecognised GParted says "busy - at least one logical partition is mounted"

sda 5 is Linux swap 9.3 GB (0x82). Gparted - "active"

sda6 is 360 GB unrecognised (but thats where I put Ubuntu). GParted says 16.6 GiB used, and its ext4. Linux (0x83),  Not mounted.

sda7 is Linux swap 9.3 GB (0x82) - Active

Something very odd. I don't understand whats wrong?

Help much appreciated

---

