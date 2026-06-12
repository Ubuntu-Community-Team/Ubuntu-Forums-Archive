---
title: "Failed hard drive on 8.04 system"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by mlamberg on 2010-03-07
Looking for a good step by step procedure to diagnose, and see if any type of recovery is possible..  I am able to bring up the live version but need help from there...  Thanks

---

### Post by Sef on 2010-03-07
Under Places once your live cd is running, can you see the hard disk?  If so, click on it and see if after it mounts, you can access it.

---

### Post by lkraemer on 2010-03-07
mlamberg,
Here is what I would recommend.  

Power off, Open the case and determine what type Drive (IDE/SATA)
it is, and the Manufacture who made it.  Make a note of the Model
Number while you are looking at the drive.  Then close the case and
Power up.

Boot up, and go into the BIOS.  See if the Drive is detected.  If it is,
then boot from a LiveCD.  If it is not detected, then you are likely
not going to recover anything unless you send the drive to some Data
Recovery Business and pay for their services.  (Although if you install
and run testdisk you might be able to recover the Partition.  Just don't
install anything on the drive that is giving trouble.)

Run gparted to determine the Partitions.
SYSTEM -> ADMINISTRATION -> GPARTED

If the partitions are detected, then you can likely get to your data.
Try going to COMPUTER and opening your filesystem(Partition)
Copy all your data to another external drive.

After your data is safe, you can download your Manufactuer's Drive
Diagnostics and run them on the drive, but most of their tests are
Destructive and write to the drive, killing your data.

lk

---

### Post by desnaike on 2010-03-07
I  keep a hdd enclosure on hand bought it at Staples 3 yrs ago for $30.00 in that time 2 of my hdd have failed and I helped 7 of my friends get there files from dives that no longer boot if it's not a mechanical failure, disk stopped spinning u can recover your data.

---

