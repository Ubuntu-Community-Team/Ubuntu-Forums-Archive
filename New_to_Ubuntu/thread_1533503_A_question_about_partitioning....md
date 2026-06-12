---
title: "A question about partitioning..."
date: 2010-07-18
forum: New to Ubuntu
---

### Post by dylan_m on 2010-07-18
Hey, I just joined this forum and am not sure where to post this... but anyway I have a question about partitioning in gParted.

I made a live gparted cd and ran the program off it. It works fine.  However, I am having trouble moving the 39.5GB of unallocated space to my data drive ( /dev/sda3 ) **see screenshot** . I have tried moving sda3 next to the unallocated space, but it wouldnt work..


How can I do this?

Thanks :)

---

### Post by Elfy on 2010-07-18
That looks like you are trying to work on the partitions from within a running ubuntu - there is a padlock against the linux partitions.

Boot with the livecd - right click the swap partition - there will be an option to turn off the swap - do that and refresh. You should then find that the padlock symbols have gone, then you can do what you wish.

---

### Post by dylan_m on 2010-07-18
> **forestpiskie said:**
> That looks like you are trying to work on the partitions from within a running ubuntu - there is a padlock against the linux partitions.

Boot with the livecd - right click the swap partition - there will be an option to turn off the swap - do that and refresh. You should then find that the padlock symbols have gone, then you can do what you wish.
I did boot with the live cd... I just opened it up from ubuntu to get a screenshot.

---

### Post by Elfy on 2010-07-18
OK - then check if there are padlocks against any partitions - not used gparted as a livecd for a while so not completely sure if it uses the swap or not.

---

### Post by dylan_m on 2010-07-18
> **forestpiskie said:**
> OK - then check if there are padlocks against any partitions - not used gparted as a livecd for a while so not completely sure if it uses the swap or not.

nope, not a single padlock in sight. haha. 

i dont see why it doesnt let you do it.. stupid program.

---

### Post by Elfy on 2010-07-18
Boot the ubuntu livecd instead - it has gparted in the system admin menu. Do a screenshot from in there. 

Though it could be that you are trying to do it the wrong way. You know that each partition to the right of the unallocated space has to be moved before you can expand sda3?

---

### Post by da burger on 2010-07-18
I don't understand partitioning that well but if I remember correctly what your trying to do is a bit more difficult than most partition operations. The partition can't just be moved there like a normal partition move, it has to be copied byte by byte to the new location because you are "jumping" over the other partitions. (I believe it is still possible, just explaining why it is difficult)

---

### Post by dylan_m on 2010-07-18
Okay :)

I'll try the above and get back to you.

---

### Post by Mark Phelps on 2010-07-18
Maybe I'm misunderstanding what you want to do, but you can't "move" the 39GB of unallocated space at the beginning of your drive into the sda3 partition at the end of your drive.

You would first have to "move" the other partitions to the left such that the unallocated space was adjacent to the sda3 partition.  You can't drag-and-drop partitions to anywhere you want on the drive.

---

### Post by dylan_m on 2010-07-18
Yes im aware of that. But the program *wont* let me move partitions to the left, thats all..

---

