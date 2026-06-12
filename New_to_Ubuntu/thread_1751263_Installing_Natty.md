---
title: "Installing Natty"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by jermza on 2011-05-06
I've not upgraded yet as I'm worried about a few things and need some advice.

I have two hard drives.  HD 1 has Ubuntu installed on it, and nothing else (other than, I suspect, software like GIMP etc, right?).  

HD 2 has all my photos, music, documents, etc. 

I can't remember how I did it initially, but I managed to re-map Ubuntu's Places menu to HD 2, so that Documents takes me to my documents folder on HD 2.

With that in mind, if I choose to fresh install Natty (instead of upgrading), will the files on HD 2 be safe?  Or will the install wipe HD 2 too?  My non-techie understanding is that everything on HD 1 (where Ubuntu is installed) will be wiped clean, and only HD 1.

Your advice will be very welcome, thanks.

---

### Post by grahammechanical on 2011-05-06
When you first installed did you let the installer program do all the work or did you make the adjustments yourself? In other words do you have any familiarity with the partition manager program?

If you make the adjustments yourself you will have to set mount points to some partitions/drives. You should set the same mounts points as you have now but only mark for formatting the partition that has the mount point of /. Then only the data in / will be wiped.

I have a separate partition for /home. so, when I do a fresh install I tell the installer to put Ubuntu into / partition by giving it a mount point of /  and I mark it for formatting but I only set my home partition with the mount point of /home. I make sure that I do not mark it for formatting. I do not lose my data.

Try it as a Live CD and run Gparted to see what partitions you have and their mount points before you do it for real.

Regards.

---

