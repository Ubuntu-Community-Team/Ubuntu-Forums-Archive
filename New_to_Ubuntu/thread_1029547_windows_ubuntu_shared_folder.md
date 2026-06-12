---
title: "windows ubuntu shared folder"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by downhiller2010 on 2009-01-03
what is the easiest way to set up a shared folder with read/write privleges between windows xp and ubuntu 8.10?

my ubuntu currently has no wireless access

---

### Post by BDNiner on 2009-01-03
U need a file system that both can understand. The best bet us FAT32 although with some configuration you can have windows see EXT2 filesystem (doesn't work that well in my opinion). Ubuntu can connect to windows shared folders with very little issues. Work out of the box. all depends on what kind of setup you are running.

Are you sharing files across a network or on the same computer?

---

### Post by Gannon8 on 2009-01-03
To get files from your Windows partition, look in the Places option on the toolbar for your windows partition (either the size of the partition or the partition label) and click it. Your files are in the "Documents and Settings/<your username>/My Documents/"

---

### Post by downhiller2010 on 2009-01-03
> **Gannon8 said:**
> To get files from your Windows partition, look in the Places option on the toolbar for your windows partition (either the size of the partition or the partition label) and click it. Your files are in the "Documents and Settings/<your username>/My Documents/"

can I read/write cross platform through here?

---

### Post by downhiller2010 on 2009-01-03
I installed with wubi to where i didnt uave to partition. My disk is a NTF. Im not seeing that file in places. Im tryimg to set this up so i can get drivers for my wireless card working

---

### Post by 1packer on 2009-01-03
I don't use Wubi, but I saw another post earlier about this issue. It seems that the Windows files are located in the /host directory of Wubi. I would check the various places in the system, from the bar on top, to see if you can find them.

---

