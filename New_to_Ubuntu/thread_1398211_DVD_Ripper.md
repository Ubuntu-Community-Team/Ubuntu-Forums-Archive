---
title: "DVD Ripper"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by mrapoc on 2010-02-04
Hey guys

i'm after a dvd ripper which actually works on ubuntu 9.10

looking to either rip at full quality DVD backup to either AVI or mkv (whichever is best quality/size ratio ya know).

Might just do a full quality rip and put all my dvds onto a 1tb drive.

So which program and what settings, also what size are we talking for a standard dvd, no menus just the film.

:popcorn: cheers

---

### Post by Grenage on 2010-02-04
Take a look at [handbrake]("http://handbrake.fr/downloads.php"), a lot people get on well with it.  I use it for re-encodes, but it can handle DVDs.

---

### Post by howefield on 2010-02-04
> **mrapoc said:**
> i'm after a dvd ripper which actually works on ubuntu 9.10

That suggests you have tried some that don't.

It'd be helpful to know which before making suggestions, but the one I use is Handbrake.

handbrake.fr

---

### Post by mrapoc on 2010-02-04
used to love dvd-rip 

seems to never work for me nowadays

also i think i tried handbrake but i could never get a good quality even with a 4gb file.

maybe ill try again, x264, mkv, what size would a full rip be and would it be worth it, unless i could turn down the settings for a slightly compressed rip while still having a good rip quality

---

### Post by SuperSonic4 on 2010-02-04
I use k9copy and/or handbrake.


If you want full quality just rip the entire DVD to an ISO. VLC can handle them

---

### Post by mrapoc on 2010-02-04
Welllll i did want it so i can use it on my Windows 7 boot as thats what I use most, and also so i can stream to my ps3 (i know avi and stuff works)

Unless I can mount the ISO in daemon tools and it will play like a normal dvd I dunnoo!

---

### Post by sxmaxchine on 2010-02-04
i use thoggen because it does what i want and is simple

---

### Post by SuperSonic4 on 2010-02-04
> **mrapoc said:**
> Welllll i did want it so i can use it on my Windows 7 boot as thats what I use most, and also so i can stream to my ps3 (i know avi and stuff works)

Unless I can mount the ISO in daemon tools and it will play like a normal dvd I dunnoo!

In theory yes because it would create an exact copy but since I have neither a PS3 nor Windows I cannot test it.

---

### Post by ushills on 2010-02-04
+1 for k9 copy and k9 copy assistant makes it easy.

---

### Post by mrapoc on 2010-02-04
can both do x264 avi/mkv?

guess ill have to try them out

---

### Post by Tholley on 2010-02-04
The only thing I have found that works for me, is DeVeDe to rip the dvd to ISO, then use K3b to burn to blank disc. (you can actually fit 2 full dvd movies onto 1 blank disc also)
 
I would imagine there is a way to convert an ISO image to avi if you really want to store them on a drive, but haven't tried that.

---

### Post by 3rdalbum on 2010-02-04
I use Ogmrip. I use MPEG-4 video and MP3 audio inside an MKV container, but if you like to support Free Software you should use Theora video, Vorbis audio inside an Ogg container.

> looking to either rip at full quality DVD backup to either AVI or mkv (whichever is best quality/size ratio ya know)

Those are just container formats, not codecs. AVI and MKV can both contain whatever sort of audio and video formats you want. MKV is a better container format because it can contain text information too, and multiple simultaneous video and audio streams. In short, a video inside AVI is exactly the same once decoded as the same video data inside an MKV container.

---

### Post by 3rdalbum on 2010-02-04
> **mrapoc said:**
> can both do x264 avi/mkv?

K9Copy can.

---

### Post by 3rdalbum on 2010-02-04
> **Tholley said:**
> I would imagine there is a way to convert an ISO image to avi if you really want to store them on a drive, but haven't tried that.

Mount it and then use any of your normal rippers; or use Ogmrip which can accept a DVD ISO.

---

### Post by mrapoc on 2010-02-04
Ah DeVeDe used to fail for me too

So use handbrake to copy to a .ISO, then use handbrake to encode too - ill try that

---

