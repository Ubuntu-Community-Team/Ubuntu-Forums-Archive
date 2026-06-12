---
title: "Can someone help"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by TDKING on 2009-09-23
I have already installed ubuntu on my comp i have two hard drives in the machine when i was going through the installation for ubuntu it gave me the option for how i wanted to set it up so i clicked on one of the hard drives then clicked to one disk but now i cant use the other disk i have in the comp it says i dont have permisions to do so but yet am the admin on the comp 

whats the best way to set up ubuntu ? can someone help me as i really want to get this working today if possible and or re-install 

also been reading that people have ubuntu running over xp or vista ?? but i just installed it on its own is this right ? 

thanks

---

### Post by credobyte on 2009-09-23
```
sudo fdisk -l

```

Can you show us the output of the following command ?

---

### Post by TDKING on 2009-09-23
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8998    72276403+  83  Linux
/dev/sda2            8999        9726     5847660    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris
/dev/sda6            8999        9302     2441817   83  Linux
/dev/sda7            9303        9324      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ca40ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9331    74951226   83  Linux
/dev/sdb2            9332        9733     3229065    5  Extended
/dev/sdb5            9332        9733     3229033+  82  Linux swap / Solaris

---

### Post by TDKING on 2009-09-23
thanks

---

### Post by credobyte on 2009-09-23
```
sudo chown -R user:user /dev/sdb1

```Replace user:group with your main username ( eg., dainis:dainis ).

Try copying a few files to your second drive and let us know the outcome.

---

### Post by TDKING on 2009-09-23
tried nothing happened mate same out come you do not have permissions

---

### Post by farsight on 2009-09-23
Hey there,

EDIT: This may be no use if you are intending on using a dual boot, in which one OS is allocated to one harddrive and the other OS to the remaining drive.

If you are going to use the reinstallation method then I'd offer the following advice. When you reach the partition screen asking you how you would like to install ubuntu, select the advanced option (i.e. you choose where to install the OS). 

If your 2 hard drives are, for example, allocated as sda and sdb, select the smaller of the 2. At the bottom you should see an edit partition option. In this partition select ext3 and mount / to this drive. On the second, larger HDD, edit the partition so you have /home allocated to the drive (using ext3). This should allow you to store all of your personal files to this HDD. 

The above method is the one I used to install Ubuntu Netbook Remix on my eee pc 1000. I neglected to create a swap partition, reasoning that I don't need space on my HDD to support my RAM.

If I can find the link for the setup guide I'll post it soon.

---

