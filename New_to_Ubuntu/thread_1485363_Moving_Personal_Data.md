---
title: "Moving Personal Data"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by bj218 on 2010-05-16
I would like to move my personal data from WinXP to a Ubuntu partition.
My WinXP data is on a separate partition ie /dev/sda6. I would like to 
move some of my personal data to separate partition on my Ubuntu drive 
ie /dev/sdb7. Can someone give me a very detailed set of instructions 
on how to do this?

---

### Post by lkraemer on 2010-05-16
First you need to explain in detail what partitions exist,
and what each partition contains.

Open a Terminal Window and do:
```

sudo fdisk -l 

```
and post the output.

With this information someone will respond.

lk

---

### Post by Miljet on 2010-05-16
Can you click on Places and access the data on sda6? If so, can you click on Places and access the sdb7 partition? If so, with both windows open, drag and drop whatever you want to copy.

If you can not access either partition, explain which one, and what happens when you try to access it.

---

### Post by bj218 on 2010-05-17
> **lkraemer said:**
> First you need to explain in detail what partitions exist,
and what each partition contains.

Open a Terminal Window and do:
```

sudo fdisk -l 

```
and post the output.

With this information someone will respond.

lk

WinXP is on /dev/sda1 & Data160 (My Data) is on /dev/sda6
Ubuntu is on /dev/sdb1 & I want put my data on /dev/sdb7

---

### Post by bj218 on 2010-05-17
> **Miljet said:**
> Can you click on Places and access the data on sda6? If so, can you click on Places and access the sdb7 partition? If so, with both windows open, drag and drop whatever you want to copy.

If you can not access either partition, explain which one, and what happens when you try to access it.

I can access both but when I try to drag & drop I get a message that says I do not have permission!!

---

### Post by lkraemer on 2010-05-18
Well, I shouldn't respond with the information you posted versus what I
asked for...because instructions are for you to follow, but I'm going
to make one last post.....because I am trying to help you along with others.

You can ONLY have four (4) Primary Partitions on any PHYSICAL HARD DRIVE.
Since you have TWO Hard Drives (sda & sdb) with some sort of mix of 
Partitions (Logical and Primary) because you have numbers greater than 
4.  With a Logical Partition you can insert multiple Partitions.  The
way you can find more info, so you can figure out what to do is to
install Gparted, then Log out and Log back in.

Run Gparted.  Figure out what the Graphic is telling you about the Partition
Layout.....For both Drives.  When you find sdb7, find the mount point.
AH, now you are making progress....

Open a terminal Widow and locate that mount point.  Look at the owner
and permissions.  Change the owner from root to yourlogin and also change
the permissions.  If your /home is a separate partition you can use that
as a guide.

This means you will be using the following commands:
```

man
chown
chmod

```
(and a combination of each ie.  man chown     &     man chmod)

And then you're done.....How easy was that?

lk

---

### Post by bj218 on 2010-05-18
file:///home/bill/Desktop/Screenshot-bill@bill-desktop:%20~.png
Can you do anything with the above??

---

### Post by lkraemer on 2010-05-18
I am afraid that doesn't tell me a thing. 

I need a png attached like this.

lk

---

### Post by bj218 on 2010-05-19
How do I make a png attachment? I made a copy in OOo but I do not know how to get it 
to you?

---

### Post by lkraemer on 2010-05-19
APPLICATIONS -> ACCESSORIES -> TAKE SCREENSHOT -> SELECT AREA TO GRAB
Save the file!

In your posting scroll down to MANAGE ATTACHMENTS, then UPLOAD, CLOSE
and POST!

Haven't you ever used Snagit in M$?

lk

---

### Post by bj218 on 2010-05-19
I hope this works, Never heard of Snagit how could I learn to use it?

---

### Post by gordintoronto on 2010-05-19
> **bj218 said:**
> I hope this works, Never heard of Snagit how could I learn to use it?

Good work, attaching the image.

Some people find it helpful to organize files on D:, E:, F: etc in Windows. However, Linux file management is built around folders, not partitions.

There is a huge benefit to having separate partitions for / (root) and /home, and one more that only applies if you are hosting web sites. Beyond that, more partitions are just a PITA in Linux, in my opinion.

I really suggest consolidating several partitions on SDB so you have just root and home partitions, then set up folders for separating your files. Ubuntu will automatically give you some, but I use a few others such as ~/Downloads (that's home/Downloads)

Note also that folder (and file) names are case sensitive in Linux, so Desktop is not the same as desktop.

---

### Post by lkraemer on 2010-05-19
Well, it looks as if I was correct, and you are making progress...... :~)

So start with Posting #6 Paragraph 3 and do what it describes.

ZIT ZOT......shouldn't take more than 5-7 minutes.

lk

---

### Post by bj218 on 2010-05-20
I still don't under stand how I move data from 1 drive to the other?

---

### Post by lkraemer on 2010-05-20
OK, sda6 is a ntfs partition with no mount point assigned.
You will be READING ONLY from this drive so you just need to
have it mounted and then do the copy.  When you are finished
you just need to un-mount the drive.

Open a terminal Window to mount the drive:
```

cd /
cd mnt
ls -alt
cd ..
cd media
ls -alt
sudo mkdir winsa6
sudo mount -t ntfs /dev/sda6 /media/winsa6

```
You just verified nothing was mounted in /mnt because nothing is
displayed.  Everything is under /media nowdays....
You created a subdirectory/folder for the mount point named winsa6
and then mounted the NTFS partition there.  No permissions or owner
changes need to be made because you are reading only.  It's not a good
practice to write to NTFS Partitions, but it does work.  I've done it
lots.

At this point you should be able to use the GUI to select what you want
and copy those files/folders to sdb7.  You may have to go to COMPUTER
and mount that destination partition by clicking on it so it mounts.

When you are finished you will need to umount the NTFS drive, and then I
always remove the subdirectory.
```

sudo umount /media/winsa6
sudo rmdir winsa6

```

That should get you copying.

lk

---

### Post by bj218 on 2010-05-22
When I tried to drag & drop an Item this is what I got. It looks like I need to put sdb7 in the terminal but I don't know how to do that?

---

### Post by lkraemer on 2010-05-22
I am wondering if you have sdb7 mounted?  I can't determine that from what
your snapshot displays.  Try this:  PLACES -> COMPUTER -> HELP -> ABOUT
This is Nautilus.  On the left menu you should be able to locate sdb7
the ~9 Gig partition you created.  Left click on it to mount it.
Then try the copy you previously tried.  Hopefully you won't have to
change the Owner and Permissions to do the copy.

If you click on Filesystem in the left menu, then the folder media or
mnt you should be able to locate sdb7.  If not you will need to create
another subdirectory and mount sdb7 as you previously did for sda6.
Just name the folder different than the previous one. Assume you named
it mysdb7.  You would use:
```

cd /
cd media
sudo mkdir mysdb7
mount /dev/sdb7 /media/mysdb7
cd /
cd media/mysdb7
sudo mkdir billxpdata
ls -alt
# (If the owner is not bill:bill you need to change the owner to #yourloginuser name and you need read write permission like this
#example......drwxr-xr-x 86 larry larry 16384 2010-05-22 17:22 larry)
sudo chown bill:bill billxpdata
sudo chmod 755 billxpdata
ls -alt
exit

```

Then try the copy with Nautilus.

Typically, you mount a drive, do a copy, then unmount the drive.
If it isn't done automatically for you, you will need to do it manually.

Now that you're done, unmount both sda6 & sdb7.
```

sudo umount /media/mysdb7
sudo umount /media/winsa6

```

lk

---

### Post by bj218 on 2010-05-23
Thank You Thank You This time it worked. I relay got a lesson and without you're help I would never have made it!!

---

### Post by lkraemer on 2010-05-23
You are Welcome!  As you probably understand now....I added a few
Terminal commands along the way, just to get a little time under
your belt in a Console or Terminal.  That way next time you won't
be so scared of a Terminal Window.

lk

---

