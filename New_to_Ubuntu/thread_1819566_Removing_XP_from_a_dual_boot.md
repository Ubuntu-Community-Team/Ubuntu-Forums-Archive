---
title: "Removing XP from a dual boot"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by johnupatree on 2011-08-06
Hi,
I have an old works laptop, XP Home and Pro installed. Installed 11.04 recently and would now like to remove all trace of Windows and have the laptop as a pure Linux machine.
How do I go about this. Absolute beginner, so as much plain English as possible please :)
Thanks
John

---

### Post by Gone fishing on 2011-08-06
Delete the partition, using gparted (either from the live cd or run ```
apt-get install gparted
```) then create a new partition using ext4 (gparted again) then run ```
sudo update-grub
```

Then mount the new partition you could do it manually but probably easier to use mount manager which you can install with ```
sudo apt-get install mountmanager
```

---

### Post by YesWeCan on 2011-08-06
Hi.
Boot a live Ubuntu cd or usb.
Use GParted to delete your Windows partitions and resize your Ubuntu partition: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Then reinstall Grub: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (section 12.2)

---

### Post by akand074 on 2011-08-06
Yes as the above said. You can download a partition manager and just delete the Windows partitions. Though, if you just installed Ubuntu and haven't done much on it, it might be easier to just reinstall Ubuntu using the whole drive. Keeps things clean. You might also want to consider making a separate partition for you home folder or at least a folder for data.

---

### Post by Muskegman on 2011-08-06
I would definatley do as akand074 said and do a clean install of 11.04 using the whole drive, make sure to back up everything you want to keep first.

---

### Post by SavageWolf on 2011-08-06
BEFORE you do any of this, can you tell us if you are using WUBI (Ubuntu in Windows). If you delete your Windows partition if using WUBI, everything will be gone.

---

### Post by johnupatree on 2011-08-15
Hi,
Thanks for the replies. Decided to go for a clean install, nothing on either system needed backing up or saving. Easy and effortless, thanks akand074 and all others who took the time and offered useful advice
John

---

