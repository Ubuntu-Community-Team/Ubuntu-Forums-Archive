---
title: "How do i repartition the hard drive?"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by bradleyed on 2009-09-29
i want to repartition the hard drive without reinstalling ubuntu. i currently have a partition with xubuntu, a partition with ubuntu (ext3 because i wasn't sure if i could trust ext4), and a blank 20 gigs (because i was planning on trying out fedora). i want to get rid of all those partitions and just have my ubuntu (ext4) and some swap.

---

### Post by thoriumchameleon on 2009-09-29
go to synaptic package manager and type in gparted. Install the package and then go to system / administration / partition editor... I think once you launch the program the rest is self explanatory. If it isn't post your questions.

---

### Post by bradleyed on 2009-09-29
thanks, i've deleted the other partitions but now i don't know how to resize the active partition to include all of the unallocated disk space. (without deleting the entire hard drive)

---

### Post by thoriumchameleon on 2009-09-29
Ok. let me guess. theres an image of a keychain and it won't let you select resize/move partition.. If this is the case then boot up from the live cd if you still have it and select try ubuntu without making changes to my computer. go to partiton editor. it should let you do it now. Also you should make sure you have a partiton for swap space.. right click the unpartitioned space and select new partition then select linux-swap for format to and make it mabey 2.5GB (2,560mb)...then you can move it to the end of the drive and expand your primary ubuntu partition. 
I'd say cheers but i think thats a brittish thing lol.

---

### Post by drs305 on 2009-09-29
If the previous post didn't explain it sufficiently, this should help:

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by bradleyed on 2009-09-29
oh. thanx.

---

### Post by thoriumchameleon on 2009-09-29
no problem just make sure you change the thread to solved

---

