---
title: "Stuck on Verifying DMI Pool Data"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by plaine on 2009-09-26
I'm brand new to Ubuntu and trying to get the Ubuntu 9.04 Server Edition setup on a brand new machine.  After installation, my system just hangs on "Verifying DMI Pool Data.....".   I left it there for about 20 minutes, so pretty sure its not impatience.  :)  

As mentioned, this is a brand new setup.  Ubunutu will be the only OS on the system and it has not had Windows or OS X or any other operating system on it, as all components were fresh out of the box and they include:

Gigabyte GA-EP45-UD3R (Rev 1.1) board
(4) 1TB Seagate SATA drives
4 GB of RAM

I was trying to set it up to be a RAID 5.  My main partition is 3TB. 

One thing I noticed, is that when I was going through, it hung on 33% partitioning for about a half hour, before continuing installation.  I'm not sure if that's typical or not, but I've seen a few threads on here to suggest various problems, none of which I had.  One also said to just be patient with RAID 5, so I did and eventually it succeeded, I believe.  

I've tried about everything I could find in the forums, but because I didn't have Windows installed originally, it seems like all the GRUB/DMI problems, I can't fix because I can't get to a Windows console and do 'fixmb' or various other things.

Can anyone give me any idea why this may be happening on fresh-out-of-the box components that never had an OS on before and how I might go about fixing this?  This is Ubuntu Server Edition 9.04.  I've tried re-installing 2 times now, but with no luck.  I tested my RAM and it had no errors.  It still just wants to hang at this spot after install and reboot.

Thank you

---

### Post by yeats on 2009-09-26
This may be a helpful thread:

[http://ubuntuforums.org/showthread.php?t=333829](http://ubuntuforums.org/showthread.php?t=333829)

---

### Post by plaine on 2009-09-26
Thanks.  I actually read that thread this morning which prompted me to flash my BIOS.  I  ended up updating it to the most current one.  That gave me a few fits in itself, but after I did, same problem.  Before this problem, I was getting past the DMI and on to GRUB, but then I'd get a GRUB Error 22.  Now, I'd love to get back to the grub error, as it would mean I'm past DMI, ha.  I haven't tried to take my CMOS battery out and reset it that way.  I'm certain its not dead, but I haven't removed it and removed hard drive cables and such.  However, it does recognize all 4 drives, so my guess is its not that.  So maybe I'll go try to remove the CMOS battery for a few minutes and then start it up again and see what happens.

As an update, I booted from Ubuntu CD just now, in Rescue mode.  When I was going through there trying to re-install GRUB, it was unable to find a boot partition (I forget the error, I should have written it down) and it gave me a fatal error.  No matter which partition I selected, it wouldn't work.  Does that give any clues or is that just another symptom of my DMI Pool error?

Frustrated, I'm currently trying to repartition.  Wiping out and starting from scratch.  Hey, maybe 3rd time is a charm now that I've updated the BIOS.  However, I can't seem to get it to remove the RAID software.  I had the RAID Multidisk setup with 2 MD devices.  I was able to remove one (the 3TB portion), but when I try to delete "md0_raid5" (the swap portion), I get a red screen that says "There was an error deleting the multidisk device. It may be in use".

Is there some way I can just wipe all 4 of those drives and start from ground zero?

Thanks.

---

### Post by bikemakr on 2011-01-18
Did you ever solve this? I have the same issue, but didn't partition.

---

