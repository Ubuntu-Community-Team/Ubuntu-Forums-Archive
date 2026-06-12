---
title: "Are there any MP3 players that support ogg format?"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by maryalesia on 2011-01-10
Because my PSP def doesn't, which is just plain irritating.

---

### Post by Habeouscorpus on 2011-01-10
Rhythmbox. It's included with Ubuntu.

---

### Post by TeoBigusGeekus on 2011-01-10
> **Habeouscorpus said:**
> Rhythmbox. It's included with Ubuntu.

I believe he meant portable ones.

---

### Post by bluelamp999 on 2011-01-10
I installed Rockbox on my iPad a while back and it handles Ogg and FLAC.

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by bluelamp999 on 2011-01-10
I installed Rockbox on my iPod a while back and it handles Ogg and FLAC.

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by maryalesia on 2011-01-10
> **bluelamp999 said:**
> I installed Rockbox on my iPod a while back and it handles Ogg and FLAC.

[http://www.rockbox.org/](http://www.rockbox.org/)

I tried downloading the utility and I can't get it to open. I made sure the permissions allowed it to run as an executable and everything. :confused:

---

### Post by maryalesia on 2011-01-10
> **bluelamp999 said:**
> I installed Rockbox on my iPod a while back and it handles Ogg and FLAC.

[http://www.rockbox.org/](http://www.rockbox.org/)

Okay I got the utility to run, but when I first open the application it tells me:


Your configuration is invalid. This is most likely due to a changed device path. The configuration dialog will now open to allow you to correct the problem

I click "OK", and I am asked to 1. select your device in the file system, and 2. select your audio player. 

Um. What?

---

### Post by bluelamp999 on 2011-01-10
> **maryalesia said:**
> Okay I got the utility to run, but when I first open the application it tells me:


Your configuration is invalid. This is most likely due to a changed device path. The configuration dialog will now open to allow you to correct the problem

I click "OK", and I am asked to 1. select your device in the file system, and 2. select your audio player. 

Um. What?

Hi. It's been ages since I installed it on my iPod so all I can suggest is to read the documentation on the Rockbox site...

If you're trying to install it on a PSP I don't think that will work. Again, check the Rockbox site for the list of devices it supports...

If you're just looking for a portable MP3 player that supports Ogg, I'd suggest a quick Google.

Good luck...

---

### Post by baddnady23 on 2011-01-10
make a mount point in /media such as ```
sudo mkdir /media/ipod 
```
and when you open the utility, you will need to manually point it to the mount point.

---

### Post by ufugu on 2011-01-10
Yes, Rockbox on an iPod is the way to go.  But it will only work on an older iPod (iPod Video 5.5G or older).

If you are having trouble installing Rockbox on your player, please read the documentation on their site. It is very simple to install, but you will get much more out of it if you take a few minutes to read up on it.

I believe the currenly popular Sanza Clip and all of the Archos line are safe bets for OGG out-of-the-box as well.

---

### Post by ScottyD135 on 2011-01-10
I have a Sansa Clip+ and can confirm that the player does, in fact, support OGG.

Good luck!

---

### Post by maryalesia on 2011-01-10
> **baddnady23 said:**
> make a mount point in /media such as ```
sudo mkdir /media/ipod 
```
and when you open the utility, you will need to manually point it to the mount point.

Thanks for the tip! I'll get on that right away. :-)

> **ufugu said:**
> Yes, Rockbox on an iPod is the way to go.  But it will only work on an older iPod (iPod Video 5.5G or older).

If you are having trouble installing Rockbox on your player, please read the documentation on their site. It is very simple to install, but you will get much more out of it if you take a few minutes to read up on it.

I believe the currenly popular Sanza Clip and all of the Archos line are safe bets for OGG out-of-the-box as well.

> **ScottyD135 said:**
> I have a Sansa Clip+ and can confirm that the player does, in fact, support OGG.

Good luck!

I'm putting it on a first gen nano just for fun, but I think I'm getting a sansa clip because my nano only has 2 gigs. Sandisk mp3 players are awesome just for the fact that they have SD card slots. :D

---

### Post by maryalesia on 2011-01-10
> **baddnady23 said:**
> make a mount point in /media such as ```
sudo mkdir /media/ipod 
```
and when you open the utility, you will need to manually point it to the mount point.

OK so I did what you said, but it still has an error message pop up saying that "mount point is not writable". When I plug in my iPod, another mount point comes up under media with a bunch of letters and numbers for a name. That's not writable either, but I'm pretty sure it's my nano.

Thoughts?

---

### Post by baddnady23 on 2011-01-10
unmount the ipod, then try using the terminal, manaully mount it to the /media/ipod folder.  I actually just put rockbox on my 4th gen ipod the other day and had to do this very thing to get it to work for me.

---

### Post by maryalesia on 2011-01-10
> **baddnady23 said:**
> unmount the ipod, then try using the terminal, manaully mount it to the /media/ipod folder.  I actually just put rockbox on my 4th gen ipod the other day and had to do this very thing to get it to work for me.

how do I unmount it and then manually mount it?

---

### Post by maryalesia on 2011-01-10
I plugged my iPod into a windows PC and reformatted the discs to FAT32, which got me past the "mountpoint is unwritable" problem. However, now when I go to install it says above the progress bar "could not open iPod: permission denied." 

?????

---

### Post by srs5694 on 2011-01-10
The music player app in Android-based cellphones plays Ogg files. (At least, that's true of my Samsung Intercept.)

---

### Post by maryalesia on 2011-01-10
[http://ubuntuforums.org/showthread.php?p=10342045#post10342045](http://ubuntuforums.org/showthread.php?p=10342045#post10342045)

That's the new thread I created dedicated to my rockbox problems. :)

---

### Post by baddnady23 on 2011-01-11
> **maryalesia said:**
> how do I unmount it and then manually mount it?

Well you don't have to unmount it, you could just point the rockbox utility to whatever directory it is mounted in automatically.  It too is going to be located in the /media folder.  Manually mounting it to /media/ipod just might make it easier for you to recognize if you have multiple things that are mounted under /media.

---

### Post by freak42 on 2011-01-11
both my hints are a bit off(topic) but hopefully still helpful:

- Android phones can be used as ogg audio players.

- The Ubuntu Banshee (iTunes Clone) Ubuntu Music player can convert music on the fly while exporting it to a HW mediaplayer. In my setup Banshee converts everything to .ogg when I sync my Android Phone and everything to mp3 when I sync my iPod.

hth

---

