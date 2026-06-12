---
title: "[SOLVED] Ubuntu cannot mount flash drives?..."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-04
So when ever I have my flash drive plugged into a windows system and remove it with out "safely" removing it and then plug it into my ubuntu it cannot mount it... is there any way around this? Because I do not personally own a system that runs Windows... so it is more than a little annoying having to wait till I get back to work or my parents house to be able to use my flash drive again...

~Jeff

---

### Post by HotShotDJ on 2009-01-04
> **beastrace91 said:**
> So when ever I have my flash drive plugged into a windows system and remove it with out "safely" removing it and then plug it into my ubuntu it cannot mount it... is there any way around this? Because I do not personally own a system that runs Windows... so it is more than a little annoying having to wait till I get back to work or my parents house to be able to use my flash drive againIf it works when you safely remove it, then, the obvious answer is -- safely remove it each and every time.  Then you won't run into this problem.

---

### Post by beastrace91 on 2009-01-04
> **HotShotDJ said:**
> If it works when you safely remove it, then, the obvious answer is -- safely remove it each and every time.  Then you won't run into this problem.

The issue is when I give my flash drive to other people to use and then get back home to find out they did not in fact safely remove it... Thanks for the stupid comment though that did nothing to help with my issue.

~Jeff

---

### Post by lykwydchykyn on 2009-01-04
What filesystem is on the flash drive?  FAT or NTFS?

---

### Post by beastrace91 on 2009-01-04
It is an NTFS but I would like to be able to force mount both types.

~Jeff

---

### Post by Tatty on 2009-01-04
> **beastrace91 said:**
> The issue is when I give my flash drive to other people to use and then get back home to find out they did not in fact safely remove it... Thanks for the stupid comment though that did nothing to help with my issue.

~Jeff

It may not have answered your question but I wouldnt have said that was a stuid comment, removing a flash stick without unmounting it first can result in destroying some or all of the data on the stick.

See this thread to force mount your stick.  [http://ubuntuforums.org/showthread.php?t=747509](http://ubuntuforums.org/showthread.php?t=747509)

Be careful though, force mounting it without safely removing it from a windows machine first can corrupt data.

---

### Post by handydan918 on 2009-01-04
> **beastrace91 said:**
> So when ever I have my flash drive plugged into a windows system and remove it with out "safely" removing it and then plug it into my ubuntu it cannot mount it... is there any way around this? Because I do not personally own a system that runs Windows... so it is more than a little annoying having to wait till I get back to work or my parents house to be able to use my flash drive again...

~Jeff

Easiest answer, besides safely removing, is to format the stick to ext3....

---

### Post by beastrace91 on 2009-01-05
Formatting it to ext3 will let me plug/unplug it on windows with out having issues on Ubuntu later?... any other draw back to formatting it like this?

~Jeff

---

### Post by lykwydchykyn on 2009-01-05
I don't think you should have a problem with FAT.  The problem is generally only with NTFS; when it gets "unsafely removed" a flag is set on the partition saying that it's dirty, and you can't mount it (for safety reasons) until that flag is cleared.

To clear the flag:
 - Plug it into your ubuntu (or other Linux) system
 - Determine what the name of the device is.  "sudo fdisk -L" is usually a good method, or you can look at syslog or something.  maybe there's a gui tool for this, anyone?
 - Once you know that, the magic words are:
```

sudo ntfsfix /dev/sdb1

```
(assuming the partition is sdb1).

That should allow you to mount the drive.  Have you had this problem with FAT partitions?  I don't think they have a dirty flag.

---

### Post by beastrace91 on 2009-01-05
I will format one of my drives to FAT and see what it does (normally I just use NTFS) thank you for the command to clear the "dirty flag" though that is exactly what I am looking for. I will test it as soon as I get home :)

~Jeff

---

### Post by dadozgb on 2009-01-05
> **beastrace91 said:**
> So when ever I have my flash drive plugged into a windows system and remove it with out "safely" removing it and then plug it into my ubuntu it cannot mount it... is there any way around this? Because I do not personally own a system that runs Windows... so it is more than a little annoying having to wait till I get back to work or my parents house to be able to use my flash drive again...

~Jeff

There is no way to get "around this". To use some file system you have to mount it. To mount it you have to have permission to do so. So look at users and groups config and give yourself permisson to mount such device.

---

