---
title: "Natty, Music, and Me - iPhone"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by ratant on 2011-07-07
First: I'm new to Linux and am not a programming wiz. I understand bits and pieces of how to use the terminal but nothing too substantial. I have recently switched from Vista to Ubuntu 11.04. So far I love it. 

 I have, however, one major dilemma that I can't get past for the life of me. I've been listening to music using Banshee 2.0, which works great. It's getting this music to a portable device that I need help with. I have a sn0wbreeze-jailbroken Iphone (4.2.8). 

 I've googled my pants off and searched plenty of forums all to receive only convoluted information, usually outdated. I realise I can't sync my music directly to the phone's Ipod app using any Linux program (as far as I know). 

 So my question is this: is there any music player app that I can download from cydia that will run as smoothly and in as organised a fashion as the default ipod app? One that will be compatible with Banshee or another Linux media player? If not, are there any alternative portable mp3 players that are known to connect well with Banshee?
 I just want the device on my desk and the device in my hand to agree, and I love my new operating system enough to ditch anything not compatible with it if there is a better alternative.

---

### Post by wolfen69 on 2011-07-07
> **ratant said:**
> I realise I can't sync my music directly to the phone's Ipod app using any Linux program (as far as I know). 


Some people can. I can sync my ipod touch using gtkpod. Do:
```
sudo apt-get install ifuse gtkpod
```
Let us know what happens.

---

### Post by ratant on 2011-07-07
Tried this, same thing happened as with banshee. Says it is syncing correctly and everything looks like it worked until I unmount my iphone and check the music. All the albums I told it to sync appear in the list but they all share the same album art and not one song works when I try to play it.

---

### Post by Pablo Pablovski on 2011-07-24
I've found that adding one other track (any), syncing agin, then deleting that track and re-sync'ing seems to fix that problem - it looks like the iPhone song database doesn't get updated until something is deleted from it. You may need to do the add / delete thing twice.

That said, adding songs has stopped working for me since I upgraded to Natty. Grrr..

---

