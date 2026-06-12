---
title: "play mp3 collection over home lan network (samba)"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by oasisforever on 2008-07-27
hello folks

since a year i'm using ubuntu with joy, but last week i had an idea and i couldn't fix it in Ubuntu (i'm using version 8.04). We have at home a few computers and some of them are windows so our network is Samba. In my room i have an ubuntu desktop with a huge collection of music, which i try to access (->view ánd play!) with an old laptop.

So my question is: how do i do this right? i tried several audio programs, a few of them don't recognise the samba folder, others does. But all these programs share the same disadvantage to be slow and asking much system resources (my laptop is an old pentium III). the music collection is about 45+GB of mp3 files.
I already tried to mount the samba music collection as a map (which was possible) and access this map with the program Amarok (which i use mostly for music playing). BUT also here: MUCH too slow, it takes way too long to load all the music in the library and sometimes it crashes.

Any ideas to help me out?
If there is no way to fix it with samba, i am willing to try a http server, but i don't want endless command line configuring, for many of you this is noob talk and maybe you are right. But i like a graphical solution for this..

thanks in advance for help, véry much!

Tom (Leuven, Belgium)

---

### Post by eldragon on 2008-07-27
if you already gotten to mounting the samba partition...say to /mnt/music_repo

and the old computer supposed to behave as a mp3 player has the username joe.

i use for this same purpose. rhythmbox. for this, i create a bind from the mount point to my music folder.

in fstab add the line
```

/mnt/music_repo /home/joe/Music/music_repo bind 0 0

```

when you start rhythmbox it will find all the music automatically (first do a mount -a)

i do a bind instead of mounting directly because i find it more elegant to have all my mounted filesystems inside /mnt and then bind different points to where i need them.

another useful hint, is to add a dynamic playlist based on path. this way you can have your music separated, in local and samba.


hope it helps.

---

### Post by oasisforever on 2008-07-27
hello dragon

in the meantime i already found another solution, but if you think yours is better i will change it..

I used DAAP as descriped on this website:
[http://ubuntu.wordpress.com/2006/09/22/share-music-in-a-network-using-avahi-daap/](http://ubuntu.wordpress.com/2006/09/22/share-music-in-a-network-using-avahi-daap/)

with the DAAP share plugin in rythmbox on my desktop, i could access this music in the rythmbox on the laptop, and it seems faster than samba..

---

