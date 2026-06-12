---
title: "removing windows"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by geomcewan on 2009-02-28
I am at present running a dual boot system with windows 2000. I wish to remove windows leaving only Ubuntu as my only OS.
Can this be done without formatting/ re installing?
Both systems at present are on my C drive, with all data, pics, mp3's etc on my D drive.
I wish to do this without touching drive D.
Is there a button called "kill windows" that I can click?
Thanks in advance for any help:P

---

### Post by smani on 2009-02-28
Did you install via wubi? Otherwise Ubuntu should be independent from windows.

---

### Post by Kareeser on 2009-02-28
I s'pose you could open GParted and delete the windows partition, then extend the ubuntu partition over... maybe.

---

### Post by geomcewan on 2009-02-28
I installed Ubuntu with a CD I downloaded. I'm not sure about deleting partitions in this OS, just wondered if there was a simpler solution.

---

### Post by arm-c on 2009-02-28
If you used the "Install Inside Windows" option, I don't know how to address that.  Given your discussion, it sounds like you did that.  Wubi is great to get a working install during try out periods when unsure of the system; however, for anyone wanting to switch for sure, I'd always recommend a normal instal.  Wubi does not use a typical Linux partition to work and I don't know if there is a utility to do the switch.  Try google "wubi linux move partition move" and see about it.  If it were me, I wold just start fresh.  I know it sounds like a lot of work, but you will learn and it is much simpler the 2nd/3rd time.  While linux is not as bad a windows (where win needs new install periodically to clean out the gunk that slows all down, get rid of accidental spyware, etc...) doing a fresh install is good.  Time your move to fresh install when you upgrade to next version of ubuntu.  That is perfect time to start fresh and when I did mine.  Many people HIGHLY recommend that instead of the upgrade of previous install method -- but you will also note that they ususally always have their /home directory on a separate partition.  That is so it won't be wipped in the process and during install, they tell the installer to mount that partition as their "/home" directory.  Thus after the install and putting all of their additional software from repositories in, all their settings / customization is still in place.  Amazingly fast...  In mean time, read about partitions and creating separate home partition.

In preparation for an upgrade, if you had to customize any files from the /etc directory, I recommend you back that up or ensure you know what you did for new install.

>> Summary:  Reinstall fresh on next upgrade (APR).  Take some time to create a separate partition for your home directory (Ext 3 format recommended as I don't think a NTFS or FAT32 partition can be mounted in this manner - dangerous regardless).  Do the labor then.

If, however, you installed to a new partition, you should just have to use partition editor to delete the partition (which I would use for a dedicated /home partition and then move all of contents from current /home to that new partition, remove the old contents of /home and mount the new partition as /home -- LOOK FOR DETAILED INSTRUCTIONS AS THIS COULD BE TEDIOUS AND CAUSE YOU PROBLEMS IF NOT DONE CORRECTLY.  But I did fine when I did it and it was first time and I learned a lot.

If you just want to use it as a data space, it should mount under your /media when you mount it.

Happy 'buntuing

---

### Post by oldos2er on 2009-02-28
Open a terminal and post the output of this command:

 sudo fdisk -l

---

### Post by Elfy on 2009-02-28
If you installed wubi - that is ubuntu installed from inside windows - it would have a folder in C:\ and available in Add/Remove  then you can migrate the virtual harddrive to a new partition and then remove the windows partitions

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I migrate to a real partition, and/or get rid of Windows entirely?

If you installed ubuntu completely seperately from windows then you can delete the partition from inside ubuntu and create a new partition.

Posting 

```
sudo fdisk -l
``` will help

---

