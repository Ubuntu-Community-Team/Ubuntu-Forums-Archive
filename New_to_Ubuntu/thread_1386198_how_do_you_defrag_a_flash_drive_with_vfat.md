---
title: "how do you defrag a flash drive with vfat"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-01-20
I have a usb flash drive that is getting slow. how do i defrag it under ubuntu 910? i know that linux does not need to be defraged but my usb drive is vfat. can this be dune?

---

### Post by rbc on 2010-01-20
You might want to read mgmiller's first post in this thread:
[http://ubuntuforums.org/showthread.php?t=1378591&highlight=defrag](http://ubuntuforums.org/showthread.php?t=1378591&highlight=defrag)

---

### Post by kerry_s on 2010-01-20
if it's not that big, just copy everything off & just reformat it with gparted, then copy everything back.

---

### Post by lance bermudez on 2010-01-20
my usb disk is 16gb and i can read and write to it. it has just gotten slow becuse the the file fragmention. I need the usb disk file system to stay somthing that windows (work) can still read and ubuntu(home).

---

### Post by vanadium on 2010-01-20
Interesting read, in the linked post. Are you sure that the file fragmentation is causing the slowness?

Anyway, kerry_s approach is the way to go. Just reformat the drive into again into vfat and copy the data back.

To reformat the USB, you can use gparted. If not installed, get it in the usual way using Synaptic Package Manager.

Start gparted with root permissions: type Alt+F2, then "gksudo gparted".

Use the drop down button to select your USB. Right-click the partition, choose "unmount". Then use the right click menu again to format the partition to vfat.

Quit gparted, remove the USB stick and plug it back in again. It should again be automounted. Then copy the data back.

---

