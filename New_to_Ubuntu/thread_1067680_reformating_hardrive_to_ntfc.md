---
title: "reformating hardrive to ntfc"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by eyezdk on 2009-02-12
Hi all.

I had ubuntu on one of my harddrives, and now i made a clean install of the system back to normal (vista)

I can se, that i cant se the harddrive with ubuntu on it (around 100gb)

Any one have a program i can use in vista, to restore my hardrive to ntfs?

Thx for the help

---

### Post by geirha on 2009-02-12
You want to remove Ubuntu and put an empty partition in its place, or do you want to be able to see the contents of the Ubuntu parititon?

---

### Post by mcduck on 2009-02-12
You can simply do that with the Disk Management in Windows.

---

### Post by eyezdk on 2009-02-12
well, i never removed ubuntu. i just had a ghost image on a dvd, and reinstalled the vista. 

mcduck, what do u mean? i cant se the drive in windows.

---

### Post by DerHesse on 2009-02-12
simply run diskmgmt.msc (START-> Search: diskmgmt.msc, and klick on it)
Find the right Partition and rightclick to format ist to NTFS.
 
P.S: It is not "normal" to run Vista. :lolflag:

---

### Post by mike555 on 2009-02-12
Do you mean that you can't install Windows because it comes up with a grub error ?   if so you will need to clear the MBR , you can do that in Linux with the command (in terminal)  sudo dd if=/dev/zero of=/dev/hda bs=512 count=1       ... that should totally clear the Master Boot Record , and let your Windows disc install ... then , if you want you can reinstall Ubuntu in a dual boot ......


  After re-reading your post, I guess you already have Windows installed ... so DON"T use this command or else Windows wont boot........

---

### Post by mcduck on 2009-02-12
> **eyezdk said:**
> well, i never removed ubuntu. i just had a ghost image on a dvd, and reinstalled the vista. 

mcduck, what do u mean? i cant se the drive in windows.

At least with all previous Windows versions the Disk Management is part of Administrative Tools, under System Management in the windows settings.

It's able to reformat any partition to Windows file systems, and shows all your drives & partitions, no matter if Windows can actually read the contents or not. Ubuntu partition will show as "unrecognized file system", and clicking it will give you option to format it.

---

### Post by eyezdk on 2009-02-13
cool, thx for the help. 

But looks like vista is just crap, and cant reformat it :/

I am gona reinstall linux one more time, but not realy sure on what to install. 
i have turion X2 cpu from AMD, and ATI radeon. 

What will work best for me, Ubuntu og Kubuntu? 
the only game I am gona to have on it is WoW, else its all writing and some CAD programs. 
I am also looking for one that not to hard to set up. 
what do u guys think?

---

### Post by mcduck on 2009-02-13
That's simply a question of preference. Which one you like more, Gnome or KDE? The only difference between Ubuntu and Kubuntu is the desktop environment and programs installed by default.

---

### Post by eyezdk on 2009-02-13
> **mcduck said:**
> That's simply a question of preference. Which one you like more, Gnome or KDE? The only difference between Ubuntu and Kubuntu is the desktop environment and programs installed by default.

Well, my cpu and ram should handle some "nice" desktop. so its ok if it can look "fancy" 
programs, well, openoffice is a start. firefox, with working java (for netbank)

I am sorry, but I am not that good to linux, so KDE and Gnome dont tell me much.

---

### Post by lakersforce on 2009-02-13
Ubuntu = GNOME DE
Kubuntu = KDE
Xunbuntu = Xcf4 DE

Only difference: Desktop Enviroment

---

