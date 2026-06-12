---
title: "how do I move things from one HD to another?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by ah pook on 2009-10-23
ok. My /   root is on a 30 gig which is dying. I have an empty 80gig, which I'd like to move everything to. All my movies, music, etc, are on an external HD. How do I move all my settings, Firefox , etc., to another HD? 
any help would be greatly appreciated...

---

### Post by kbielefe on 2009-10-23
I would boot into a live CD, partition and format the new drive using gparted, mount both the old and new drives, and do a cp -pr from the old to the new.

---

### Post by egalvan on 2009-10-23
PartedMagic LiveCD has software to clone one drive to another...
The iso is not too large, it's worth downloading.

---

### Post by mapes12 on 2009-10-24
To make an exact copy of a drive install the new drive as slave where the old drive is master. Then boot from a Live CD. Go to Terminal and enter:
```
dd if=/dev/sda of=/dev/sdb
```
where sda is the old drive and sdb is the new drive. Power down then disconnect sda from its IDE channel, connect sdb into sda's IDE channell (thus making it sda). You will need to change the jumpers as necessary for the drive. And vice versa for sdb. Reboot, removing the Live CD and everything will boot from the new HDD.

Another way is to burn yourself a Partimage CD. Then:

To Backup:

   1. Boot from the Partimage System Rescue CD
   2. Bring up a Terminal which will be a Root Terminal
   3. At the terminal prompt "mkdir /mnt/mydir"
   4. Then mount the second HDD to it "mount /dev/sdb5 /mnt/mydir" (where sdb5 is where you want to store the backup)
   5. Load Partimage
   6. Select the partition to backup
   7. Tab down to the location line and enter "mnt/mydir/filename" where file name e.g."root140809_partimage.
   8. Note that Partimage saves files with 3 zeros at the end. In the above case the file would be called root140809_partimage.000
   9. Do NOT select any compression


To Restore:

   1. Boot from the Partimage CD
   2. In Terminal mount the device where the backup is located
   3. On the next screen select the option that places zero's in unused space
   4. Check you are happy with everything then hit OK - job done!

---

