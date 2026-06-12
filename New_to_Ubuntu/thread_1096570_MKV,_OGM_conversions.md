---
title: "MKV, OGM conversions"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by HebrewTheHammer on 2009-03-15
Hey guys,
I'm using gutsy.

I have some MKV and/or some OGM video files i want converted to Avi, Divx, mpeg 4, WMV etc. i want it to play on my ps3(playstation 3), which has limited video support, but it acts more like a home entertainment console than my computer does. i haven't got around to making my computer for anything other than work.

I am using convertit( [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016) ). 

It's based on mancoder ffmpeg gambas2 and what not.

When ever i convert using this(no matter what i try to convert it to) i alway get a watchable peice of poop. it sets the audio of by 30 secs and doesn't play but half the video i'm trying to view.

I have had other successful ventures but only converting from avi to divx, xvid, wmv, mpeg4 etc. whenever I throw MKV or OGM into the mix i get the same result.

I don't really understand MKV and OGM however, Does the converter not have the necessary programs or support to convert these file types, is it impossible, do i need a better converter, do i need to stop trying to get a virtual copy off my dvd's. 

Thanks in advanced.

---

### Post by martrn on 2009-03-15
> **HebrewTheHammer said:**
> I have some MKV and/or some OGM video files i want converted to Avi, Divx, mpeg 4, WMV etc. [..] ..I don't really understand MKV and OGM however, Does the converter not have the necessary programs or support to convert these file types, [....].

Have you tried
```
sudo apt-get install avidemux
```
?

Can you play the mkv / ogm files normally in mplayer / vlc player etc.. ?

I don't know anything about the mkv format, I thing the ogg/video format is just a container file format for differing kinds of MPEG layer 4 codecs.

You need to install all the codecs from the unofficial repositories to use this file format.

---

### Post by HebrewTheHammer on 2009-03-16
Yeah i can play them on my pc, using mplayer...however i cannot play them on my ps3...

i use my ps3 for home entertainment 
i use my pc for work

therefore i want to change them into an avi, mpeg, divx, xvid, wmv, etc.

i think you right about them being a sort of container file type. 


But i went ahead and installed avidemux, is that a codec to play them?

---

### Post by leonardo_neo on 2009-03-16
For converting and compressing video files, I use 'avidemux'. Though claimed by many people that this is equivalent to pro software, I politely disagree with that, because I find many issues when I try to convert files with that. Mostly I use it to convert .avi files. But still it is one of the best software I found in the package list, and I think you should give it a try.

For sound conversion, I uses "soundconverter". This software is really very good, and works seamlessly! I give 5/5 to sound converter.

---

### Post by HebrewTheHammer on 2009-03-20
Well i got avidemux...but...eh...i...cant figure it out :oops:

i can sync the audio, but how do i actually get it to convert.

maybe an instructional video, readme, tutorial?

---

### Post by HebrewTheHammer on 2009-03-20
OK i'm in the process of my first .OGM to .AVI

i will let you guys know how it turns out.

---

