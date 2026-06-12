---
title: "LiveCD for Disk Partitioning [PPC]"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Xarok on 2010-09-30
I need to completely wipe my hardrive on my iBook G4 and create a single partition for installation (currently it has 3 or so partitions I need to get rid of).

Know of any live CDs with an easy to use GUI that would work on my iBook G4 that could allow me to do this? 

Thankyou

---

### Post by thinkinhurtz on 2010-09-30
Grab the Ubuntu Desktop live CD. It always has a gnome disk partitioner, look under System for Disk Utility.

---

### Post by mikewhatever on 2010-09-30
I believe you can both delete and create partitions from the Alternate installer. Are there any PPC live cds at all?

---

### Post by Daniel0108 on 2010-10-01
Take the Ubuntu Live Desktop CD and choose Delete partitions and use entire disk, when installing Ubuntu :)
This formats the hard-drive and installs Ubuntu on 1 partition, the other partitions will be deleted ;)
Yours,
Daniel

---

### Post by sikander3786 on 2010-10-01
> **Daniel0108 said:**
> Take the Ubuntu Live Desktop CD and choose Delete partitions and use entire disk, when installing Ubuntu :)
This formats the hard-drive and installs Ubuntu on 1 partition, the other partitions will be deleted ;)
Yours,
Daniel
+1 for the easiest way of accomplishing that.

---

### Post by mikewhatever on 2010-10-01
Those above suggesting Ubuntu live cds, they are not available for PPC architecture.

---

### Post by Daniel0108 on 2010-10-01
> **mikewhatever said:**
> Those above suggesting Ubuntu live cds, they are not available for PPC architecture.
no, you're wrong ;)
[http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/)
click on [Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-desktop-powerpc.iso")
EDIT: Sorry if it's not Live CD, I didn't try it ;) But non-live Cd's can partition too ;)

Yours,
Daniel

---

### Post by srs5694 on 2010-10-01
One thing you should look into is the partition requirements of the firmware used on your PPC Mac. I don't recall the details, but I'm pretty sure that the firmware requires one or two specific partitions at the start of the disk, so you shouldn't delete *all* the partitions on the disk. I recommend you research this issue before firing up a partitioning application.

Alternatively, you could use a Mac OS partitioning tool. It won't create Linux partitions, but you can be sure it'll create anything else that the platform requires. When you go to re-install Linux, you should be able to use the installer's partitioner to change the type(s) and/or delete and re-create just the OS partition(s).

---

