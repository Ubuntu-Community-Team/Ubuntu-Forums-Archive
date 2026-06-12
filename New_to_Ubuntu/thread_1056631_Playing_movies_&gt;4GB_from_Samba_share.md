---
title: "Playing movies &gt;4GB from Samba share"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by dacium on 2009-01-31
Hi, 
When I try to play movies of greater than 4GB from a mounted samba share that is sharing from a winxp computer, all of the media players i have tried 'wrap around' back the begining when they pass the 4gb mark.

I have tried the default player with ubuntu and also VLC and mplayer, they all reach the 4GB mark in the movie and start again. 

My movies files are recorded free to air getting recorded on the samba mount by another PC. They are HD TV and can be upto 30-40GB. If I copy the file to the local disk then it seems I can watch them, but this means I can't watch anything live. 

I am guessing samba is limited to 4GB or something? Anyone know how to get around this at all?

---

### Post by handydan918 on 2009-02-01
Dunno, but why samba? What kind of file system is the movie database on? It may be a filesystem issue...

---

### Post by dacium on 2009-02-01
ok im a bit of a noob,

I have a winxp box with NTFS harddisk. it has a shared folder that has movies that typically end up being 30GB. On other XP boxes they play fine using VLC etc.

On ubuntu I mounted it by using smbmount or just browsed to it by going places -> network -> etc. Both ways have the same effect, where once the 4GB position in the movie is reach, the player starts over at the beginning of the movie.

---

### Post by HotShotDJ on 2009-02-01
> **dacium said:**
> On ubuntu I mounted it by using smbmount or just browsed to it by going places -> network -> etc. Both ways have the same effect, where once the 4GB position in the movie is reach, the player starts over at the beginning of the movie.You need to use the lfs option... something like this:```
smbmount //Hostname/Username /local/mountpoint -o username=username,password=password,lfs
```I don't have much experience with this, so you may need to google if you need something more detailed.

---

### Post by dacium on 2009-02-01
I tried to to mount smbfs with the -o lfs option, but I get exactally the same result. Infact that seemed to make it so 2GB was the limit 
:-(

---

