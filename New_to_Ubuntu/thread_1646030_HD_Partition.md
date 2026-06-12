---
title: "HD Partition"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by stktek on 2010-12-15
Running Ubuntu 10.04
AMD Athlon 3200 sempron
1G RAM
1T HD
I have been running this system for 4 months with no major issue as I had with XP. I loaded Ubuntu on to a brand new 1T HD with out partition. I find that the system is running a bite slow and was wondering if I partitioned the HD would this help and if so how would I do this with out doing a complete reinstall.
I will be upgrading the cpu and ram when i can find a better AMD Athlon 64 x2 am2 cpu.

---

### Post by lindsay7 on 2010-12-15
find and read the tutorial on GParted.

---

### Post by stktek on 2010-12-15
Here is what I got what would be the best setting.

---

### Post by srs5694 on 2010-12-15
First, your disk *is* partitioned.

Second, what type of disk is it? Certain models, particularly from Western Digital, use a new "Advanced Format" design with 4096-byte sectors. These drives require [special care with partitioning.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) Given your posted screen shot, I suspect your disk is already partitioned in this way, but I can't be positive. If you think you might have such a disk, please post the output of "sudo fdisk -lu" between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings.

Third, are you saying that Ubuntu is slow, that Windows XP (on another disk?) is slow, or that something else is slow? How are you judging the system's speed? For instance, if Ubuntu is slow compared to XP, it could be you're seeing OS-to-OS differences. If dragging windows around on the screen is slow, that's likely a video driver or X issue, not a disk partitioning issue. Please be more precise in your description of what's slow.

---

### Post by stktek on 2010-12-15
I just notice that when opening a window it takes 5 seconds as when i was running xp it was faster. Also when i open firefox it takes about 15-20 seconds before it opens and loads and is ready to use.
Might need some tweaks but I am no computer wiz.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a3a66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1947510783   973754368   83  Linux
/dev/sda2      1947512830  1953523711     3005441    5  Extended
/dev/sda5      1947512832  1953523711     3005440   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a11baa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   42  SFS

---

### Post by srs5694 on 2010-12-15
Your /dev/sda is properly aligned, and /dev/sdb is Windows-only, so it's likely not an issue.

There are so many variables between the two OS installations that it's impossible to identify the cause of the speed difference at this point. A few possibilities that come to mind include:


[list]
[*]The Windows installation might be better optimized (speedup utilities, etc.).
[*]/dev/sda could be a slower hard disk than /dev/sdb.
[*]There could be video driver problems in your Linux installation.
[*]Linux might not be detecting/using all the RAM, and therefore might be swapping unnecessarily.
[*]Some unknown process or processes might be running under Linux, slowing it down.
[*]You might be using inherently slower Linux applications than the Windows ones you're comparing them to. (This is particularly likely if you're comparing entirely different programs or if you're comparing modern programs under Linux to older programs on Windows, since programs tend to accumulate bloat over the years, under any platform.)
[*]It could *seem* slower under Linux but not be so in fact, since our perceptions of time can be influenced by a lot of extraneous things. You could time operations with a stopwatch to get objective measures.
[/list]


Since most of these issues aren't related to hard disks, I recommend you start a new thread with a more descriptive title, like "Ubuntu seems slow; want optimization suggestions". Describe the issues in as much detail as possible, and include the output of the following commands, typed after the computer has been idle (no big programs running) for at least a couple of minutes:

```

free -m
uptime
df -h
cat /etc/mtab

```

Please do as I asked (and you didn't do) with this output: Post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This will improve legibility.

Also, attach the /var/log/Xorg.0.log file to the new thread.

With that information, it's likely that somebody will be able to suggest some optimizations. You may also be asked to run additional tests.

---

### Post by sandyd on 2010-12-15
Whats the brand of the HD, and what is the RPM?
7200+ rpm w 16mb+ cache should not be slow.

---

