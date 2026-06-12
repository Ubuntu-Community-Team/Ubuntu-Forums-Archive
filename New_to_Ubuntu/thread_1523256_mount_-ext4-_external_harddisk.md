---
title: "mount -ext4- external harddisk"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Korenwolf on 2010-07-03
Hello All,

I've got an external harddisk that is I formatted as an 'ext4' instead of 'fat' by accident.

I didn't think it would be a problem, as I won't be using it with windows, so I didn't reformat them to fat.

But now I'm having trouble mounting the ext4 formatted harddisk.
That is to say, It does not show up when I connect it to the USB port.

Any tricks to get it mounted and usable?

FYI, I'm working on Ubuntu 10.04

Cheers,
Erwin

---

### Post by Sin@Sin-Sacrifice on 2010-07-03
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) but you're also going to have to change the permissions of the disk so that your user can write to it.

---

### Post by Korenwolf on 2010-07-03
Thanks a lot for the quick responce.
I didn't see that page in the documentation, silly me :)

---

### Post by Korenwolf on 2010-07-03
I found the external hard disk in the media folder of the filesystem.

I can't copy anything from the external harddisk to the internal harddisk, I always get the message that it is a "read-only" file.
I tried changing the permissions of the harddisk, but it doesn't apply them to the subfolders.
And changing all folders and files on that disk manually before being able to copy them will take ages.

Any thoughts?

Cheers,
Erwin

---

### Post by gallifrey on 2010-07-03
try this:

sudo chown username:username /dev/sdx 
sudo chmod 755 /media/name-of-your-disk

---

### Post by Korenwolf on 2010-07-03
> **gallifrey said:**
> try this:

sudo chown username:username /dev/sdx 
sudo chmod 755 /media/name-of-your-disk

That gives me a load of errors, but maybe I did it wrong

I don't know what the name is of the disk, I checked it in the terminal with fdisk -1 if I'm not mistaken.
But there where so many names, I didn't know which was the correct one.
I only know that it's called Freecom 160 in the file browser.

I added a screenshot of how the files and folders look on the external disk to clarify

---

### Post by gallifrey on 2010-07-03
Okay, try this:

sudo fdisk -l (as in L)

It'll bring up a list of all partitions. Your main internal hard disk will be /dev/sda, and the partitions will be /dev/sda1. /dev/sda2, etc.

An external hard disk will show up as /dev/sdb1 or dev/sdc1. Anything apart from /dev/sda.

For example, let's say it is /dev/sdd1. And it is called Freecom 160.

You need to enter this:

sudo chown username:username /dev/sdd

then, if that goes well:

sudo chmod 755 /media/"Freecom 160" 

Notice the quotation marks around the name (terminal doesn't handle spaces well :) ). And make sure you get the case right in the disk name, i.e. if it shows up as Freecom, type Freecom, and not freecom. 

I do hope this helps.:D

---

### Post by Korenwolf on 2010-07-03
Together with your latest post, and another thread here on the forum I solved my problem.

Many thanks for the help

Cheers,
Erwin

---

