---
title: "What is good audio converter software?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by cloyd on 2010-01-25
I'm looking for a audio file converter to convert mp3, ogg, wav, wma, etc. Especially, I want to convert mp3 to ogg, and ogg to mp3. I would like to have the ability to handle conversions in batches.  While using Windows, I used Easy CDA extractor from Poilkisoft----it did batch conversions, ripped, burned and worked well with my old Dell Inspiron when other audio programs gave bad results. It had no flashy graphics, and cost only $20 to $30. (If you still do a lot in Windows, I recccomend it!) I love my music (I'm a boomer) and collect 60' &O 70's rock and roll and country wherever I can find it.  

I have lots of music files, and am considering converting _lots_ of mp3's to ogg.   I have a program called  Ogg Convert, but I have to load and process one mp3 at a time, and don't know that it will go both ways. Converting each file one at a time is too slow.  I need to be able to load a list of 20 or so files to convert at once. What would others reccomend to use in Ubuntu?

I may be off the net for a few days, but I'd appreciate any input.  Thanks in advance.:)

---

### Post by cascade9 on 2010-01-25
Soundkonverter (KDE) or Soundconverter (gnome). 

I hope you are aware that with lossy-> lossy transcodes the output file is always lower quality than the input file.....

---

### Post by cloyd on 2010-01-25
Yes, I am aware. Most of my mp3's are the original from emusic.  I don't reallly intend to do an endless chain of conversions; I am aware that quality will deteriorate. None the less, thanks for the reminder. I would like a batch converter.

Thanks.

---

### Post by hashimoto on 2010-01-25
> **cloyd said:**
> ...I would like a batch converter.

Thanks.

Soundconverter can do batches/whole folders with subfolders, all at once; create new subfolders to converted files or replace the originals, etc.

---

### Post by cloyd on 2010-01-25
Thanks. I'll look into that one.

---

### Post by howefield on 2010-01-25
> **cloyd said:**
> I would like a batch converter.

Winff, a front end for the excellent ffmpeg.

---

### Post by ajgreeny on 2010-01-25
Never used winff, but the command line ffmpeg is superb, so no doubt winff is also good.

---

### Post by cloyd on 2010-01-25
Thanks hashimoto and cascade9.  (Cascade9, I didn't read your first remark when I first read your reply. Sorry.) You both gave the same info, and I have tried it, and it seems to be exactly what I want. Again, thanks alot.

---

### Post by cascade9 on 2010-01-25
> **cloyd said:**
> (Cascade9, I didn't read your first remark when I first read your reply. Sorry.)

LOL, not a problem. ;) 

You've got something that works for you, that is really all that matters :)

---

### Post by hessiess on 2010-01-25
FFMpeg

---

### Post by FakeOutdoorsman on 2010-01-25
Just about any command-line program, such as FFmpeg, can be used with the *find* command to perform batch processing.  See the excellent *find* tutorial by andrew.46:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

---

