---
title: "How to partition HDD for Jaunty"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by acimna on 2009-07-31
Partition 1: Free space (say 100GB).  If EVER I need anything outside of Linux

Partition 2: Extended partition (say 250GB)
      Locical 1 for Ubuntu (say 50GB to allow for Edubuntu ...)
      Locical 2 for Ubuntu /Home (say 100GB)
      Logical 3 for Suse (say 10GB)
      Logical 4 for Suse /Home (say 10GB ... IF, and only if Suse can't save data 
                   in Ubuntu /Home)
      Free space

Partition 3 (?) for swap (say 5GB)

Free space (about 146GB)

If this could work, please help with partition names as I'm a bit lost with the NTFS (?) and Ext3 jargon.

---

### Post by mapes12 on 2009-07-31
> **acimna said:**
> Partition 1: Free space (say 100GB).  If EVER I need anything outside of Linux

Partition 2: Extended partition (say 250GB)
      Locical 1 for Ubuntu (say 50GB to allow for Edubuntu ...)
      Locical 2 for Ubuntu /Home (say 100GB)
      Logical 3 for Suse (say 10GB)
      Logical 4 for Suse /Home (say 10GB ... IF, and only if Suse can't save data 
                   in Ubuntu /Home)
      Free space

Partition 3 (?) for swap (say 5GB)

Free space (about 146GB)

If this could work, please help with partition names as I'm a bit lost with the NTFS (?) and Ext3 jargon.

I haven't tried a dual boot Linux box but your suggestion looks good to me. Some observations:

- I don't think you will need 50GB for Logical 1. 15GB should be more than enough. But if you start at 50 you can always resize (GParted) later.
- Swap should be roughly twice your system RAM

Don't worry about partition names. The Partition tool will take care of that. Until you know what data you are going to put on Partition 1 you could leave that unformatted ftb. It will probably be labeled sda1 by the Partition tool. Partition 2 (Extended Primary partition) will probably be labeled sda5, Logical 1 sda6 and so on. 

When installing Ubu remember to select "Manual" when you get to the partitioning section so that you can tell it where you want "/" /home and swap to be installed.

EDIT: Forgot to mention that the file system should be ext3. Swap works itself out.

---

### Post by mikechant on 2009-07-31
> Swap should be roughly twice your system RAM

This used to be the standard advice, but now it really only applies if you have a very small amount of RAM (say 512Mb or less).

If you have more than that the usual recommendation is for swap to be equal to RAM size. This is plenty for normal swapping and allows you to use the hibernate function. If you don't want the hibernate function you probably don't need more than 2Gb of swap even if you have more than 2Gb RAM (though of course disc space is cheap so it doesn't matter that much).

---

### Post by oldfred on 2009-07-31
Some on this site recommend a separate /data partition rather than separate /home.
My understanding is that the separate /home is the way to go if you are using one ubuntu and when you want to upgrade it makes it easy to do a full reinstall instead of an upgrade. The use of a separate /data is when you have different versions of linux that may use different versions of applications so the hidden config files in /home could be different. You keep separate /home for each version of linux in root but put your data in a separate /data to share with all versions.
I have also seen some recommendations for a very small separate /grub partitition just for grub not a /boot partition. This is a master menu.lst to chain boot into the various versions of linux.

---

