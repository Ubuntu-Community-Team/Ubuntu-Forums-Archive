---
title: "NTFS files disappeared"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by remco_t on 2009-05-11
I have this VIA Epia PD1000 system which I'm using as a (light) server. So far I've managed to do (read: mess up) a lot of things;

- installed Ubuntu server (LAMP)
- installed GUI
- reinstalled kernel (C3-CPU not supported by Server)
- set up samba, etc

so far so good. My HDD is a LaCie 120GB LittleDisk, with 4 partitions: /root (EXT3 4,76GB), /home (EXT3 14,3GB), /swap (SWAP 973MB), and a formerly FAT32 partition (91,77GB). On the FAT32 I've recently copied a *lot* of files from an OSX computer after which the drive started giving I/O errors when trying to acces that partition. These errors occured both from the Ubuntu installation as well as when the drive was connected to a Vista machine. Hardware testing indicates the drive is perfectly healthy and I'm guessing the errors are due to some limitations I've read about in the FAT32 filesystem.

I decided to remove the FAT32 partition (all data on there was either backed up or not important anyway) and replace it with an NTFS one since I still want to be able to hook the drive to either my regular PC (Vista) or my laptop (Win7rc) using it as a mobile drive. I've managed to install one, mount it without problems and hook it up to samba just as the FAT32 partition was. Great.

Now, I've just unhooked the drive from the Ubuntu machine, connected to Vista, copied files on the NTFS partition, and booted the Ubuntu machine again. Now Ubuntu says the drive is completely empty... Connected it back on the Vista machine and the files are still there... Has anyone experienced similar problems or am I overlooking something incredibly simple?

---

### Post by lisati on 2009-05-12
My first thought is this: did Windows shut down properly?

---

### Post by nandemonai on 2009-05-12
> **lisati said:**
> My first thought is this: did Windows shut down properly?

My thoughts too, if it's a removable drive be sure to 'Safely Remove' it in Windows before connecting it to the server.

---

### Post by remco_t on 2009-05-12
Yes, it's a removable drive ([specs]("http://www.lacie.com/uk/products/product.htm?pid=10982")) and no, I didn't remove the drive with the "remove hardware safely" option. I must admit I never use that option with external equipment...:( I just unplugged it after file operations were done. Maybe I should start using that option then...

Question remaining is, how do I make Ubuntu see the files again? You guys think there's any way of making that happen? Or should I hook up the drive to my Vista machine again, copy all data, (safely) remove the drive and rebuild the partition in Ubuntu?

---

