---
title: "Ubuntu no longer to read Lacie External H.D"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-26
Hello everyone,

I used Gparted in the Hardy's OS repositories to unmount the External HD partition, that I had been using for backup, as I wanted to rid myself of the backups on it. Then I found that Sbackup would not read it as what it did before (named 500.1 GB Media). I wrote down two of the partitions:

/dev/sdf2
/dev/sdf5 as an Ext 3

There was was one more, but I didn't write it down and don't remember it.

Then I unmounted the /dev/sdf5 partition, thinking when I rebooted, that the OS system would read it as before, when I had initially used Gparted from the CLI to rid the NTFS information that was on it. 

Well, it didn't work, and now Hardy does not recognize the HD. I booted the Hardy Live CD and took this screenshot, to show the properties to you.

Any ideas?

See screenshot below

---

### Post by brunogirin on 2009-08-26
If you wanted to get rid of the backups on your drive, why use GParted and not just delete the files? Can you open GParted again while the drive is connected and post of screenshot of the window please?

---

### Post by WitchCraft on 2009-08-26
> **brunogirin said:**
> If you wanted to get rid of the backups on your drive, why use GParted and not just delete the files? Can you open GParted again while the drive is connected and post of screenshot of the window please?

Exactly, and why unmount a drive with GParted? 
You can simply unmount it with the command line tools.

Given your description I have no idea what you did, but you probably deleted your hard drive.

---

### Post by Zack McCool on 2009-08-26
Your screenshot shows that the disk is currently mounted on the LiveCD at /media/disk-2, as an ext3 partition.

What this means is that there is nothing wrong with the disk.

How about you boot to your OS on the HD and get information that way.  Perhaps show us the results of the following commands:

sudo fdisk -l /dev/sdf
mount

This will show the current partitions that are seen by your OS, and what is actually mounted.  From there, it should be a little easier to give you support.

---

### Post by mikodo on 2009-08-26
[QUOTE=brunogirin;7848303]If you wanted to get rid of the backups on your drive, why use GParted and not just delete the files? Can you open GParted again while the drive is connected and post of screenshot of the window please?[/QUOTI 

I admit it was the wrong thing to do, I didn't know how to completely delete the whole partition of files. Anyways here's a screenshot of Gparted from the Live CD of the External HD.

Thanks for the help,

---

### Post by mikodo on 2009-08-26
> **WitchCraft said:**
> Exactly, and why unmount a drive with GParted? 
You can simply unmount it with the command line tools.

Given your description I have no idea what you did, but you probably deleted your hard drive.


Because I am still unfamiliar with shell scripts! But anyways now the External HD is showing  on the Desktop, under Places, and in Gparted, since entering into Terminal the previous poster's commands. What the Heck??

---

### Post by mikodo on 2009-08-26
> **Zack McCool said:**
> Your screenshot shows that the disk is currently mounted on the LiveCD at /media/disk-2, as an ext3 partition.

What this means is that there is nothing wrong with the disk.

How about you boot to your OS on the HD and get information that way.  Perhaps show us the results of the following commands:

sudo fdisk -l /dev/sdf
mount

This will show the current partitions that are seen by your OS, and what is actually mounted.  From there, it should be a little easier to give you support. 

Here it is

---

### Post by mikodo on 2009-08-26
> **Zack McCool said:**
> Your screenshot shows that the disk is currently mounted on the LiveCD at /media/disk-2, as an ext3 partition.

What this means is that there is nothing wrong with the disk.

How about you boot to your OS on the HD and get information that way.  Perhaps show us the results of the following commands:

sudo fdisk -l /dev/sdf
mount

This will show the current partitions that are seen by your OS, and what is actually mounted.  From there, it should be a little easier to give you support.

Maybe this one is easier for you to see!

---

### Post by mikodo on 2009-08-26
Well thank you everyone,

The External HD is back and showing on Desktop, in Places, Gparted, and Sbackup. It is clean of all data from previous backups and just now received new data from a new Sbackup run.

Don't know what brought the HD back? The booting of the Live CD, or the running of the  sudo fdisk -1/dev/skf
                mount?

Anyways, I was able to do what I wanted to do, even if it meant going about it in a convoluted way, and having to request the help of you folks!

IF ANYONE WOULD BE SO KIND TO DIRECT ME TO THE TERMINAL CODE TO DELETE DATA OFF A HARD DRIVE, I'M SURE IT WOULD BE EASIER THAN GOING ABOUT IT THE WAY I JUST DID!!!

mikodo

---

