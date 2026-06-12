---
title: "Newbie, Dual-booting, Partitioning?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by zepl on 2009-07-09
Alright, I want to try ubuntu studio, I've never used any linux distro before, it seems complicated/or people make it out to be. I know how to burn the iso's, and ive read how to install it but I would like to dualboot with windows xp. I've read around google a few times but most threads I have found were for older releases so I'm not sure if they still apply. 
Anyways, I found a post earlier that says you could just install ubuntu, and type osmething in and it will download and install unbuntustudio, should i go for that? 
and if i did, how would i set up a dualboot, the walkthrough setup said that when it asked if you wanted to partition your drive it asked for whole drive, then whole drive guided?
idk, from there im lost, im backing up all my files right now, and i dont mind installing win xp again if i screw something up.
But does anyone wanna hold my hand through this? lol

---

### Post by philcamlin on 2009-07-09
to dualboot you just boot into the cd and chosse install side by side 

and it will automatically install without and issues :)

correct me if im trying to do the wrong thing i think i know what you mean :D

---

### Post by mevets on 2009-07-09
You might be refering to wubi..? Wubi runs inside windows and installs ubuntu in a nondistructive way. Its not ubuntu studio, but anyone of the programs included in studio you could just install yourself.

Try [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by philcamlin on 2009-07-09
> **mevets said:**
> You might be refering to wubi..? Wubi runs inside windows and installs ubuntu in a nondistructive way. Its not ubuntu studio, but anyone of the programs included in studio you could just install yourself.

Try [http://wubi-installer.org/](http://wubi-installer.org/)

wubi is allright but its really slow and i wouldent use it because it runs on a virtual filesystem with is slow 

installing side by side is better or full install on the hdd :popcorn:

---

### Post by zepl on 2009-07-09
yes, that is what i was reffering to, the side by side thing
another question, if i left my files on the windows partition, would i be able to grab them when running ubuntu? or would i need to make another partition / drive to acces them

---

### Post by mevets on 2009-07-09
nah ubuntu should automaticcaly recognize your windows partition and use ntfs-3g to allow you to read and write to it.

---

### Post by Elep.Repu on 2009-07-09
Realize that it will be hard to switch back over if you so desire to.
I'd suggest having your windows disk on hand.
Play more with the live disk to see if you're ready. (Check sound!)

---

### Post by Ranko95 on 2009-07-09
I was scared at first too so I used wubi. You may want to Start there you can access you windows files and it intalls inside windows like a program. I would recommend doing a real install. It's a pain to move all the files when u decide u want a real install, which u probably will. Don't try to do any partition editing yourself yet. I have screwed up grub countless times before and you don't want to go there

---

### Post by mevets on 2009-07-09
Yes wubi is a good temporary solution. Once you get used to things and want to move onto the real thing then you can just remove it from the add/remove menu from windows.

---

