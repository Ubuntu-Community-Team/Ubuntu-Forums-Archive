---
title: "Unable to access media files on windows hard drive."
date: 2011-03-15
forum: New to Ubuntu
---

### Post by mevans-9000 on 2011-03-15
Hi there, I installed Maverick using Wubi the other day after several years of vista (I won't go into how impressed I am with it) so at the moment I'm quite the novice. I seem to have everything running as I would like it to but the only (rather large) problem is that I cannot access my media files that were on my windows file system. I have never partitioned my hard drive, any partitions are default.

Here is my current HDD setup:

Total ~250GB partitioned into
~10GB HP_TOOLS (stock partition)
~10GB HP_RECOVERY (another stock one)
~230GB Windows OS files, all my media and documents + 30GB Ubuntu 10.10 partition made by Wubi.

All I can see in my places menu are the HP_TOOLS, HP_RECOVERY (after installing ntfs config) and my Ubuntu file system.

Ideally, I would like to be able to read and write my media from Ubuntu 10.10, so until I can afford an external HD/new laptop I can play my music and films. I know I could format the disk and reinstall everything, but at the moment I do not have a copy of a windows OS, an external to backup my music and films (~100GB) so please, if there are any fixes for this issue, your help will have my eternal gratitude.

---

### Post by Morbius1 on 2011-03-15
I know nothing of Wubi but I believe your Windows host partition is automatically mounted at:
```
/host
```

---

### Post by mevans-9000 on 2011-03-15
Wow, that really was a rather simple solution...

You sir, have earned my eternal thanks...

---

