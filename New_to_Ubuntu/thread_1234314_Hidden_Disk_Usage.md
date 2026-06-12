---
title: "Hidden Disk Usage?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by brtomkin on 2009-08-07
I am trying to clean up my home directory and remove a bunch of files, mostly pictures and videos.  I have pretty much deleted or moved everything to an external hard drive.  I have brought my disk usage down from about 280 GB to around 500 MB (300 GB capacity).  The disk usage analyzer agrees with this.  However, if I run GParted, it shows that there is still around 6 GB of disk usage.  I was wondering what would cause this discrepancy.

---

### Post by synapsys on 2009-08-07
Gparted is showing you how much of your partition is being used. If you only have one partition (home and root together) then 6gb sounds about right for a standard ubuntu installation.

---

### Post by brtomkin on 2009-08-07
It is one hard disk with 3 partitions as follows (from GParted):
root: /dev/sda1 9.32 GB/4.99 GB used
home:  /dev/sda2 286.85 GB/**5.68 GB** used
swap:  /dev/sda2 1.92 GB

For the home directory/partition:
Disk Usage analyzer reports **289.6 MB** used
Nautilus reports **271.9 MB** used

---

### Post by Barrucadu on 2009-08-07
Did you clear your trash? It's possible Nautilus and the Disk Usage thingy ignore that. Failing that, try `du -sh ~/*` in a terminal and see what's eating the space (may take a while, if that amount of space is being used).

---

### Post by lavinog on 2009-08-07
have you tried df in the terminal?
```

df -h

```

I think gparted also includes the journal as used space.

---

### Post by brtomkin on 2009-08-07
Ok, I must've looked at the Disk Usage Analyzer wrong.  It reports 1.2 GB used for the entire partition, but the size of the home folder (the only folder on the partition) is only 289.6 MB... trash is empty.  Also, 'df-h' reports 1.2 GB usage for that partition.  The command `du -sh ~/*` looked to be close to the 289.6 MB number (I didn't do the arithmetic and add the results up).

So, now I have three disk usage numbers:
1.  289.6 MB is the total of the contents of all (hidden and non-hidden) folders on the partition
2.  Disk Usage Analyzer and 'df -h' reports 1.2 GB usage
3.  Gparted reports 5.68 GB usage

Right now I have booted a live cd to run fsck on that partition to see if it checks out ok.  I used the following command:

sudo fsck -C -y -t ext3 /dev/sda2

It is taking a long time though.  The progress bar went to around 20% pretty quickly, but now it seems to have slowed/stalled (ok, it is still ticking up, but really slowly) - maybe I have disk errors?

---

### Post by asmoore82 on 2009-08-08
I think the disk usage analyzer is easily fooled by links, shortcuts, and subfolder mountpoints.
GParted may be picking up on the space that is reserved for root use,
you can tweak this value with the `tune2fs` command.

---

### Post by lavinog on 2009-08-09
try this:
```

sudo du -hx --max-depth\=1 /home/

```
the -x makes it stay on one filesystem
I am wondering if you have something in /home/lost+found

---

