---
title: "Windows files to Unbuntu (samba) Choose drive letter"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by cK` on 2010-04-08
Hello everyone,

I am trying to set up samba file sharing on my windows to my unbuntu server.

When i go map my network drive it asks for a drive letter.

I am lost, unbuntu does not have drive letters. Which one am i supposed to choose there is like 50.........

If it wants me to put the drive that is on my windows machine, well. thats the C: drive and it is not even listed.

I know its probable obvious but i do not know what to do and some pointers would be awesome.

Thanks!

---

### Post by tarps87 on 2010-04-08
Assuming you are talking about setting the drive letter on the windows machine the drive name does not matter, it is the drive letter that windows will you.
If your samba share is setup correctly you should be able to select any drive letter and then browse the network for the share.

---

### Post by Steven_S on 2010-04-08
Windows knows all the disks and partitions in your windows pc. When you map a network drive (or partition, or folder - whatever you are creating the link to), you are basically asking windows to include it in the overview in your windows explorer. In order to do that, windows will assign a drive letter to it. 

This is the same as when you insert a usb stick - windows will all of a sudden show the stick under a new letter (D: or E:). 

What you do when you map is making a sort of "hard link" in the explorer, so that the networked drive shows up every time and you don't have to look for it under (My Network Places). 

You can use whatever letter you want, except the ones that windows needs for itself (A: for floppy, B: for I-don't-know-what), C: for the OS, D: for your cd and E: which is usually reserved inserted usd sticks or sd cards. 

The list windows shows you is basically that of the letters still available. I usually start with K:, but that is completely to your discretion. 

The drive letter windows assigns to the mapped location has nothing to do with the drive letter (or lack thereof) on the system you are connecting to. This is purely something that happens within the windows system you are mapping from.

---

