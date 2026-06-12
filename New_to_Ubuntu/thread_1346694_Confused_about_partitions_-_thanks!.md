---
title: "Confused about partitions - thanks!"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-05
Hi - I am trying to dual boot windows 7 and the latest ubuntu so that they can share the same folders.

Firstly, I am trying to shrink the already installed windows partitions. However I have got stuck....I have three partitions....is that normal?

1. Recovery Partition - Capacity 1.46 GB Free Space 1.46GB 100% Free 
2. Data D: - Primary Partition - Capacity 73.36 GB Free Space 73.27 100 Free
3. Vista C: - System, Boot, Page File. Active, Crash Dump, Primary Partition - Capacity 74.22 Free Space 54.49 Free 73%

----

I installed W7 over Vista - or at least I thought I did....can I simply delete Vista C: (as per my list 3)?

Also, why do I have three partitions - I thought I was only meant to have 2 - and simply I would shrink the largest partition allowing room for ubutnu....

Any advice much appreciated!!!

Thanks!

---

### Post by lindsay7 on 2009-12-05
See this. look at Ranch Hands post. it may give you some help.


[http://ubuntuforums.org/showthread.php?t=1346361](http://ubuntuforums.org/showthread.php?t=1346361)

---

### Post by raymondh on 2009-12-05
> **listerdl said:**
> Hi - I am trying to dual boot windows 7 and the latest ubuntu so that they can share the same folders.

Firstly, I am trying to shrink the already installed windows partitions. However I have got stuck....I have three partitions....is that normal?

1. Recovery Partition - Capacity 1.46 GB Free Space 1.46GB 100% Free 
2. Data D: - Primary Partition - Capacity 73.36 GB Free Space 73.27 100 Free
3. Vista C: - System, Boot, Page File. Active, Crash Dump, Primary Partition - Capacity 74.22 Free Space 54.49 Free 73%

----

I installed W7 over Vista - or at least I thought I did....can I simply delete Vista C: (as per my list 3)?

[COLOR="Red"]Did you upgrade Vista to win7 or did you do a fresh install? Are you able to boot into win7 automatically or, do you have a dual-boot scenario with win7 + Vista?  If you only have win7 and plan to dual-boot with ubuntu so that "they share the same folders" ..... why not just shrink the existing win (C: drive) to give space to Ubuntu.  The data partition (D:drive) can be such ... data storage for both OS.  However, if you have Vista or are dual-booting Vista + win7, a re-do of the win7 might be the easier way to go[/COLOR]. 

Also, why do I have three partitions - I thought I was only meant to have 2 - and simply I would shrink the largest partition allowing room for ubutnu....

[COLOR="Red"]I don't know your install process.  By default, win7 creates 2 partitions (boot and system) unless you specifically install on a existing partition.  Nevertheless, if D is indeed a storage and in NTFS, you can use it as such for both OS' to read and write to.  Where to get space for Ubuntu is your choice (either from C drive or D drive. If you decide to do it manually, make sure that space is an extended partition and Ubuntu root and swap are logical partitions inside said extended.[/COLOR]  


Any advice much appreciated!!!

Thanks!

Regards,

---

### Post by Paqman on 2009-12-05
Your "Vista" partition is actually your Win7 partition. Having a recovery partition is normal on Windows systems.

---

### Post by mrbiggbrain on 2009-12-05
The extra partition should be 100mb, this partition actually holds the windows boot loader, and recovery tools. By having the windows boot loader on a different partition then windows 7 the entire windows 7 partition can be encrypted using bit locker. However this partition also includes a complete "untaintable" recovery environment. This means that viruses, malware, or even partition problems with the main partition cant cause issues with the recovery environment.

99% of installs will likely have this option turned on, and it may be used for more things down the line but thats the current use. Note that this partition is 100% needed.

---

