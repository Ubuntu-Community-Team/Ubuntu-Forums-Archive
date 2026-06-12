---
title: "Formatting Hard Drive with Ubuntu on it!?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by bludderz on 2009-01-18
I have Ubuntu 8.04 installed on my Seagate Freeagent 500gb external hard drive.
However, I have jujst bought a new internal hard drive for my laptop, and instead of having Ubuntu on the external hard drive, I would like to install it onto the new Internal hard drive.
How can I format the external hard drive, as it is no longer recognised in windows.
Or is there some way I can make it recognisable to Windows, even though I have Ubuntu installed on it?

Thanks,
Aaron

---

### Post by taurus on 2009-01-18
While you are running Ubuntu from the internal harddrive, install gparted and use it to delete all the partitions on your external harddrive.  Then, create a one partition to take up the whole disk space and format it to ntfs filesystem.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```
Make sure none of the partitions on your external harddrive are mounted or you won't be able to delete them.

---

### Post by rahimveron on 2009-01-18
Use GParted to clone the external hard disk to the internal hard disk.

---

### Post by Montblanc_Kupo on 2009-01-18
GParted is preinstalled on LiveCD's... fyi.

---

