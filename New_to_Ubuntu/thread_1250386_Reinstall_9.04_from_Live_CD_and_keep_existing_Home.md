---
title: "Reinstall 9.04 from Live CD and keep existing /Home?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by texla on 2009-08-26
I'm looking for info about reinstalling 9.04.  I had a system crash but from what I understand about Ubuntu, because I have a separate /Home partition, all I should have to do is reinstall the OS from the live CD by formatting the Root and Swap partitions and not the home partition. Anyone know the correct way to do this or is there a trick to it I should look out for? 

started another post earlier about this crash but I think this is a new topic now - but here it is:
[http://ubuntuforums.org/showthread.php?t=1250247](http://ubuntuforums.org/showthread.php?t=1250247)

---

### Post by SunnyRabbiera on 2009-08-26
Yeh be sure to go to the advanced settings in the installation setup.

---

### Post by alexlafreniere on 2009-08-26
As long as your home folder is in a separate partition, all you need to do is erase and reinstall on your OS partition and specify to the installer that you don't need a /home directory because it's in a separate partition.

---

### Post by texla on 2009-08-26
> **SunnyRabbiera said:**
> Yeh be sure to go to the advanced settings in the installation setup.
Dig it - will do - thanks!

---

### Post by texla on 2009-08-26
> **alexlafreniere said:**
> As long as your home folder is in a separate partition

Starting to wonder if I do have my home folder in a separate partition.  My advanced install disk says my dual boot (XP/Ubuntu) layout looks like this:

fat32 8.6 GB
ntfs 107 GB
ext3 82  GB
swap 1.5 GB

- don't see no home... :(

---

