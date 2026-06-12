---
title: "How come i Cant Boot to Windows 7? (GRUB)"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Ira_S on 2010-01-17
hey,   I have Windows 7 Installed on my machine,    

Decided that i would install Ubuntu 9.10 with windows 7,  


after i did the installation (i made a new partition for it, DID NOT FORMAT WINDOWS 7 Partition)           

i cant boot to windows 7,    once the grub boot loader comes on, it gives me a series of things to boot from,   (windows 7 loader is one of them)   however, when i select the windows 7 one,  it just loops around and restarts the GRUB boot loader!!!!.      i can boot into ubuntu though,...   Is there a way i can edit, this?   or if anything,  Delete the Grubs boot loader so windows takes over?  i would rather beable to choose from both of them, i just cant figure out how, since the GRUB is glitchy....

---

### Post by warfacegod on 2010-01-17
Open a Terminal and type:

```
sudo update-grub2
```

---

### Post by Ira_S on 2010-01-17
I just did that,  and it dident do anything,  a whole bunch of code came up though,  and then it finished (i soppose)  but i tryed restarting,  and it still does the same thing =[

---

### Post by warfacegod on 2010-01-17
For now, I suggest searching the forum on ways to fix Windows 7 bootloader.

---

### Post by lidex on 2010-01-17
Ira_S:
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Ira_S on 2010-01-17
at the end of the explanation, it talks about replacing files? but it doesent say. .........    lol. this is getting redicolous

---

### Post by Ira_S on 2010-01-17
ok i tried that, and it totaly just ruptured my whole GRUB thing, and i had to reinstall Ubuntu,    but now when i launch windows 7,  it says "unknown file system"



at this point, i just want to GET RID>   of UBUNTU ALL TOGETHER, it has caused me too much **** in the face.   is there any partitioning software i can use on the disk without installing ubuntu?

---

### Post by Mark Phelps on 2010-01-17
> **Ira_S said:**
> after i did the installation (i made a new partition for it, DID NOT FORMAT WINDOWS 7 Partition) 
Did you allow the Ubuntu installer to shrink the Win7 partition? Or did you do it the proper way -- use the Win7 Disk Management utility to shrink the partition?

The link that was provided in a previous post covers the steps needed to restore the Win7 boot loader.

---

