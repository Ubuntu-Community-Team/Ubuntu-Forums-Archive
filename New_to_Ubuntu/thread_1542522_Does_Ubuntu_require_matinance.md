---
title: "Does Ubuntu require matinance?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Pikzilla on 2010-07-30
I've had an Ubuntu Machine running for quite some time, and have noticed that the system is gradually getting slower, and suffers frequent graphics crashes. Are any kind of system upkeep utilities required for Ubuntu, the same way you need to perform frequent hard drive defragmentations, virus scans, and system cleanups on windows?

---

### Post by _h_ on 2010-07-30
You could try BleachBit, which would clean up your filesystem of alot of junk.

---

### Post by mbsullivan on 2010-07-30
> I've had an Ubuntu Machine running for quite some time, and have noticed that the system is gradually getting slower, and suffers frequent graphics crashes. Are any kind of system upkeep utilities required for Ubuntu, the same way you need to perform frequent hard drive defragmentations, virus scans, and system cleanups on windows?

Yes and no... Of course, over time your system will accrue junk -- log files will grow to unmanageable sizes, you'll accumulate a long list of kernel revisions in /boot, you may install thousands more packages than when you fresh installed. However, defragmenting is not typically necessary, nor is there a constant threat of viruses and malware.

Cleaning out your harddrive, while a good idea, will probably not make your system snappier or more stable. Keeping up-to-date (or perhaps reverting back to older versions) is the best way to ensure stable operation, and it pretty much has to be handled one issue at a time. 

Also, how's your memory usage? Linux is very good at utilizing large amounts of RAM, and makes use of your unused RAM (in addition to the memory storing programs and data) as a sort of file cache, to speed up repeated file accesses. If you have slowly accumulated more stuff that must be running, filling up more memory, then there's less "cache" room to go around. Therefore, using more memory could potentially make the system feel more sluggish. Definitely, if you're almost full and need to swap memory to disk, things are gonna crawl!

What's the output of:

```
free -m
```

???
Mike

---

### Post by Pikzilla on 2010-07-30
Here:
 
            total       used       free     shared    buffers     cached
Mem:          3014        729       2285          0         37        350
-/+ buffers/cache:        341       2673
Swap:         8832          0       8832

Also, could you give an explanation as to why my system will often and without warning go into low-graphics mode with no way to get back to the GUI?

---

### Post by jerenept on 2010-07-30
What graphics card are you using?

This may help with the low-graphics issue.

---

### Post by mbsullivan on 2010-07-30
Your memory looks fine! That's certainly not an issue at this point.

Mike

---

### Post by Pikzilla on 2010-07-30
My graphics card is Intel Corporation 82915G Integrated Graphics Control

---

### Post by sandyd on 2010-07-30
> **Pikzilla said:**
> My graphics card is Intel Corporation 82915G Integrated Graphics Control
xorg-updates ppa has got some new drivers for ur card.
add [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)
update, and see if it speeds up.

and don't even try using X-Crack unless your prepared to break your system.

---

### Post by k3lt01 on 2010-07-30
[Take a look at this thread in the forum]("http://ubuntuforums.org/showthread.php?t=140920"), it will help you to clean up a certain amount of junk that could be causing an unnecessary burden on your system.

---

### Post by soldier1st on 2010-08-03
the only maintenence is to keep the latest 2 kernels(1 as current and 1 for backup so if you have say 6 delete the last 4 and keep the 2 with the newest date) defrag is not needed and cleaning the rest is not needed unless your HDD is very small, also do not install prereleased or unsupported updates as those can break your system and for software only get it from either synaptic or the software center and if you need something badly that is not in either synaptic or software center you could add a ppa to your sources but make sure it is compatible with your architecture/version of Ubuntu/Linux  and go for the stable ppas as the rest could be buggy and in synaptic go into preferences/files and check the box that says delete downloaded packages after installation and the first time you go into that setting make sure to delete cached package files(only needs to be run once) and make sure not to remove any of the default ubuntu applications as ubuntu needs them but if your not gonna use them but something else just hide them.

---

### Post by Keen101 on 2010-08-03
If you've been installing and uninstalling random packages from the repos, then yes those could build up over time and slow your system down.

I myself periodically do the following to clean my system up.

1. run "sudo apt-get autoremove"
2. run "sudo apt-get autoclean"
3. Go into synaptic package manager, and click "status" on the bottom left hand column, and then click on "not installed residual config"... Then i select all those packages that are no longer installed, but taking up space, and select "mark for complete removal", and i click apply.

That seems to keep my system running pretty good. :)

---

