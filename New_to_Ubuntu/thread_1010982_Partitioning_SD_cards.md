---
title: "Partitioning SD cards"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by goame on 2008-12-14
I'm trying to partition a few SD cards using gparted, the problem is they don't show up as devices in the program.  What is the proper way to create tables and partitions using a terminal?

---

### Post by jay li on 2008-12-14
I think you don't need that, just unmount them first through gparted.

---

### Post by goame on 2008-12-14
I can't even select them through gparted.  They just don't show up.  The read only locks are also off and only one of them automounts upon insertion.  The only way I can access the other is through creating a truecrypt device and mounting that.

---

### Post by jay li on 2008-12-14
When you mark the sd card then right click and perform unmount, what happen?

---

### Post by goame on 2008-12-14
I can't do that.  Any SD card I put in my computer cannot be recognized by gparted.  I can't even get to the step where I could unmount them because I can't even select them.  They don't show up in the "devices" section.

---

### Post by jay li on 2008-12-14
Did you try usb drive instead of sd card?

---

### Post by goame on 2008-12-14
My USB drives all seem to work with gparted, but I really would prefer to use SD and MicroSD.  I know it's worked for other people.

---

### Post by jay li on 2008-12-14
I know, my ubuntu itself is runing from SD card. 
So in that case I think maybe there is a problem with the adaptor you using. 
Therefore I suggest you try another one to see if it's solve the problem

---

### Post by Kellemora on 2008-12-14
Hi G

Do you have a camera, PDA or GPS or something you can use to place a folder onto the SD card to get you started?

I had the same problem!  A new blank SD card is not seen at all!

But if I put a folder on it, then it mounts.
AFTER it mounts then gparted should see it and you can unmount it and the data regarding the SD card stays on the screen then for you to manipulate it.

If that don't work then I don't know what else to try.

TTUL
Gary

---

