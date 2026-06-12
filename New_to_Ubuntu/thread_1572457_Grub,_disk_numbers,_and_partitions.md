---
title: "Grub, disk numbers, and partitions"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by necronom on 2010-09-11
Hi,

I installed Ubuntu 10.04.1 desktop AMD64 last night, and I have a few queries, if anyone can help.

A bit of background:

This is the first time I've installed Ubuntu at home, though I did install Red Hat about 10 years ago at work.

I've only used Linux for a total of about 10 hours, though I've used other OSs since the '80s (AmigaDOS/Workbench, DOS, Win 3.1 - XP).

I'm in IT support, so I know the general non-Linux stuff.

I used Unix for a few months about 10 years ago, though I've forgot most of it.

---

So, last night I deleted my blank disk's partition (disk 0 - my old ATA drive), backed up my MBRs, then installed Ubuntu from the CD.

I rebooted, and expected the boot menu to appear, but instead it booted into XP as usual.  I rebooted, and pressed F11 to get to my PC's boot menu, and chose the disk to boot from, it then booted from disk 0 and the Ubuntu Boot Menu appeared asking if I wanted to boot into Ubuntu, XP, etc.

So, my first questions are:

How do I get rid of Grub from disk 0 and onto my boot drive (disk 1)?

When it's on the right disk, can I set it to default to XP with a 2 second delay.  If I want Ubuntu, I'll choose it within the 2 seconds.

My disk 0 now has two partitions that Ubuntu made.  What are they, what format are they in, and what's on each?  At the moment I have no idea of the way things are organised.

When I tested Ubuntu from the Live CD, my Hard Disk light was flashing a lot, and it even tried to download drivers at one point during testing.  Where was it writing data to?  If the light was flashing it must have been doing something to one of my drives.  I would like to know what it did, where it did it, and if it left anything behind.

If this helps, [HERE]("http://homepage.ntlworld.com/paul.a.kitching/temp/Disks.png") is a pic of my partitions.

Thanks for any help you can give.

---

### Post by rolnics on 2010-09-11
Welcome back to linux.

Right your first question you need your livecd again boot up with that, from there you can install grub on whatever disk you want. The grub guide can be found [here]("http://http://ubuntuforums.org/showthread.php?t=1195275") you need to scroll down to section 13. But having a quick read you might want to provide some more details here first.

Run this command in terminal from ubuntu and post here. 
```
sudo fdisk -l
```

Right your other question about two partitions on disk 0. One is the /(root) partition including your /home partition and the second partition is the swap area. If you had installed with a separate /home you'd have three, some distro's go even further separating other parts of the install onto partitions. The partitions should be ext4, I think that's now the default for Ubuntu, the swap area can be anything really from ext2 upwards I believe.

As for the flashing hd light using the livecd, I'm not sure, I was thinking it might be using some kind of swap area, but then its not supposed to be touching your hd partitions, so I'm really not sure on that one.

---

### Post by TeoBigusGeekus on 2010-09-11
> How do I get rid of Grub from disk 0 and onto my boot drive (disk 1)?
Once in Ubuntu, mount every partition on your system, open a terminal and type:
```
sudo fdisk -l
```
that's -L not -1.
It will give you the partitions and the places where they are mounted. Let's say that the disk you want to install grub to is /dev/sdb. Open terminal and give:
```
sudo grub-install /dev/sdb
```

> When it's on the right disk, can I set it to default to XP with a 2 second delay. If I want Ubuntu, I'll choose it within the 2 seconds.
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

> My disk 0 now has two partitions that Ubuntu made. What are they, what format are they in, and what's on each? At the moment I have no idea of the way things are organised.
The fdisk command will give you info about every partition, but I think the two partitions are your swap space (something like pseudo memory, for when things get tough ram-wise) and your root partition (mount point:/). The root partition is where all things start - see attached image for more info.

> When I tested Ubuntu from the Live CD, my Hard Disk light was flashing a lot, and it even tried to download drivers at one point during testing. Where was it writing data to? If the light was flashing it must have been doing something to one of my drives. I would like to know what it did, where it did it, and if it left anything behind.
It probably used some free space from your drives as a temp location. I don't think it's left anything behind.

---

### Post by necronom on 2010-09-11
Thanks for the replies.  I've now got it all working as I wanted it.  I suppose I still have Grub on the other drive, but I don't expect that is a problem; it's just pointless being there.

I now have a wobbly sound problem, but I should probably do that as a new thread.

---

