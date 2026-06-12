---
title: "Wubi help"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by adeee on 2011-02-16
guys i ask my problem here. [http://ubuntuforums.org/showthread.php?t=1688921](http://ubuntuforums.org/showthread.php?t=1688921) but no reply. i already waste time on waiting reply.

i just need back up of my files in ubuntu. ubuntu is currupted. see my thread.
So i have a question.

i install ubuntu as a separate partition. 

so can i install wubi in windows to get just backup.? is the ubuntu (install in seprate drive) mounted?

Can i get the backup?

---

### Post by bcbc on 2011-02-16
You wubi install is all contained on a virtual disk (a file on the 'drive' you installed to \ubuntu\disks\root.disk). You need to copy the root.disk OUTSIDE of the \ubuntu directory. If you reinstall or uninstall wubi it will be deleted and all the data on it will be lost.

Then after you install again, you can mount it with the loop option and access your data on it:
sudo mount -o loop /pathtofile/root.disk /mnt
nautilus /mnt

If you want you can also access the data from windows using the tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (just point it at the root.disk file).


EDIT: did I misunderstand - is your ubuntu a direct install, not wubi? In that case, yes, you can install wubi to access it. But you could also use ext2read and get the data off it from windows as well. That would probably be easier.

EDIT2: Or a live CD.

---

### Post by mastablasta on 2011-02-16
you got this problme because you didn't tell them that you are running a wubi install. so now have a look here if it can help you:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by adeee on 2011-02-16
Well guys you just dont understand What i want to say.

i clearly says i install you ubuntu as a seprate partition.
and i want to install wubi for backup files that are in ubuntu.

But i sloved problem. and i backed up files via live cd. Thanxs for your bad help.

---

### Post by mastablasta on 2011-02-16
Well you were missunderstood. If so many people missunderstood you, are you sure they are the ones that are wrong? well it could be...
 
Anyway as you already found out LiveCD is also a recovery CD. Please mark the thread as solved (thread tools in upper right corner).

---

