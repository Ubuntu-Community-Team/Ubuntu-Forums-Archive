---
title: "CD vs. DVD?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Mariane on 2008-12-03
Hi everyone, 

I'm puzzled by this difference between CDs and DVDs. Is 
a DVD a CD with more disk space, or is there some kind 
on hardware difference between the 2 making one 
incompatible with the other? 

I have 4 musical CDs, commercial stuff all by the same 
artist. On all of them there are some songs I like 
and some I like less. I want to create a new CD with 
only the songs I like. 

One of these songs has talk before it, so for this one 
I wish to edit the file to remove the talk and only keep 
the song. 

Yesterday I got RW DVDs and copied unto 2 of them 
using k3b. 
On one DVD I copied 3 .wav files (to test). 
On another DVD I copied a whole music CD. 
I tried both DVDs in my radio/CD player. None could 
be read. They are read fine by the laptop. 

The files have white spaces in their names 
"Track 01.wav", etc. Could this be an issue? 

It took about an hour to transfer the music CD onto 
my laptop but only a few seconds to transfer from the 
laptop to the DVD. Is this normal? I have to transfer 
on my laptop first as I only have one CD/DVD slot. 

Why is saving on a DVD called "burn" instead of "save"? 

Why doesn't noatun exit when you click on the little 
top-right x? It only goes and hides in the task bar 
(KDE) and KEEPS PLAYING. :( 

Why are there several versions of the songs on the 
music CD? I seem to have everything 4 times. 
* The root directory has the .wav files, 1 per song. 
* CDA directory has .cda files, whatever these are, 
1 per song. 
* Full CD directory had "Full CD.cda", "Full CD.ogg" 
and "Full CD.wav"
* Information directory has an empty txt file called 
"CDDB Information: No record found.txt"
* Ogg Vorbis directory has .ogg files, 1 per song. 

So, 4 versions of all songs plus the cda... Why? 
And what is the cda? Can I delete everything except 
the individual .wav files, in order to be able to 
put more songs onto the DVD (or CD)?

Will I be able to use these DVDs at all or will I 
have to discard them and get some CDs?

Mariane

---

### Post by halitech on 2008-12-03
they are different in the way they are read. a DVD player/burner will normally read a cd but a cd rom/burner will not read a DVD. 

.wav files cannot be read by a cd player, it needs to be burned as an audio cd.

if you have DVD RW then you should be able to erase them and reuse them

---

### Post by Mariane on 2008-12-03
Thank you. 

So, how do I specify I want to create an audio cd, 
please? 

Mariane

---

### Post by Michael.Godawski on 2008-12-03
Every good burning application like brasero which comes pre-installed in Ubuntu Intrepid or k3b has an option to burn an traditional audio cd which will be playable on computers and stereos.

Have a look at these tutorials:
[https://help.ubuntu.com/8.04/musicvideophotos/C/cdburning.html](https://help.ubuntu.com/8.04/musicvideophotos/C/cdburning.html)
[https://help.ubuntu.com/community/Brasero](https://help.ubuntu.com/community/Brasero)
[https://help.ubuntu.com/community/K3b](https://help.ubuntu.com/community/K3b)

---

### Post by tarps87 on 2008-12-03
You want to create a new audio project, when k3b starts I believe this is one of the options. An audio cd can be played in most cd players, some have issues with copied cd but this is very rare.
If your cd player supports the mp3 format you can copy mp3 formatted files onto a cd, the bonus of this way is that you can store more music on the cd, but you can only play these in a mp3 supported player.

To sum it up if it is a standard cd play, you will need to create a audio project. In k3b File -> new project -> audio cd
select you music files and then burn

Hope this helps

---

### Post by Keen101 on 2008-12-03
DVD's are in another format, and cannot be read by regular cd players. I've had drives fail to read dvd's, but not cd's becuase the dvd read laser failed. I believe there are four lasers that can fail if the drive can read and burn, maybe more.

yeah, you will need to use a regular CD-R, and use brasero or gnomebaker to create a specific audio disc instead of just copying the wav files.

---

### Post by carml on 2008-12-03
It may be quite normal you spent 1 hour to copy all of your cds over the disk,and then to spent less time to transfer them to the DVD,it depends on the Read/Write speed from the optical unit(your cd/DVD or what else burner) to the hard drive.Consider that in the second phase it was your hard drive leading the transfer.
Yes,there's a substantial difference beween a CD and a DVD: it relays on the burning method;reducing the space among the data you can put more data(this is the DVD case),an hifi cannot read a DVD because of this reason.):P.

---

### Post by Mariane on 2008-12-05
Thank you everybody. I copied the .wav files unto my hard disk then used brasero to burn a CD. I'll tell you whether my CD player was able to read it or not. I was not sure about choosing .wav as the CD also has .ogg files. 

The second part of my problem is how to edit one .wav (or .ogg) file to remove the talk which happens before the song. I know .wav have rather complex headers so just cutting the file would be useless as the song comes after the talk so I would have to re-create a header for it. Anyway I don't know how to divide a binary file. 

Mariane

---

### Post by Awperator on 2008-12-05
> **Mariane said:**
> Thank you everybody. I copied the .wav files unto my hard disk then used brasero to burn a CD. I'll tell you whether my CD player was able to read it or not. I was not sure about choosing .wav as the CD also has .ogg files. 

The second part of my problem is how to edit one .wav (or .ogg) file to remove the talk which happens before the song. I know .wav have rather complex headers so just cutting the file would be useless as the song comes after the talk so I would have to re-create a header for it. Anyway I don't know how to divide a binary file. 

Mariane

You can use audacity to edit sound files. You can either edit the wav or convert it to mp3 and strip the talk part either way. I am unfamiliar with wav files having complex headers. I have usually been able to just edit wav files straight. If you need help installing or using audacity, please post again.

---

### Post by snova on 2008-12-05
> **Mariane said:**
> Why is saving on a DVD called "burn" instead of "save"?

Inconsistent wording? It means the same.

> Why doesn't noatun exit when you click on the little 
top-right x? It only goes and hides in the task bar 
(KDE) and KEEPS PLAYING. :(

This can be quite useful. There's probably an option somewhere to disable this if you don't like it.

> Why are there several versions of the songs on the 
music CD? I seem to have everything 4 times. 
* The root directory has the .wav files, 1 per song. 
* CDA directory has .cda files, whatever these are, 
1 per song. 
* Full CD directory had "Full CD.cda", "Full CD.ogg" 
and "Full CD.wav"
* Information directory has an empty txt file called 
"CDDB Information: No record found.txt"
* Ogg Vorbis directory has .ogg files, 1 per song.

I've seen that. I don't think they're actually there. For one thing, would all that actually fit on a single disk? ;) (Especially the "Full CD" ones.) For another, it'd be pointless, since a lot of players don't even support Ogg Vorbis.

I think the purpose is so that you can drag and drop them somewhere and have it automatically convert the audio format.

---

### Post by Therion on 2008-12-05
> **Mariane said:**
> Why is saving on a DVD called "burn" instead of "save"? 
Good question... I tend to think of **saving** as moving data onto a CD/DVD for, say, back-ups or just off-line storage and the like.

**Burning**, on the other hand is when I expect the disk to *do something*; like auto-run when inserted into my drive or play a movie.

But that's just me and my twisted way of thinking about things.  You should hear my conspiracy theorie's sometime!!!

---

### Post by oldos2er on 2008-12-05
"Burning" comes from the laser burning data onto a DVD or CD.

---

