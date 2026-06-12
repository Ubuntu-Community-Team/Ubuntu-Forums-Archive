---
title: "Some smart advice please"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by ericstrom on 2010-09-25
Running Ubuntu 10.04 Lucid Lynx. Everything is currently on a 40 GB IDE drive that's getting full. I have a second 40 GB IDE drive that's empty. I also have a 160 GB external drive that connects via USB (originally purchased as a backup). No longer need a back up as I have dropbox.

I would like to be able to run Windows XP and a few programs that wont run under Wine on occasion. Was thinking a Virtual Machine (VM Ware) would be the way to go but I don't have the room for XP and the other programs on the current 40 GB drive.

Wondering what the best way to set things up is ? Should the drives be set up as RAID (no idea how to do that...only read about it a bit). Or is there a better way. I'm estimating 80 GB to maybe 90 GB is what I'd need. I could get by with 80 GB if needed  but would like more if it's not too complicated to set up.

Sorry for the long question.

---

### Post by QIII on 2010-09-25
Assuming you don't want to mess with your current installation of Ubuntu on that original drive, you can put your .vdis for VirtualBox on any drive.  I have a drive in my machine that is entirely dedicated to .vdis.

It is actually preferable to put your virtual drives on a different physical drive from your host to avoid competition for read/write on the host drive.

You'll have to either mount the drive manually or make sure it is mounted at start up.

---

### Post by ericstrom on 2010-09-25
Thanks for the comments. May I ask you a few other questions:

How would I have the second drive mount automatically ?

The last time I tried something like that, the second drive ended up under the root and for some reason, the root only had 40 GB capacity (which was close to capacity). So adding the second drive just filled the root to capacity.

Would I download and set up VM first and then somehow load Win XP of the CD ?

Sorry for the simplistic questions.

---

### Post by Elfy on 2010-09-25
Add it to fstab - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You'll need somewhere for it to mount - if you put the mount in /media it will show on the desktop (unless you've turned that off anyway) - I mount my drive(s) in /mnt so they don't show.

I have a couple of partitions mounting at boot - here's the fstab lines I use for them

#Media drive
UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/sysmedia ext4 defaults 0 2

#Spare Drive
UUID=3549d0ba-dc4d-4ef0-b3ed-417e53a71e1d /mnt/spare ext4 defaults 0 2

---

### Post by ericstrom on 2010-09-25
Right now GParted shows the 2nd drive (sdb) file system type as extended / unallocated. Do I need to assign a file system type to the drive with GParted before I set up the automatic mount ?

---

### Post by Elfy on 2010-09-25
I would

---

### Post by ericstrom on 2010-09-25
Sorry for all the questions forestpiskie. But I'm almost there. 

Thinking of using the following line since I can't find the UUID:

/dev/sdb1 /mnt ntfs-3g defaults,locale=en_US.utf8 0 0

Would that work ?

Exactly how do I add this line ?

---

### Post by Elfy on 2010-09-25
I'd not use /dev/sdb1. If the drive was not plugged in - or another was plugged in beforehand sdb1 would be a different drive.

Use UUID's - plug in the drive that you need to have mounted and run 

```
sudo blkid -c /dev/null
```
It's a long time since I added an ntfs drive - but when I did I got the syntax from a thread by bodhi.zazen - that is now copied to the fstab wiki page I linked earlier.

I would also mount it into a folder

so make the folder 

```
sudo mkdir /mnt/nameyouwant
```

then in fstab 

```
UUID=incomprehensiblenumber /mnt/nameyouwant ntfs-3g defaults,locale=en_US.utf8 0 0
```

Those being the options in the fstab page.

Please make a backup of fstab before you start if you have not alreaady done so 

```
sudo cp /etc/fstab /etc/fstab.bak
```

---

