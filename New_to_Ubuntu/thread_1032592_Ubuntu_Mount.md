---
title: "Ubuntu Mount"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by HazByn on 2009-01-06
hi all..

i'm not sure i should open a thread but already search and cant find one.

i'm new to ubuntu.my machine have 4 partitions (2 hdd). C D E and F.im a windows xp user.After a while i learn and study ubuntu and decided to install from the cd (8.04).I install it in E.After completed i enter ubuntu environment.the problem is i cant find E all i have is C D and F.so any suggestions?.Some said i should mount it..if i mount it will all the data in E lost?..(*got few important documents that can be view in windows*).hope all the ubuntu genius help me here.thanks.

p/s: sorry for my english.cheers..

---

### Post by Titan8990 on 2009-01-06
Mount just means get ready to use. In Ubuntu drives are not defined C, D, E, etc like in Windows.

Go to Applications -> Accessories -> Terminal

Type the following:


```
sudo fdisk -l
```


Copy and paste the results in your next post.

---

### Post by kestrel1 on 2009-01-06
Stop thinking like a Windows user:D
The drive that you installed to will show up as filesystem. If you go to Places - Computer & open filesystem you will see the files on the drive.
All you personal data is held in home - 'yourusername'

---

### Post by HazByn on 2009-01-06
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3afa3af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4981    40009851    7  HPFS/NTFS
/dev/sda2            4982        9964    40025947+   f  W95 Ext'd (LBA)
/dev/sda5            4982        9964    40025916    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8683448

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sdb2            9730       19457    78140160    7  HPFS/NTFS

this is what i get after sudo fdisk -l

---

