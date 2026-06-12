---
title: "Cant See Some Media Files"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by phiednate on 2009-01-04
Did a quick search and couldn't find the solution so I registered to ask the question. I am completely new to Ubuntu but recently purchased an eee PC and after seeing a friends which he had ubuntu loaded on I decided to wipe the drive of XP and install it. As I will be taking this machine on my long flight tomorrow I wanted to load some of my music and movies from my XP machine and put em on the ubuntu system. I copied them onto a sasa fuse I had, got it all connected but I cant see any of the media files. I can see a few random files on there and all of the folders but no media files.

Am I doing something wrong?:confused:

---

### Post by beastrace91 on 2009-01-04
Can your windows/non ubuntu PC see the files?

~Jeff

---

### Post by phiednate on 2009-01-04
Yea the other system is running windows xp and can see them no problem.

---

### Post by SuperSonic4 on 2009-01-04
What if you do ```
ls /media/[COLOR="Red"]X[/COLOR]\GB\Media
``` where X\GB\Media is the path to your device.

If it is called "fundisk" and you want to copy to a currently nonexistant folder ("~/media") then try (one at a time) ```
mkdir ~/media
cp -Rvf /media/fundisk ~/media
```

Edit /media/fundisk to the directory you wish to copy files from

cp: copy
-R : recursive, got into folders and copy
-v : verbose, tells you what it's doing
-f : force, does not ask for confirmation

mv (move) can be used too if you don't need the originals

---

