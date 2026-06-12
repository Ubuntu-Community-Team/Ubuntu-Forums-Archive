---
title: "dmraid problem"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by kevinwinner on 2009-05-06
Hi, I'm trying to move my desktop to Ubuntu and have run into some problems with dmraid.  I have 2 Maxtor drives setup in a RAID0 array which I used as my storage drives in Windows.  I do not have any interest in booting from them, which seems to be the only topic covered in tutorials, I only want to mount the array without reformatting it (I don't have anything to back that much data up to).  dmraid got setup and configured properly, but I can't mount the drive.  Here's the output I get from some calls:

```
sudo dmraid -r
/dev/sdd: nvidia, "nvidia_dcdcdbic", stripe, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_dcdcdbic", stripe, ok, 488397166 sectors, data@ 0
``````
sudo dmraid -a y
RAID set "nvidia_dcdcdbic" already active
RAID set "nvidia_dcdcdbic1" already active
```Thank you to anyone who can help me with this, let me know if you need me to post any more information.

---

### Post by ronparent on 2009-05-06
I had your problem exactly. You could fix this and see those drives on your desktop if you wanted by mounting it in /etc/fstab. I currently have selected windows partition so mounted. Simply link your symbolic link for the partition as found in **/dev/mapper** to a mount point. If the directory you want it to appear in doesn't exist in the file system you create it wherever you want for it(ie /media/WinXPfiles/). Congratlulations. I think you have it about made!

---

### Post by kevinwinner on 2009-05-08
Sorry, but I'm not experienced with mounting drives.  What commands would I use to mount this this way?

---

### Post by b0b138 on 2009-05-08
First make a folder to mount the drive

```
sudo mkdir /media/whatever
```

Then mount the array

```
sudo mount /dev/mapper/nvidia_dcdcdbic /media/whatever
```

cross your fingers :)

---

