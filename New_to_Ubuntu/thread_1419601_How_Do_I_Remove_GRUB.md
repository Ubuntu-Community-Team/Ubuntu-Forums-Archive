---
title: "How Do I Remove GRUB?"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by carl_76 on 2010-03-02
Hi.

Removing grub may not be the solution but not knowing more about it that's all I can think of.  Here's the situation:

I've been running 9.04 64 and 9.10 64 on my AMD64 laptop for a while.  I'd like to reinstall windows and then 9.04 again in a dual boot configuration.  I ran the restore discs for the laptop but when it tried to reboot for the first time I got the following error:

unrecognized file system
grub recovery>

I'd appreciate any suggestions of how to either replace grub with the orignal boot loader, or get grub to recognize and start windows.  Or, any other suggestions.

Thanks.

Carl

---

### Post by victor.zamanian on 2010-03-02
I believe this thread might be of interest in this situation:
[http://ubuntuforums.org/showthread.php?t=1419459](http://ubuntuforums.org/showthread.php?t=1419459)

---

### Post by carl_76 on 2010-03-02
I think that situation is a little different from mine because the individual has a windows install disc that will overwrite the MBR.  I have a set of restore discs that in theory should put an image of the original install onto the disc but it doesn't appear to overwrite the MBR with the windows boot loader.  If I formatted the disc would that clear the MBR for the image discs?  Obviously I'm not quite sure how it all works but I'm pretty sure there's a difference between the restore discs and an install disc.

Oh, I just remembered that I had a copy of windows xp that I can't activate.  But, I thought if I ran through the installation it would overwrite the MBR with the windows bootloader and I could move on from there.  Instead I got the blue screen very early in the install process.

---

### Post by jimmy the saint on 2010-03-02
I assume you backed up your data since you are re-imaging the drive with the restore cds.  Yes?  Good.

Wipe the drive completely.  I like Dban, but you can also use the ubuntu live cd and 0 out the drive.

[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

Then try the restore disks again.  Then pop in the Live CD again and install Ubuntu.  Ubuntu will replace the MS boot loader with Grub and you should be good to go.  I have no idea why the restore disks are leaving the grub system behind.  A guess would be that it leaves the first partition alone in case it is a restore partition created by many laptop manufacturers.  Windows is finicky about where it is installed on the drive, so that may be why you are running into issues.  

You may want to try simply installing Ubuntu before you try anyting else, as a simple Grub installation might be all you need.  If that fails, though, I am pretty sure wiping the drive and starting from scratch will work beautifully.

---

### Post by carl_76 on 2010-03-04
Thanks.  Writing zeros to the harddrive allowed me to reinstall windows from the restore discs.  I really appreciate the help.

Carl

---

