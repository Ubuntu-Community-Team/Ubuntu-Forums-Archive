---
title: "Dual boot install w/Win7- geek style or Wubi?"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by rfbeck on 2010-02-21
My homie here is warning me about installing Ubuntu dual boot with Win7 (already installed). He says I *need* to do it Wubi style. I want to do it geek style with it's own partition and ext4 and the like. I mean, is that doable? Or am I in for a challenge? I've done it with XP, so it's not like I am a total partition virgin or anything.
______
Robert

---

### Post by sandyd on 2010-02-21
> **rfbeck said:**
> My homie here is warning me about installing Ubuntu dual boot with Win7 (already installed). He says I *need* to do it Wubi style. I want to do it geek style with it's own partition and ext4 and the like. I mean, is that doable? Or am I in for a challenge? I've done it with XP, so it's not like I am a total partition virgin or anything.
______
Robert
In a sense, your friend is right, and wrong.
Hes right, if you dont know how to use the windows 7 partition manager, cause windows will not startup properly if you resize the windows partition manager with the ubuntu installer.

Howeever, he is wrong.... if you follow the steps below.
squish windows 7 using the windows 7 partition manager.
Then when partitoning ubuntu, select the option "use largest contineous block of free space".

HINT: defragging will result in a larger "squishable" space.

---

### Post by rfbeck on 2010-02-21
Good lookin' out. Thanks.

---

### Post by presence1960 on 2010-02-21
Either way will work, but as carlee suggested if you install ubuntu to a dedicated partition be safe rather than sorry and use windows disk management utility to shrink windows partition to create unallocated space for ubuntu. Then use the ubuntu installer to either install to that unallocated space by choosing "use largest continuous free space" or "manual" to create custom partitions  from that unallocated space to install ubuntu onto.

My personal belief is that what you call "geek style" is the only way to go, but each person must decide for themselves whether to do a real install or wubi.

---

### Post by sandyd on 2010-02-21
> **rfbeck said:**
> Good lookin' out. Thanks.
Your welcome.

> **carlee said:**
> In a sense, your friend is right, and wrong.
Hes right, if you dont know how to use the windows 7 partition manager, cause windows will not startup properly if you **resize the windows partition manager** with the ubuntu installer.

Howeever, he is wrong.... if you follow the steps below.
squish windows 7 using the windows 7 partition manager.
Then when partitoning ubuntu, select the option "use largest contineous block of free space".

HINT: defragging will result in a larger "squishable" space.
oops
I think I typed a bit too fast there.
:lolflag:

---

### Post by vlamnire on 2010-02-21
Go to Start then right click on Computer then click Manage after that you'll get a new window opened.  Double click on Computer Management (Local) then double click on Storage.  After that find your Windows partition and right click on it then click Shrink change the size to what you want (You may get an issue of only being able to shrink a few MB if you get this just say it).  You will then have to wait a bit when shrinking.  You will get a new partition that says Unallocated which will be colored gray.  After that then boot from the Ubuntu CD and install it selecting the first option when getting the colored bars for partitions.

---

