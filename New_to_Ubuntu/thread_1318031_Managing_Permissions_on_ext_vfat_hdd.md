---
title: "Managing Permissions on ext vfat hdd"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by webwiller on 2009-11-07
Hi all and thx in advance for your kind help I get all times I get stuck with my new experience with ubuntu, something as much similar to a nice chick I ever seen from years!!! XD :D

Back to the point.

I bought an external media-box, with its hdd and the possibility to watch my movies straight on TV without any PC's stuff. Glam  you'd say! 'n it is indeed...but I'm experiencing some troubles with permission on my movies. I created directories and sub-dir and messed-up around as normal.

At one stage I was not able to delete or move or copy/paste my movies to/from my media box. I found-out it has something to do with the fact that I'm managing it (a vfat partition) from ubuntu.

Have you any clue about an easy solution? I'd go for a less easier too!!!! XD!!!!

ThX in AdV;)

---

### Post by ajgreeny on 2009-11-07
vfat does not recognise linux permissions in any way, so that can not be the problem in itself, but the mount point of the vfat disk may need some permissions tweaking.

---

### Post by webwiller on 2009-11-07
So? How do I check the vfat mount point "needs" and solve them?

---

### Post by coffeecat on 2009-11-07
How are you connecting the media-box to your Ubuntu computer? How are you mounting it?

If it is a USB connection and you let it be automounted, you will get **no** permissions problems. Period.

---

### Post by webwiller on 2009-11-08
It's USB connected and mounts automatically. In fact I did not have any problem till few days ago, when I started getting messages saying I could not delete or copy/paste my videos from here to there. I checked file permissions and noticed that some files (I can move) belong to myself, and some other one are owned by root, and I cannot mess around with em..

---

