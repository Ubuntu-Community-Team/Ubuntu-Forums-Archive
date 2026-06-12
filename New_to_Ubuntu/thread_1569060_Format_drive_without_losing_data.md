---
title: "Format drive without losing data"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by vishalsmisra on 2010-09-06
> **oldos2er said:**
> Just boot from the Ubuntu LiveCD, run the installer, and choose 'Guided--Use Entire Disk' when the option appears.
this will erase all the partition, even i am facing the same issue i need to use only UBUNTU, but dont want to delete the other file data its too much to take the back up

---

### Post by shreeyashattal on 2010-09-06
> **vishalsmisra said:**
> this will erase all the partition, even i am facing the same issue i need to use only UBUNTU, but dont want to delete the other file data its too much to take the back up

Please shrink one of your volumes with ample free space, create a new partion and use that partition for linux, u will also need to create a swap partition

---

### Post by coffeecat on 2010-09-06
If you want help with preparing your machine for Ubuntu, but keeping the partition with your files on, boot up with the live CD, go to System > Administration > Gparted. With the Gparted window open, press Alt-Print to get a screenshot of the window and post that.

---

### Post by stmiller on 2010-09-06
Resizing partitions with data can take a long time (hours). It's best to just dump your files onto an external drive, then format and reinstall Ubuntu on your computer.

Then you can just copy your files back over to the clean install.

---

### Post by TNT1 on 2010-09-06
Backup your data, format, restore your data.

---

