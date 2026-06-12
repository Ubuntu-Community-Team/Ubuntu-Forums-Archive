---
title: "Mp3 Player is read-only?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by nyxm on 2010-06-06
I am trying to move files to my mp3 player, but  when I try it says error copying file, opening file,read only system.  When I try to change the permissions, it says error setting permissions,  read only file system. I am using Ubuntu 10.04 on a Compaq Presario CQ60, if that helps. What can I do?

---

### Post by ajgreeny on 2010-06-06
How did you mount the mp3 player, did it automount when you connected it, or have you made a folder for it and mounted it with a **sudo mount** command?

---

### Post by schtufbox on 2010-06-06
I had the same problem. The only way I could fix it was to plug the mp3 player into my laptop which still runs windows (as it's a work laptop and I don't get to choose the OS)  from there I did the following:

Open a command prompt, type the following

```
f: (F: being the mp3 player..replace with whatever drive your mp3 player is..)
```
press return

```

chkdsk /f

```

It will ask you if you want to unmount the drive to check it, say yes, let chkdsk do it's thing then the drive should  be useable in Linux again.
Sometimes a process may be using the mp3 player (windows media etc, in which case schedule the check for a restart, then restart :P


If anyone has a purely Linux fix, I would love it as this is clunky and useless if you don't have any windows installed anywhere be it a pc or a virtual machine...

Hope this helps.

---

### Post by schtufbox on 2010-06-06
> **ajgreeny said:**
> How did you mount the mp3 player, did it automount when you connected it, or have you made a folder for it and mounted it with a **sudo mount** command?
When I had this issue it was when automounting.  It worked fine at first, then for no apparent reason it started mounting the drive as read only.  A forum search/google search yielded the method I posted above  as a fix, not found any other fixes yet.  Mind you since I did the chkdsk method, I have not needed to do it again.

---

### Post by nyxm on 2010-06-06
well, windows is out of the picture for me. apparently i had a fake copy and got tired of the "get genuine" message. I have used Ubuntu before and was pleased but was still dependent on some windows programs. Now that all I have is Ubuntu, my mp3 player won't work. It was auto mounting, I guess. I plug it in and it shows up in places as a 3.8GB file system. It has a microSD card in it that shows up separately and I can actually use, but the card is only 1GB and not really for the mp3 player. I took it out of my phone to see if I could use it and so far that is the only Linux fix I've found.

---

### Post by schtufbox on 2010-06-07
Well I am sure there must be a linux only method too, I just do not know it yet.  It would be useful as I may be changing jobs soon and will have no requirement for a windows machine :)

---

### Post by nyxm on 2010-06-07
I was thinking. Is there a way to use Wine to change the way the player is viewed? Or some kind of file manager for Windows that works with Wine to use? Just wondering because I have never had any problems with this player when I was using Microsoft.

---

### Post by nyxm on 2010-06-09
I finally got it working. I just had to format the internal memory and now it's running like a tune.

---

### Post by Chronon on 2010-06-09
Unmount the player, then use
```
fsck.vfat -a /dev/sdc1
```
to check and repair a FAT32 file system in the first partition of /dev/sdc.  Change the device path as appropriate to your player.

---

### Post by schtufbox on 2010-06-15
> **Chronon said:**
> Unmount the player, then use
```
fsck.vfat -a /dev/sdc1
```
to check and repair a FAT32 file system in the first partition of /dev/sdc.  Change the device path as appropriate to your player.
Thanks, that will save me using the work laptop if this happens again :D

---

### Post by felipe_crimson on 2010-10-18
You should try mount the device yourself...

like this:

create a directory:

> mkdir ~/mp3

and then, mount the mp3-player.
note: /dev/YourDevice... here, my mp3-player is in /sdc

> sudo mount /dev/sdc ~/mp3


and finally, remove and write in yout mp3-player
using sudo. that works for me.

---

