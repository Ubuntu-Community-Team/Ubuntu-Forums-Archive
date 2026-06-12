---
title: "Out of space on hda1"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by cartisdm on 2009-02-04
On a recent install of Mythbuntu 8.10 I have the following partitions on my 40gb harddrive.
```

/dev/hda1      ext 3        9.86gb(size)       9.72(used)
/dev/hda2      extended     27.41gb            ---
   /dev/hda5   linux-swap   862mb              ---
   /dev/hda6   xfs          26.57gb            215.94

```

I also have a separate 120gb harddrive details below:

```
/dev/hdb1     ext3          111.76gb(size)     31.54gb(used)
```


I'm not quite sure why the 9.86gb and 26.57gb partitions are there, I must have created them by mistake during installation.  Anyway, the 9.72gb space is obviously full and is causing me lots of problems (can't do updates etc.)  I have a liveCD of gParted running but it won't let me re-size the partitions around and I don't have enough experience to know what I'm really doing.

What solutions do I have for solving this space issue?  The hda1 holds all my important folders that the OS defaults to so it being full creates a lot of problems!

---

### Post by michaeless on 2009-02-04
Try:

sudo apt-get autoremove
and
sudo apt-get clean

That might clean out some stuff.

---

### Post by sowelie on 2009-02-04
Definitely clean things up...but for a more long term solution, I'd be willing to bet a lot of the space is your home folder.  I'd recommend moving your home folder to your bigger drive.  Having your home folder separate is better anyway because if you re-install you don't have to worry about backing up, then restoring everything.

---

### Post by cartisdm on 2009-02-04
> **michaeless said:**
> Try:

sudo apt-get autoremove
and
sudo apt-get clean

That might clean out some stuff.

I'll try that out.  In the long run though I'll need to have more space.

---

### Post by cartisdm on 2009-02-05
> **sowelie said:**
> Definitely clean things up...but for a more long term solution, I'd be willing to bet a lot of the space is your home folder.  I'd recommend moving your home folder to your bigger drive.  Having your home folder separate is better anyway because if you re-install you don't have to worry about backing up, then restoring everything.

My 120gb harddrive doesn't show up as a second drive.  I mount it inside 

```
/media/share
```

How do I move my home directory inside that while keeping the file paths the same? (I don't want to have to go through and manually change the path for everything that defaults to the home directory now)

---

### Post by Elfy on 2009-02-05
If you're not using the xfs partition then why not add it to hda1 then you'd have a 36Gb root drive

You'd need to use a livecd.

---

### Post by mikechant on 2009-02-05
*I have a liveCD of gParted running but it won't let me re-size the partitions around and I don't have enough experience to know what I'm really doing.*

You probably just need to right click on the 'swap' partition and select 'swapoff', then all the partitions should be unmounted and you can resize, delete etc.

If the xfs partition was a mistake, delete sda6 and sda5 (it's easy to recreate the swap later). Then you can delete sda2, the now-empty extended partition. Next, create a new swap partition - I'd recommend putting it at the end of the disc. Then you can resize sda1 to whatever you want.  Then you'll have
sda1 - resized to what you want
unallocated space for future use
sda2 - new swap

or just
sda1 followed by sda2 if you used all the space


You probably want to back up sda1 to your other drive before you repartition - you could use partimage for this. Gparted is generally very reliable but there are always data loss risks with repartitioning (e.g. power loss).

---

### Post by cartisdm on 2009-02-05
Ok, that's what I'll try this weekend.  I'm going to delete sda5,6 then delete sda2.  Resize sda1 to use all the space (except for what I leave for the swap).  I'll let you know how it goes

---

### Post by cartisdm on 2009-02-06
Well, I decided to risk it and not make a backup.  I couldn't remember if anything was on the sda2 partition or not.  Apparently there was, haha.  At least I figured out how to do the resizing and such, everything is a lesson right?

Reinstalling now, but I had some changes I wanted to make anyway so it's not the worst thing in the world....

---

