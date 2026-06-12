---
title: "Need help with scrollbar, taskbar, and mounting"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Winlinos on 2009-07-18
...all the kinks I have that I'd like to iron 'em out if I sought help. I've attached a few images to give you an idea what I`m talking about. 

First of all, the scroll bar is sort of a bit thin however (see image below), I know where the folder that I should go into to &quot;customize&quot; the size of the scroll bar according to one of the thread I found the other day. The problem is that I cannot change it due to permission. The scrollbar size may be normal but it's annoying when I have to grasp it to scroll it with the pointer.

Secondly, I made some changes to the taskbar, originally, there's two at the top and bottom of the screen. I decided to fiddle around a bit with it until I got a message saying that I'd lose the settings if I delete the top bar, the one with windows buttons with those were active and non-active programs in there. So, *poof* I went ahead with it that I figure I can get past that but I failed do so. How do I get the applications back in the taskbar?


[IMG]http://i179.photobucket.com/albums/w285/HighAway/ubuntuforums/UDT.png[/IMG]

And lastly, (for now!) one of the volume I wanted to mount has failed(see images below). The error message reads:
Failed to read last sector (329414592): invalid argument   
Perhaps the volume isa RAID/LDM but it wasn't setup yet, or
the wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sdb3'; Invalid argument The device '/dev/
sdb3' doesn't have a valid NTFS. Maybe you selected the 
wrong device? Ir the whole disk instead of a partition (e.g./
dev/hda, not /dev/hda1)? Or the other way around?

[IMG]http://i179.photobucket.com/albums/w285/HighAway/ubuntuforums/MountFailed.jpg[/IMG]

According to the Windows Computer Management (see image(CM.jpg)), I do not understand how the mount error is giving me problems as all look ok. To give a bit of a background. Disk 1 has three partition, and I moved files from E: to D: then I click on E: to extend it (forget how exactly what I did sorry). Which E: has become D: still having three partition. So I subsequently decided to format the D: partition to become one partition elimating the E: drive. Agian moved files back in there again. At that point, when I installed linux, it been like that. What do you think?

[IMG]http://i179.photobucket.com/albums/w285/HighAway/ubuntuforums/CM.jpg[/IMG]

I'm new at this and willing to learn and will attack it as much as I can to learn more!

*If you find those images too big, you can resize it to fit the thread.

Thanks in advance!

---

### Post by jerome1232 on 2009-07-18
As for your hard drive issue I think it's because it's a dynamic volume, I'm very sure only Microsoft can read dynamic volumes. They are similar to Linux LVM in that you can span multiple discs with a volume and such.

To see a list of open apps right click your panel, select add to panel, find window selector and add it.

---

### Post by Winlinos on 2009-07-18
jerome, actually it's the only volume that can't access to along the other volumes that are on dynamic still can be accessed.

But I'll try your advice whatever it takes... thanks man.

---

### Post by jerome1232 on 2009-07-18
> **Winlinos said:**
> jerome, actually it's the only volume that can't access to along the other volumes that are on dynamic still can be accessed.

But I'll try your advice whatever it takes... thanks man.

In that case I stand happily corrected, normally I'd say the FS is corrupted seeing that message but Windows is using it fine so.... hopefully someone who knows ntfs better than I stumbles along. Running Window chkdsk on it once couldn't hurt anything though I doubt it would help.

---

### Post by Winlinos on 2009-07-18
I'll work on that when I get the chance and post back after I'm done.

---

### Post by Winlinos on 2009-07-20
Well, g'morning Ubuntu'ers. I made my way around learning the OS more and more and still on it. Yet, there are issues that need to be resolved: the volume cannot mount. And the scrollbar is an annoyance. Anybody...?

---

### Post by /usr/sbin on 2009-07-20
Hello, i did a quick search on the forums and i found this post;

[http://ubuntuforums.org/showthread.php?t=255065](http://ubuntuforums.org/showthread.php?t=255065)

Hope it helps you change the scroll bar width

---

### Post by Winlinos on 2009-07-20
I'm workin on this so to speak but I'd have to be in root account to get this to work due to this directory /usr/share/themes/Crux permissions, right?

---

### Post by Winlinos on 2009-07-20
Ok never mind the previous post that I've got it changed and worked! Though, what about the stepper part? Not sure if I be able to put in the right format. anyone could tell me this? 

Thanks

---

### Post by Winlinos on 2009-07-21
Update: the scrollbar and the taskbar has been fixed. Unfortunately, one volume are yet needed to be resolved. Still calling out on yu'all to help me with this one. I tried searching the forum and the net to no avail. 

Still working on this and I don't really expect it to be cured.

---

