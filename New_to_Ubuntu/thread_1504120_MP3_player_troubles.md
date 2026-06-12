---
title: "MP3 player troubles"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by dirtynorth on 2010-06-07
I am a new ubuntu user (10.04) and I am trying to use a mp3 player I bought a while ago.  It is a 2GB COBY player that connects via USB.  The filesystem type is msdos.  When I first plugged it in I erased all the mp3 files from the device and now I can not add any new files.  The device is empty but it also has no free space.  

Any help would be greatly appreciated

---

### Post by PPrincipeza on 2010-06-07
Hello.

Check if you have GParted installed in your box (it should appear under System > Administration). If not, execute the following command from a Terminal to get it installed:

> sudo apt-get install gparted

Once installed, plug in your USB device and locate it under the GParted > Devices menu. You may right-click the default partition and format it to FAT32.

HTH.
--
PPrincipeza

---

### Post by dirtynorth on 2010-06-07
Figured it out!!

All I had to do was Format the player to the FAT file system and now it works like new.

---

### Post by dirtynorth on 2010-06-07
Thanks

---

### Post by e24ohm on 2010-06-07
> **dirtynorth said:**
> ThanksRemeber to use .ogg format for your music (smiles)...good luck...glad you were able to get it working.

---

