---
title: "Blobwars no sound"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by winsane on 2009-04-25
I am not getting any sound in either Blobwars game.  I installed the SDL modules and I think I installed the correct zlib mod.  Is there something I need to configure? My sound works normally otherwise.

---

### Post by lukjad on 2009-04-27
Try checking the settings. When you are in the game, hit escape and poke around in there. Also, as a bonus for being so patient, type "lockandload" and notice what happens... ;)

---

### Post by winsane on 2009-04-29
Tried that right off the bat.  Played music and video from youtube and usb drive.  No joy. I downloaded SDL but am I supposed to do something after synaptic installs it?

---

### Post by winsane on 2009-04-29
To clarify, Youtube and USB thumbdrive had no problems but only Blob Wars seems to have a sound problem.

---

### Post by Psy[H[] on 2009-10-13
Karmic brings no changes. It seems that something wrong with ubuntu packages. Use official debs from [www.parallelrealities.co.uk](www.parallelrealities.co.uk). Sound is working in both blobwars and blobandconquer.

---

### Post by Mike3 on 2010-04-06
The problem, as I have read up is not related to ALSA. By default, Blobwars has no sound in the Ubuntu or Debian packages because the sound is nonfree. However, the official packages from Parallel Realities has the sound built in. You must then download the official packages if you want sound. This means you should enter the following in a terminal:
 
```
sudo apt-get purge blobwars blobwars-data

wget http://www.parallelrealities.co.uk/download/blobwars/blobwars-1.17-1.i386.deb
```

Then, go to your home folder, double click the Blobwars DEB, and install. This should fix your problems, even though the answer is about a year late. I just thought that I should write out a guide and explanation, even though the answer was described above.

---

### Post by arjang60 on 2010-05-29
Well I am glad you replied to this post a year later, because today I had the same problem. 

Your solutions works great

Thanks a lot

Arjan

---

### Post by Xcursion666 on 2010-12-06
> **Mike3 said:**
> The problem, as I have read up is not related to ALSA. By default, Blobwars has no sound in the Ubuntu or Debian packages because the sound is nonfree. However, the official packages from Parallel Realities has the sound built in. You must then download the official packages if you want sound. This means you should enter the following in a terminal:
 
```
sudo apt-get purge blobwars blobwars-data

wget http://www.parallelrealities.co.uk/download/blobwars/blobwars-1.17-1.i386.deb
```Then, go to your home folder, double click the Blobwars DEB, and install. This should fix your problems, even though the answer is about a year late. I just thought that I should write out a guide and explanation, even though the answer was described above.
thanks for the help i was having the same problem on my desktop and my netbook

---

### Post by KirkS on 2012-05-23
> **Mike3 said:**
> The problem, as I have read up is not related to ALSA. By default, Blobwars has no sound in the Ubuntu or Debian packages because the sound is nonfree. However, the official packages from Parallel Realities has the sound built in. You must then download the official packages if you want sound. This means you should enter the following in a terminal:
 
```
sudo apt-get purge blobwars blobwars-data

wget http://www.parallelrealities.co.uk/download/blobwars/blobwars-1.17-1.i386.deb
```Then, go to your home folder, double click the Blobwars DEB, and install. This should fix your problems, even though the answer is about a year late. I just thought that I should write out a guide and explanation, even though the answer was described above.

That fix evidently doesn't work anymore.  The first Terminal command took the game off my system, and the second got a return of "404 Not Found".  I have now lost everything I had gained, and will have to start from the beginning.  Kind of irritating.  :confused:

---

### Post by oldos2er on 2012-05-23
Old thread closed.

---

