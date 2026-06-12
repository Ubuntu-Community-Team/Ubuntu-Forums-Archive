---
title: "cant figure out how to boot into linux from windows."
date: 2009-07-24
forum: New to Ubuntu
---

### Post by centennial on 2009-07-24
STUPID question, I know, but I cant seem to figure it out. 
For a while, I've been running linux on a small partition with a ton of free space on my HD, intending to eventually install another OS. Finally, I did (the windows 7 RTM), but now I cant find how to boot back to linux! Before, when I booted up, it would ask me which partition to boot before running any OS. Now, it just boots straight to windows. I'm sure there's a quick way to get back to that screen (holding F4 or something like that) but I just cant figure it out. 

I already tried going into system and changing the "default" OS, but it wont even recognize ubuntu--windows 7 is the only choice. 

I'm running ubuntu 9.04 on a sony vaio.

Any help would be appreciated :)

---

### Post by cariboo on 2009-07-24
Have a look at this [howto]("http://ubuntuforums.org/showthread.php?t=224351"), it should solve your problem.

---

### Post by Mark Phelps on 2009-07-25
> **centennial said:**
> 
I already tried going into system and changing the "default" OS, but it wont even recognize ubuntu--windows 7 is the only choice. 


Sounds like you were using MS Windows boot loader to select your OS. So, did you have Vista or XP installed earlier and overwrote it with Seven?

Cariboo's suggestion will install GRUB and allow you to select Ubuntu or Seven from a GRUB menu, not from an MS Windows boot loader menu.

---

