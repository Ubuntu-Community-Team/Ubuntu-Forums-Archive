---
title: "Quick Partitioning Question"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by The Pokemon Master on 2009-10-22
I'm new to the hardware side of computers and so I came across a little issue. I have two storage devices inside my computer: a 40 GB ATA hard drive which came inside the computer, and an 80 GB ATA hard drive installed by a friend a couple of years back. The 40 GB hard drive has a useless Windows XP partition. My question is this: can I reformat the 40 GB hard drive and not do any damage to my computer? (Sorry if my grammar wasn't the greatest or if my question was stupid.)

---

### Post by earthpigg on 2009-10-22
yes, yes you can.

keep in mind it is essential to have a solid and recent backup before ever doing anything with partitions.

if any part of your Ubuntu install (/, /home or anything else) is on the 40gb hard drive, then do it from an Ubuntu LiveCD. system -> administration -> partition editor.

---

### Post by The Pokemon Master on 2009-10-22
Thank you earthpigg!

---

### Post by x C0MMAND0 x on 2009-10-22
Here is what I would do to be TOTALLY safe.
Open your computer and DISCONNECT the hard drive that Ubuntu is installed on.  Boot to a live CD and then re-format the older hard drive then.  That way, you can feel safe that nothing will happen to your files (assuming they are ALL on the hard drive you disconnected)

---

### Post by jmundinger on 2009-10-22
My desktop has a similar setup.  It came with windows xp installed on an 80 gb hard drive.  When sp3 came out, my attempt to update xp failed and the failed process hosed the OS.  Rather than reformat it and reinstall windows, I had a second hard drive installed with the original hard drive slaved to the new one.  I installed xp to the new hard drive, creating several partitions in the process.  I then attempted to repair the system on the old hard drive from the OS on the new one - it was so hosed, I couldn't "see" it from the new system.  Disk management knew it was there but didn't know what it was.  Fortunately, all of the data on that hard drive was already backed up.  So, I reformatted it from the new system - I had to use disk management to delete the partitions on it before I could do anything else.  At that time, I also put three partitions on the old drive.  I installed Windows in one partition - just to have it in case of a crisis.  I used the rest of the old drive as a storage, a place to back up my back ups.  I have since bought another external hard drive and didn't the additional redundancy.  So, I deleted the largest of the storage partitions, with disk management, and left it as empty space and then installed 9.04 into that space.  The only affect on Windows is that GRUB supercedes the old MBR.  Windows appears as an option in GRUB and, when I select it, I then have a choice between the two Windows systems.

---

### Post by The Pokemon Master on 2009-10-22
> **jmundinger said:**
> My desktop has a similar setup.  It came with windows xp installed on an 80 gb hard drive.  When sp3 came out, my attempt to update xp failed and the failed process hosed the OS.  Rather than reformat it and reinstall windows, I had a second hard drive installed with the original hard drive slaved to the new one.  I installed xp to the new hard drive, creating several partitions in the process.  I then attempted to repair the system on the old hard drive from the OS on the new one - it was so hosed, I couldn't "see" it from the new system.  Disk management knew it was there but didn't know what it was.  Fortunately, all of the data on that hard drive was already backed up.  So, I reformatted it from the new system - I had to use disk management to delete the partitions on it before I could do anything else.  At that time, I also put three partitions on the old drive.  I installed Windows in one partition - just to have it in case of a crisis.  I used the rest of the old drive as a storage, a place to back up my back ups.  I have since bought another external hard drive and didn't the additional redundancy.  So, I deleted the largest of the storage partitions, with disk management, and left it as empty space and then installed 9.04 into that space.  The only affect on Windows is that GRUB supercedes the old MBR.  Windows appears as an option in GRUB and, when I select it, I then have a choice between the two Windows systems.

What exactly hosed your XP?

---

### Post by earthpigg on 2009-10-22
one thing before you proceed, Pokemon: i assumed that this was ***not*** a [wubi]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29") install in my reply earlier. 

if it ***is*** a wubi install, please let us know, as that will involve a whole new mess of steps that will need to be taken.

---

### Post by The Pokemon Master on 2009-10-22
No. It will be a complete reformatting of the hard drive. Unless it being the Primary Master has any complications associated with it, I will be okay.

---

### Post by searchfgold6789 on 2009-10-22
SIMPLE SOLUTION
Get the windows disk, boot from the disk, enter into the recovery console, wait for everything, and enter in :    DISKPART   Then, use the arrow keys to select the Windows partition, and press D, then L if you're really sure.

---

### Post by jmundinger on 2009-10-23
> **The Pokemon Master said:**
> What exactly hosed your XP?

Neither I nor Microsoft tech support knows.

I was doing the the update from XP sp2 to XP sp3.  The update failed.  I rebooted the computer and ran update a second time.  That time the update failed a second time and the procedure to undo the update also failed.  At that point, the system hung up and then it would not boot up.  I took it to a local shop - he installed the new hard drive but was unable to recover the system on the old drive and, as I noted, I couldn't even read it from the XP that I installed on the new hard drive.

If there is an upside to the story, I learned a few things about xp in the process.  I also developed a curiosity about GNU/Linux.

---

