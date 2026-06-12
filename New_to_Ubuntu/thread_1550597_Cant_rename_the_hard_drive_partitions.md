---
title: "Cant rename the hard drive partitions"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Jmih on 2010-08-11
I just cant rename the harddrive partitions made by the disk manager utility

---

### Post by pastalavista on 2010-08-11
> **Jmih said:**
> I just cant rename the harddrive partitions made by the disk manager utility

Sorry to hear that. Why not? Why do you want to?

---

### Post by howefield on 2010-08-11
Try GParted, it is on the Live CD or you can install it with Synaptic Package Manager.

Maybe best using the Live CD as you won't be able to change the label on a mounted partition... maybe that's your issue with the disk manager utility.

---

### Post by Jmih on 2010-08-11
> **pastalavista said:**
> Sorry to hear that. Why not? Why do you want to?

just cant rename new volume to any other name

---

### Post by muteXe on 2010-08-11
From your screenie it looks like you want to do something like create a folder in your home folder called "Media" and then mount your 500Gb drive to that folder. 
Would that be better or less hassle than renaming the volume?

---

### Post by Jmih on 2010-08-11
i want to rename it media and mount.
will dismounting the drive will allow me to rename?

---

### Post by pastalavista on 2010-08-11
You need to unmount the drive before you can change the label. If you can't unmount with the Disk Utility, you need to use sudo in terminal```
sudo umount /dev/sdxx
```To find which dev it is use```
sudo fdisk -l #(lowercase L)
```

---

