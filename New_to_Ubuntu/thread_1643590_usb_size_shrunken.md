---
title: "usb size shrunken"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by DracomanX69 on 2010-12-12
Hey yeah, this hapopened to me too. Except i had done openSuse, and when i tried to delete it this happened.

My usb is a 3.8gb one, i was trying to mount a live version of openSUSE onto it, but the program couldn't read the iso, so i had to rename the .iso to .raw. It worked, but was crap. When i put my usb back into windows 7, it said i needed to format to use. But it was like this.


Capacity: 681mb
File System: Fat
Allocation Unit Size: 42 kilobytes

WTF!!!!!!
so i quick formatted it but windows only recognized that it was 681mb, with 31mb used (even though the drive was emty)
So i ejected it, put it back in and reformatted it (not quick), and now it's working again.

---

### Post by pchilds on 2010-12-12
You are using the usb on linux and on windows. Usb's that I've used to transfer data between OS's set up multiple partitions on them with different filesystems. Windows doesn't recognise the ext4 native filesystem of Linux and so it probably isn't recognising the size of space that used to be occupied by your .iso file hence why you only have 681M left. Quick format will only operate on this 681 chunk so you can't expect it to work while a full format will remove all filesystems and set up new ones giving you all your space back. I can get the available space back by making sure when I delete files I also remove their wastebasket entries too (took me 4 months of searching to find out how to do this in SLE).

---

