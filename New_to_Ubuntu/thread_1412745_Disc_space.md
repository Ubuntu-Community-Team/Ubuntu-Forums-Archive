---
title: "Disc space"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by muksmak on 2010-02-21
I have 40 Gb hard disk and i have installed ubuntu 9.10 and i am a newbee with it i am getting used to it.

Now i have a problem that the file system shows only 21 gb alloted . 
As much as i know i did enterd 60% somewhere when i was installing it and that is why i guess it shows 21 GB.

I have very little space left. Can you help how can i use the other 17 GB
I dont want to format as i hae updated everything..

This is what fdisk shows 

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffff6a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4839    38869236   8e  Linux LVM
/dev/sda2            4840        4870      249007+   5  Extended
/dev/sda5            4840        4870      248976   83  Linux

Thanks in advance

Attached is what Gparted shows.

---

### Post by muksmak on 2010-02-22
plz reply

---

### Post by stlsaint on 2010-02-22
Im not sure but im thinking its the way lvm works. You may want to double check though. Do a wiki search on lvm maybe. Sorry i cant be of more specific help.

---

