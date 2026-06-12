---
title: "can't mount all ntfs HDs simultaneously (new machine)"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by alayoyo on 2010-11-01
**Hello**. I recently built a new box, and am having trouble seeing all of the HDs. Since i was working on getting the mobo, boot drive, etc working, i'm not quite sure of initially how this problem started.   

**background**: my old computer was dying, i think it was a motherboard/psu problem. I hadn't noticed any disk file system errors.  

I installed ubuntu 10.10 (10.04 live usb, then did updates to 10.10). I have most things working & imported from my last computer, the problem is related to hard drives i am trying to install from my old computer: four sata drives, 3 are NTFS with media on them. I currently cannot mount one of them.  

**Currently**:
Using gparted and ubuntu disk utility, i see: 
sda - NTFS; "samsung" (to name the physical drive) 
sdb - NTFS; "st3" 
sdc - NTFS; "maxtor" 
sdd - xt4, extended, swap; "WDC" (this i formatted to do the ubuntu install/booting)  

Last time i booted, the "samsung" drive wouldn't mount. I was moving some things around and hoped a reboot would fix things. This boot, "ST3" doesn't mount (doesn't show up in Menu>Places>Computer). I looked in Disk Utility, and st3 shows up there; disconcertingly, when i look in gparted, there is an error message:
[see screenshot1, i don't know how to copy this or replicate via command line]

when i try to mount the drive in ubuntu disk utility, i get this error message:
```
Error mounting volume
Details:
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdd1 is already mounted on /
mount failed
```I probably would spend longer fiddling with settings, but i don't want to risk data corruption since some of the larger drives have tv shows/film i don't have room to backup (though important records are backedup). I could not find anything directly on point i felt comfortable doing. Thanks for the help. 
[B]
my skill level[/B]:i would say i'm generally competent with computer hardware, scripts, etc. but i have limited experience with linux, mostly used windows in the past. I installed openSUSE to a laptop once. I know very little wrt linux-specific commands.

---

### Post by oldfred on 2010-11-01
If you have a mount in fstab to media or /home, it will also show a second mount on the left side panel. If you click on the second one it will say it is already mounted.

Many times Ubuntu or gparted will not mount NTFS partitions that need chkdsk or have been hibernated. This is to protect the drive as chkdsk should be able to repair it, but if you start writing to it, then chkdsk may not be able to repair it.

I would use a windows disk CD/DVD and run chkdsk on the NTFS partitions.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by alayoyo on 2010-11-17
Thanks for the reply; I spent some time looking but I found it easier to scrounge up the space to backup my files, format to ext4, and repopulate my drive than to find a windows disc.I did figure out that the problem with one of the drives was a broken SATA cable, which was complicating things. For some reason ubuntu 10.04 liveusb boot was able to view the corrupted NTFS drive while the boot from installed 10.10 was not.

---

