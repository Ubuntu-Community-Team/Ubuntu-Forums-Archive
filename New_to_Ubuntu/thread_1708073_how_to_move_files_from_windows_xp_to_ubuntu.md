---
title: "how to move files from windows xp to ubuntu?"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Artas187 on 2011-03-16
hi, i am very new to linux, read a lot of documentations here but didnt find answer to my issue of how to move files from windows to ubuntu in real-time. is this possible anywayz? because it would take ages to load windows, copy some files on my usb, then load linux, copy them and start it all over again. keeping in mind i would have to do this with 300+ gb........... any help is appreciated

---

### Post by nkae100 on 2011-03-16
You can mount the Windows partition from within Linux. In GNOME (a desktop enviornment for Linux, which the Ubuntu distribution uses), you should see your Windows partition in the 'Places' menu. Simply clicking on it should mount it, then you can copy the files over the same way you would do it in Windows..

---

### Post by Arand on 2011-03-16
If I understand it correctly:
You have only windows installed currently and would like to replace windows with only ubuntu and keep the data files on the windows filesystem?

- arand

---

### Post by Artas187 on 2011-03-16
yes, i am thinking of uninstaling windows but i would like to keep them for a while. talking about that partition on my desktop, i see only c disk while all my important files are on d disk (i installed ubuntu on d disk if thats related somehow). btw thnx for quick reply:p

---

### Post by nothingspecial on 2011-03-16
> **Artas187 said:**
> yes, i am thinking of uninstaling windows but i would like to keep them for a while. talking about that partition on my desktop, i see only c disk while all my important files are on d disk (i installed ubuntu on d disk if thats related somehow). btw thnx for quick reply:p

:shock:


It is related if you used the whole d disk. If you did that your files are gone. Please tell me you only installed Ubuntu to a partition of your d disk.

---

### Post by Artas187 on 2011-03-16
well, there was approx, 45 gb left on my d disk, i installed ubutu through windows installer and chose the size of installation of 14 gb if thats what you mean

---

### Post by nothingspecial on 2011-03-16
Phew. That's ok then.

So you have wubi. I don't really know anything about wubi.

---

### Post by arun ganesh on 2011-03-16
Why don't you try Virtual Box..There you can have linux Os at same time u have Windows os and share the files of your host(windows) with the guest (linux) just cut copy paste will do....

---

### Post by Artas187 on 2011-03-16
wow, didnt think of that. thnx:p

---

### Post by MibunoOokami on 2011-03-16
The windows partition should be in the places menu. It should have an image of a drive, but may have a different name. Mine for example gets called "54 GB Filesystem" rather than Windows or C: for whatever reason. Another possibility, go places> computer. It may show in there. 
I am only new myself, but I think if you can't see it in your places or computer menu, then you may have deleted the entire partition and it is now your Ubuntu OS. I could be mistaken though.

---

### Post by Arand on 2011-03-16
I'm not really sure I understand the way your partitions are arranged, I would assume windows is on C: implying that if you used wubi you would've also installed ubuntu to C:
Is C and D separate partitions(filesystems) or harddisks?

Anyhow posting the result of running```
sudo fdisk -l

#List all partitions found on system, note lowercase L, NOT number 1
```In the terminal (Start via Ctrl+Alt+T or in accessories in main menu)
...Will hopefully make things clearer.

> **arun ganesh said:**
> Why don't you try Virtual Box..There you can have linux Os at same time u have Windows os and share the files of your host(windows) with the guest (linux) just cut copy paste will do....If Artas does intend to migrate to ubuntu at some point, using virtualbox is probably not a good idea, since the install will (probably) need to be redone in order to get it onto a physical partition.

Likewise also with wubi, although the migration is somewhat easier there, I would still go for the dual-boot proper setup instead, if as was mentioned, intent is to migrate over to ubuntu completely at some pont. 


- arand

---

### Post by Artas187 on 2011-03-16
thnx for all the help, everything goes great

---

### Post by prshah on 2011-03-16
> **Artas187 said:**
> how to move files from windows to ubuntu in real-time. 

> **Artas187 said:**
> i installed ubutu through windows installer

If you have installed Ubuntu through Wubi (Windows installer), your files are directly accessible through the "/host" directory (folder) in Ubuntu.

Important point: In a wubi install, the Ubuntu installation resides in a "virtual drive", which is actually a file on the host OS (Windows in this case). If you installed it to "D:" drive, it will probably be in d:\ubuntu or d:\wubi.

If you copy files from your host partitions to the "virtual" ubuntu drive, you will be pointlessly filling up space on the "d:" drive.

If you want to migrate your wubi install to a true install, please consider using the LVPM tool. Please post back if you want more information on this.

---

### Post by Artas187 on 2011-03-16
ok, i got the idea, i was just learning how to use linux because i have never seen it in action, never. i just wanted to migrate from windows (that goddamn overpriced crap!!!) to something more... lets say normal and i heard that ubuntu is just the case at least for the beginners. so if instal linux on my d harddisk (while windows are occupying c disk) will i still be able to chose between these two OS when bios starts just like wubi allows?

---

### Post by nothingspecial on 2011-03-16
Yep

---

