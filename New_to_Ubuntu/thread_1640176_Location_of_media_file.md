---
title: "Location of media file"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by prmdk on 2010-12-07
Hey Guys,
I installed gnome-mplayer to play apple movie trailers. Now when i clicked on the download trailer link. 
The gnome-mplayer was launched and started playing the trailer. 
So the problem that i have is how to know the know the location of the video file that mplayer is currently playing.

I have tried virtually every tool in the mplayer menu bar
Searched the file (via type and name separately) using ubuntu search tool.

But i am not able to find it.

Thanks in advance guys...

:eek:

---

### Post by cariboo on 2010-12-07
Have you look in /tmp? That is usually where downloaded videos are buffered.

---

### Post by prmdk on 2010-12-08
Yes,
But its not there...
:(

---

### Post by rburkartjo on 2010-12-08
prm go to terminal type locate then space. and if you know the file name or the type of file you should get an output. might help

---

### Post by prmdk on 2010-12-08
I tried
sudo locate *.mov

and 

sudo locate *tron*

Got nothing...:(

---

### Post by rburkartjo on 2010-12-08
prm maybe this link will help

[https://help.ubuntu.com/community/FindingFiles](https://help.ubuntu.com/community/FindingFiles)

---

