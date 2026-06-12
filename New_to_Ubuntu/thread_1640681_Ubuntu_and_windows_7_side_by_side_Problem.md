---
title: "Ubuntu and windows 7 side by side Problem"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by speed86 on 2010-12-08
HI,

When I try to install Ubuntu 10.10 along side windows 7 I don't get that option on install,

At first I thought it was a space issue so shrank my D (has plenty of free space) and didn't see it on manual install or the side by side option didn't appear as well.
(only the same 4 partitions always appear)

I thought it was a problem with the windows boot but when trying to install Ubuntu 9.04 it says Windows vista boot detected (I have win7) but as well no side by side option.

What should I do even if I install ubuntu on windows there is always a fault so which doesn't allow me later on to access hardware to activate wireless because that part of the install failed or something.

Everything works fine on trial though............

Please Help

---

### Post by Rubi1200 on 2010-12-08
Hi and welcome to the forums :)

There have been changes to the installer for 10.10 and the side-by-side option is no longer available.

See here for more information:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by arubislander on 2010-12-08
> **speed86 said:**
> At first I thought it was a space issue so shrank my D (has plenty of free space) and didn't see it on manual install or the side by side option didn't appear as well.
(only the same 4 partitions always appear)

Are those 4 partitions by any chance all primary partitions? In that case you will not be able to install Ubuntu anywhere on that drive without deleting one of the partitions.

---

### Post by speed86 on 2010-12-08
Yes they all are primary, so if I go to Disk management and delete one of parameters completely I should be able to find free space to install Ubuntu on?

---

### Post by rvchari on 2010-12-08
hey guys, m joining this topic to replenish my knowledge...
if one partition is deleted and ubuntu made to install there, wont it get transfered to logical partition ? somewhere someone had told me that 2 diff OS can reside on primary partition side by side, is that true ? (years back i had win98 and win2k on same partition... but unix and ms ? will that b possible ? i have a doubt.

last but not the least, i hav win7 on primary c and 10.10 on logical (or extended?)
i had lucid earlier which i directly upgraded to maverick without having to download iso and install seperately....
grub also works fine ...

---

### Post by Quackers on 2010-12-08
In the MBR partitioning system there is a maximum permissible number of Primary partitions. That maximum is 4. If you already have 4 primary partitions and you wish to install another operating system (or just create another partition) you must delete one of the primary partitions then create an extended partition in its place. This new extended partition can have as many logical partitions within it as you like (well nearly).
If 4 primary partitions exist in a Windows 7 system (as some machines have from new) and you try to create a fifth partition without deleting a partition, Windows will change your primary partitions to Dynamic partitions!!!! This is not good news, especially for Linux users.
Please beware!

---

### Post by wheelyfeet on 2010-12-08
I'm having this problem so am jumping in on this thread. My HP Mini 210 came with 4 partitions. Three are labeled volumes and the fourth is unlabeled.  It's tiny and cannot be explored.  I am hesitant to just delete a partition not knowing if it is necessary for something. My mini came with Splashtop (which I had to disable in BIOS in order for Ubuntu to load) and I wonder if that is where it resides. 

One idea I have is to move drive E contents to a USB drive (HP tools), but I'll need to find out if I can and if they'll run from a stick.  OR should I run a boot info script as suggested in another thread I saw regarding this problem and have someone more computer literate look at it?

I am a COMPLETE Linux novice and since the days of MS DOS haven't really bothered to learn much about computers, so please speak very S L O W L Y and use small words!  Thanks! 

Debra

---

### Post by Quackers on 2010-12-08
wheelyfeet, it may be better if you start a new thread so that this one can be left to the OP. If you create a new thread just copy/paste what you have written above. Could you also include a screenshot of your Windows Disk Management screen (Start > right-click Computer > select Manage > in the new screen select Disk Management). Thanks.

---

### Post by Mark Phelps on 2010-12-08
rvchari: Please don't hijack this thread with your own list of questions.  It's hard enough to help someone without others trying to take over their threads.  Start your own thread for your questions.

---

### Post by wheelyfeet on 2010-12-08
Okay, I started a new thread. Hope it might help speed86 as well.  Deb

---

