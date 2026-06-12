---
title: "Help! Dual booting windows 7"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by urbackdoor on 2009-05-17
Okay, I have two hds one windows xp (or used to be) and one ubuntu. Today I completely wiped my xp and installed windows 7. Before that I could dual boot. But now it no longer gives me the choice. I'm not sure how to get back in to my ubuntu :(
 
Also, I looked up guides and stuff, but as I read them I only understood them to be installing ubuntu brand new, and thats not what I want :P
(Windows also does not recognize my ubuntu drive)

---

### Post by Sunfist on 2009-05-17
I am thinking that most likely Grub was overwritten when you installed windows 7. You will need to reinstall grub to get to the point where you can once again run either OS. I am not familiar with Win7 so hopefully someone here can point you in the right direction to reinstall grub. I remember a program I used once called SuperGrub to help me out of a similar situation when I some how overwrote grub, not sure if it works with Win7 thou.

---

### Post by mfmbcpman on 2009-05-17
[http://lmgtfy.com/?q=restore+grub+after+windows+installation]("http://lmgtfy.com/?q=restore+grub+after+windows+installation")

---

### Post by Joeb454 on 2009-05-17
This is a relatively easy fix :)

I followed this guide when I had to recover my dual boot

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Terry of Astoria on 2009-05-17
[You could try this link here (click me)]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+reinstall+can%27t+boot+ubuntu")
@ mfmbcpman: Thanks for the link . . . very intelligent suggestion. You are obviously very astute.
   @ urbackdoor: An interesting tool is Smart Boot Manager. - [http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)
- I see it's in the repositories, too . . . .

---

### Post by walker9010 on 2009-05-17
A lot of people have given you information about how to restore grub...follow any of the links. I just installed Windows 7 as well, and followed [this ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")through step 5. No problem, and grub detected Win 7.

In order to get Win 7 to detect your ubuntu drive, assuming you formatted your ubuntu drive to ext3 (or something else in the ext range) you will need to download and install a driver so windows will read the file system. A nice guide to the various options is available [here]("http://www.howtoforge.com/access-linux-partitions-from-windows"). Personally, I used [this]("http://www.fs-driver.org/").

Hope that solves all your problems!

---

### Post by urbackdoor on 2009-05-17
Thanks everyone for your responses! I can dual boot now :) I guess the silly thing that threw me off was getting back into ubuntu to change grub...I guess that part only makes sense in my head, but anyway, thanks for dealing with me...as you can tell I'm a total newbie at this @.@

---

### Post by Joeb454 on 2009-05-17
Everybody has to start somewhere :)

Glad you've got your dual boot back

---

