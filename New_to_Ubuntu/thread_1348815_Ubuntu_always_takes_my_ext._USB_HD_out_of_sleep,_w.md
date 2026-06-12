---
title: "Ubuntu always takes my ext. USB HD out of sleep, why?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by ProDigit on 2009-12-07
every so many minutes I note that my ext.USB hd gets out of sleep by (X)Ubuntu!
I really dislike that!
It wears down the HD!

Can I disable that?

I only want the HD to spinup when I'm actually accessing it, and the computer needs data from it that it doesn't already have (eg: When I play an MP3 file, many media players load the file to RAM, so they don't continuously need to access the disk).

---

### Post by adaucourt on 2009-12-07
> **ProDigit said:**
> every so many minutes I note that my ext.USB hd gets out of sleep by (X)Ubuntu!
I really dislike that!
It wears down the HD!

Can I disable that?

I only want the HD to spinup when I'm actually accessing it, and the computer needs data from it that it doesn't already have (eg: When I play an MP3 file, many media players load the file to RAM, so they don't continuously need to access the disk).

You can try checking your preferences in power management (spin down hard disks when possible).  Worth a try.

---

### Post by ProDigit on 2009-12-07
> **adaucourt said:**
> You can try checking your preferences in power management (spin down hard disks when possible).  Worth a try.

In Xubuntu powermanagement there is no hard disk settings displayed, only the computer (turning it off) and monitor.

---

### Post by Landslide on 2009-12-07
If you're using a journaling file system on that drive, you might consider switching to ext2, as it is not journaled and performs fewer writes.

[http://en.wikipedia.org/wiki/Ext2]("http://http://en.wikipedia.org/wiki/Ext2")

---

### Post by ProDigit on 2009-12-07
> **Landslide said:**
> If you're using a journaling file system on that drive, you might consider switching to ext2, as it is not journaled and performs fewer writes.

[http://en.wikipedia.org/wiki/Ext2]("http://http://en.wikipedia.org/wiki/Ext2")

It's a 1TB NTFS drive, I used NTFS, because I could compress the data to get more on it. On average the compression ratio is rather small (less than 2% compression, in other words it holds about 1,01TB of data.
It's 95% full, so I don't want to risk converting it...

I suspect that xubuntu tries to ping the HD every so many minutes, getting it out of sleep; because there is not supposed to be any disk activity going on....

---

### Post by Sir Jasper on 2009-12-07
Hi,

If it shows in fstab, you could try

sudo gedit /etc/fstab

and put a hash sign, #, at the start of the drive/partition line
then save.

Then Just delete the # if it doesn´t work.

My regards

---

### Post by adaucourt on 2009-12-11
> **ProDigit said:**
> every so many minutes I note that my ext.USB hd gets out of sleep by (X)Ubuntu!
I really dislike that!
It wears down the HD!

Can I disable that?

I only want the HD to spinup when I'm actually accessing it, and the computer needs data from it that it doesn't already have (eg: When I play an MP3 file, many media players load the file to RAM, so they don't continuously need to access the disk).

command line utility to set hard disk parameters (including harddrive sleep times)

Usage:  hdparm  [options] [device] ..
 -S   set standby (spindown) timeout
```
hdparm -S 5 /dev/hda
```

Hope this helps... sorry it took so long!

---

### Post by aaale on 2010-02-15
Have same issue here using ubuntu 9.10 and 2x1TB USB disk ext3 formatted.
In 8.04 this problem never happened.

Is there a way to see who or what process is accessing to disks and waking them up? :icon_frown:

---

