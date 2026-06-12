---
title: "My ext4 partition is having some problems"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by adeklipse on 2011-06-25
I'm sorry for the ambiguous title, but I couldn't figure out how else to describe my situation.

Around 2 days ago, I was playing around with a live session of MeeGo. Impressed, I decided to install it. On the installation dialog, I shrank a part of my /home partition (for Ubuntu) to make way for around 8GB for MeeGo. When it process was completed, it resulted in an error, which I (stupidly :() ignored. The installation aborted from that point, and I did not try again.

Then I booted into my Ubuntu (11.04). It ran an fsck since it was plugged in. While doing so, it encountered an error on my /dev/sda7 partition (I'll try to take a picture of it if I manage to; I don't want to log out of my live session of Ubuntu 10.10 that I'm running now). 
It had options to fix, skip or ignore; I pressed "f" to tell it to attempt to fix it. It did not work. It successfully booted to the display manager, but once I try to log in, it said something about unable to update the .ICEAuthority, or something. That was when I realized my /home partition (on /dev/sda7) did not mount.

Desperate, I booted to an Ubuntu 10.10 live session (as that was the only one I had) to fix it. I read some threads and posts in forums, and evetually ran these:
```
sudo fsck.ext4 /dev/sda7
sudo mke2fs -n /dev/sda7
sudo e2fsck -b 20480000 /dev/sda7
```
I restarted, the same error messages popped up on Plymouth, and /dev/sda7 could not be mounted again.

Then I search some more, and ran:
```
sudo mke2fs -S /dev/sda7
sudo fsck /dev/sda7
```
It prompted if I wanted to continue/fix, and, out of desperation, I pressed "y". It continued to give me prompts. I held "y" for half an hour, before I fell sleepy and decided to put a small stone on the "y" key.

When I woke up, it was still prompting. I decided to Ctrl+C it (yes, I really am that much of an idiot), and decided to mount the partition using nautilus, and it resulted in "Error mounting: mount: Stale NFS file handle". I have no idea why Ubuntu thought my /home is an NTFS partition (since I formatted it to ext4).

Now, I need to recover the partition as a whole, but don't know what to do. I already have a backup of my data, but I really need my Ubuntu to be functional, since I'm 8% away from downloading a 35GiB torrent that I've been downloading for the past 2 weeks (I have a crippled internet connection).

Oh, and this is the output for fdisk:
```
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8ba0d59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14647296   83  Linux
/dev/sda4            1824       30401   229546689+   f  W95 Ext'd (LBA)
/dev/sda5           22068       30152    64942383    7  HPFS/NTFS
/dev/sda6           30153       30401     2000061   82  Linux swap / Solaris
/dev/sda7            1824       20947   153600000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1017 MB, 1017117696 bytes
32 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2a0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1017      992561+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

```
Any help would be greatly appreciated.

Sorry for the long post, but I thought I needed to describe how I got to this mess. Excuse my stupidity, too, I really am a beginner and I will be asking stupid questions with apparent obvious answers.
Let me know if there's any info missing.

Thanks in advance.

---

### Post by fabricator4 on 2011-06-26
> **adeklipse said:**
> 
Then I search some more, and ran:
```
sudo mke2fs -S /dev/sda7

```

My feeling is that this was a step too far.  From the mke2fs manual:

 ```
-S    Write superblock and group descriptors only.  This is useful  if
      all  of the superblock and backup superblocks are corrupted, and
      a **[SIZE="3"]last-ditch recovery method is desired[/SIZE]**.  It  causes  mke2fs  to
      reinitialize  the  superblock  and  group descriptors, while not
      touching the inode table and the block and inode  bitmaps.   The
      e2fsck  program  should  be run immediately after this option is
      used, and there is no guarantee that any data will  be  salvage&#8208;
      able.   [B][SIZE="3"]It  is critical to specify the correct filesystem block&#8208;
      size when using this option, or there is no chance of recovery.[/SIZE][/B]

```

Emphasis added by me.  I think what this is saying is that this should only be used as an absolute last ditch effort, because there's no recovery from this if it does not work. 

Unless someone come forward with a magic bullet, you might have to face the fact that your partition is completely scrambled.

This is why we always recommend that the partition(s) is backed up before any resize/move operations are done on it.  If something goes wrong during the process it is usually not trivial to figure out what that something is and change it back.

Chris.

---

### Post by adeklipse on 2011-06-26
> **fabricator4 said:**
> My feeling is that this was a step too far.  From the mke2fs manual:

 ```
-S    Write superblock and group descriptors only.  This is useful  if
      all  of the superblock and backup superblocks are corrupted, and
      a **[SIZE="3"]last-ditch recovery method is desired[/SIZE]**.  It  causes  mke2fs  to
      reinitialize  the  superblock  and  group descriptors, while not
      touching the inode table and the block and inode  bitmaps.   The
      e2fsck  program  should  be run immediately after this option is
      used, and there is no guarantee that any data will  be  salvage&#8208;
      able.   [B][SIZE="3"]It  is critical to specify the correct filesystem block&#8208;
      size when using this option, or there is no chance of recovery.[/SIZE][/B]

```

Emphasis added by me.  I think what this is saying is that this should only be used as an absolute last ditch effort, because there's no recovery from this if it does not work. 

Unless someone come forward with a magic bullet, you might have to face the fact that your partition is completely scrambled.

This is why we always recommend that the partition(s) is backed up before any resize/move operations are done on it.  If something goes wrong during the process it is usually not trivial to figure out what that something is and change it back.

Chris.

Well, that wasn't as dandy as I had hoped for. I did have a recent backup, though, so nothing too critical was lost. The thing that I regretted was that 35GiB torrent (the Ubuntu repo, to use in offline environments).

But no matter, thanks for the heads up.
Hopefully I won't be as ignorant later...
:)

---

### Post by fabricator4 on 2011-06-26
> **adeklipse said:**
> Well, that wasn't as dandy as I had hoped for. I did have a recent backup, though, so nothing too critical was lost. The thing that I regretted was that 35GiB torrent (the Ubuntu repo, to use in offline environments).

Hi, Yes well lessons learned I guess.  You really shouldn't run any CLI command unless you understand what it's going to do to your system, particularly if you're running it from a LiveCD or in conjunction with 'sudo'.

It's easy to find out - I just typed 'man mke2fs' and scrolled down to -S switch.  I'm sure if you'd read it first you wouldn't have run the command, at least not without asking some questions!

Chris.

---

### Post by adeklipse on 2011-06-27
> **fabricator4 said:**
> Hi, Yes well lessons learned I guess.  You really shouldn't run any CLI command unless you understand what it's going to do to your system, particularly if you're running it from a LiveCD or in conjunction with 'sudo'.
Yes, I do realize that I shouldn't really just type in and enter any command that people post out, but I was really desperate.

> **fabricator4 said:**
> It's easy to find out - I just typed 'man mke2fs' and scrolled down to -S switch.  I'm sure if you'd read it first you wouldn't have run the command, at least not without asking some questions!

Chris.

I did take a glimpse of the manpage for mke2fs (and other commands that I entered) before I entered them, but English isn't my first language (I guess that's apparent in my posts), so all those fancy and sophisticated words don't really mix in. In addition to that, I didn't really understand the manpage syntax (thankfully, I think I have the general idea now), so it was hard for me to distinguish which options are for which variable; I'm not so much a Linux poweruser, I just do it for Inkscape and GIMP and a bit of freedom now and again. :D

Thanks for your help and heads up, though! :)

Hari.

---

