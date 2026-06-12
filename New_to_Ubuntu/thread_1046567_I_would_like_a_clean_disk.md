---
title: "I would like a clean disk"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Morganman on 2009-01-21
Hi

I am new to Linux and have installed 8.10.
So far I am very happy with it and will continue.

I am using a self built system with dual core Intel and Nvidia 9800 graphics, never seen windows.

I have had the system for a few weeks but have caused myself a few headaches.

The upshot is that I would like to start again with a completely fresh install, lessons learnt. I have saved all my important files.

To that end I would like a clean Hard drive, i.e. reformatted but I do not know how to do this from Linux. As the machine has never seen windows I don't want to use that route. Could you please advise as to how I can clean my disk from Linux.

Thanks

---

### Post by adult swim on 2009-01-21
whenever you reinstall just choose the option (i think it is step 4) "guided - use entire disk."  that will format your drive and install ubuntu at the same time.

---

### Post by taurus on 2009-01-21
Do you plan to use the same partition table when you reinstall?  If you do, you don't have to wipe anything first.  Just install it and when you get to the partition screen, pick the Manual option and tell the installer to mount whichever partition to /.  And if you have other partitions, mount them there too.  Also, don't forget to tell the installer to format those partitions so you would have a clean system when it's finished installing.

But if you want to delete all the partitions and start it from the beginning, then use gparted in System -> Administration to delete everything.  If there is a lock on the swap partition, you first need to unmount it or else you won't be able to do anything with your harddrive.

Applications -> Accessories -> Terminal
```
sudo swapoff
```

---

### Post by Michael.Godawski on 2009-01-21
hi,

you can boot from the live CD and run Gparted. There just delete the partitions you want to delete.

It is not bad to create a separate home partition when you are doing a fresh install; the next time you do a fresh dist installation your private data won't be touched.

---

### Post by Morganman on 2009-01-22
Thanks

I now have what i need until the next time.

---

### Post by panoramix77 on 2009-01-22
Hi everybody!!!

  Personally I prefer wipe out my entire HD using tools as Gparted, into the software building on the desktop/server ed.

  You can choose another method, as said adult swim, make a clean installation from the Ubu Cd´s.

   If you have other/another problem discuss it into this thread´s forum.

---

