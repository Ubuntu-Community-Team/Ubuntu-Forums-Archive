---
title: "Restoring Ubuntu without loosing data"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by JonathanDS on 2010-08-12
Okay, my problem is quite simple. I have ruined my current install of Lucid. I've searched the web for fixes, but found nothing that will help me. However, this thread is not about restoring my current install, so please comment with that in mind. The purpose of this thread is to ask if files kept in a separate partition, on the same HDD as my root directory, will be harmed if I reinstall 10.04 on it's original partition.

TY,
Jon

---

### Post by jtarin on 2010-08-12
As long as they are not on the partition where you install Ubuntu they should be fine.

---

### Post by JonathanDS on 2010-08-12
> **jtarin said:**
> As long as they are not on the partition where you install Ubuntu they should be fine.

Thank you. I feel more confident about this decision.

---

### Post by philinux on 2010-08-12
> **JonathanDS said:**
> Thank you. I feel more confident about this decision.

Backup anyway ;)

---

### Post by mapes12 on 2010-08-13
I've attached a screenshot to show how I divide up my HDD. This machine only has Ubu installed and the partitions are formatted to ext3.

Partitions are:-
16GB = /
103GB = /home
1GB = Swap

Now, if i screw up my system I just reinstall Ubu making sure that at the partitioning stage of the install select "Advanced" and then manually tell the install where to put "/" /home and Swap. Tell the installer to format the partition (16GB in my case) where "/" goes but DO NOT format /home (Otherwise your stuff and settings will be lost).

This gets me back up and running in no time. However, I then have to reinstall all my favourite application packages and Update Manager updates. So to cut this out I have Remastersys installed which I use periodically to make an installation .iso 

If my system crashes I burn the Remastersys.iso to a DVD-RW (it's to big for a CD-R) and use this as the installation disk. This then reinstalls UBU "as before" i.e it includes all the apps and updates I had before the crash. Saves time and works a dream. When making the Remasters.iso I use the "dist" option. There are many HowTo's on the web for using Remasters.

For my stuff in /home I hook up an external HDD and use Grsync to backup everything in there. After the first backup the sync feature of Grsync only backs up new or changed files and so is very fast. I find I have to configure Grsync to --exclude=*/.gvfs in the Advanced tab as this hidden file causes me problems.

That's it. Nice n easy. Everything safe and sound.

---

### Post by philinux on 2010-08-13
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

See Step 5 of the installation. 

**Specify Partitions Manually (Advanced)** Is the option needed.

---

### Post by mapes12 on 2010-08-13
> [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

See Step 5 of the installation.

Specify Partitions Manually (Advanced) Is the option needed.Yep! That's the one.

---

### Post by JonathanDS on 2010-08-13
Okay, I've finished, leaving me an encrypted 50 GB partition and a 260 GB / partition.
[IMG]http://i775.photobucket.com/albums/yy39/JonathanDS/Screenshot.png[/IMG]

---

