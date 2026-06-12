---
title: "THE tools to convert DVDs to AVI"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Jaraqui on 2010-11-15
Hi people,     Thinking about where to post, I concluded that these are very beginner questions, but I´m having some difficulties to  find the answers:    x) What is the tool that: a) I pick a DVD movie; b) put this DVD in my drive; c) call a powerfull tool and convert its contents to an AVI file by selecting some options in a  graphical menu?    y) Where can I find a simple quick-guide for this hipotetical tool?     Some notes:    1) I found some tools that do something like this. The  differences were, at the end of the process, several AVI  files containing pieces of the film were created;    2) Belonging to the same problem, there is the  audio/subtitles options that must be choosen after the film  itself begins. I would wondering some tool that has a "start"  button and begins to capture/record/convert after my options  were choosen;    3) Regarding notes (1) and (2), it is considered "accepted"  for this tool some extra-files for the extra options in the DVD  (comments of the director, alternative ends, blah, blah, blah).  Thanks in advance Jaraqui

---

### Post by 311005901 on 2010-11-15
Have you tried [Handbrake]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots")? It might be what you're looking for.

---

### Post by rampageoberon on 2010-11-15
Maybe DVD::RIP could also work for you? ```
sudo aptitude search dvdrip
```

---

### Post by blur xc on 2010-11-15
> **311005901 said:**
> Have you tried [Handbrake]("https://edge.launchpad.net/%7Estebbins/+archive/handbrake-snapshots")? It might be what you're looking for.


Handbrake ftw.  I've used it a few times and it's got handy presets for popular portable media devices (ipod, iphone, psp, etc...)

BM

---

### Post by howefield on 2010-11-15
> **311005901 said:**
> Have you tried [Handbrake]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots")? It might be what you're looking for.

Excellent application that it is, it wouldn't work, at least not if the output has to be .avi

dvd::rip would however.

---

### Post by MartyBuntu on 2010-11-15
AcidRip.

My personal favourite.

---

### Post by andrew.46 on 2010-11-16
You could try and get your hands a little dirty and take the commandline way:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

BTW avi might not be such a good choice of container, have a look at either mp4 or mkv?

Andrew

---

### Post by slooksterpsv on 2010-11-16
I recommend DVD::RIP, but you do need to resolve some dependencies (just install them as it doesn't for you) - such as rar, and that. When you get into the program go to Help -> Debug and it'll tell you what you need to install, whatever is in read go ahead and search for it in Software Center.

---

### Post by cascade9 on 2010-11-16
K9copy is decent as well. Probably better for KDE users though (not that it wont work on gnome/xfce/lxde/etc)

---

### Post by MellieM87 on 2011-02-21
I have tried to use Acidrip, and I have used the instructions of someone which I found on a much older post on this site, but everytime I click start, it pops up with an error stating Mencoder interrupted by user. Can anyone tell me what this means, as I don't do anything to stop it from starting? 

Apart from that, it seems pretty easy to use, I haven't tried anything else on Linux.

---

### Post by Mariane on 2011-02-21
dvdrip is fine. On first use launch it through the command line so you can read the error messages such as missing libraries. You need libdvdcss among other stuff. 

Don't worry, though, once you getit working it'll keep on working. It has only one drawback: it takes about 2 hours to rip a dvd, depending upon settings and you computer. 

Mariane

---

### Post by waynefoutz on 2011-02-21
> **MartyBuntu said:**
> AcidRip.

My personal favourite.

+1 on Acidrip.

Unlike the others, it does the conversion as it rips. DVD::rip and Handbrake take twice as long, because there are two steps, ripping, then transcoding. You can set up DVD::rip to do this as well, but it takes twice as long as Acidrip. With Acidrip, I can put a DVD in, and take it out 30-40 min later with a 700 mb avi file on my hard drive.

---

### Post by JohnAStebbins on 2011-02-21
> **waynefoutz said:**
> +1 on Acidrip.

Unlike the others, it does the conversion as it rips. DVD::rip and Handbrake take twice as long, because there are two steps, ripping, then transcoding. You can set up DVD::rip to do this as well, but it takes twice as long as Acidrip. With Acidrip, I can put a DVD in, and take it out 30-40 min later with a 700 mb avi file on my hard drive.

HandBrake does **not** require 2 steps.  If you have libdvdcss installed, it can transcode direct from disc.

---

### Post by howefield on 2011-02-21
> **JohnAStebbins said:**
> HandBrake does **not** require 2 steps.  If you have libdvdcss installed, it can transcode direct from disc.

To get to .avi, it would be a two stage process. On that basis, Handbrake may be a poor choice.

---

### Post by JohnAStebbins on 2011-02-21
> **howefield said:**
> To get to .avi, it would be a two stage process. On that basis, Handbrake may be a poor choice.

Gotchya.  You are correct.  Not only would it take longer, but you loose quality by transcoding twice if your final objective is to get an avi file.

---

### Post by waynefoutz on 2011-02-22
> **JohnAStebbins said:**
> HandBrake does **not** require 2 steps.  If you have libdvdcss installed, it can transcode direct from disc.

I have never had any luck with handbrake, on Linux, or Windows.

---

### Post by MrWES on 2011-02-22
Andrew,
You don't have all that in a bash script? Come on man! :)

~Bill

---

### Post by 3rdalbum on 2011-02-22
> **MellieM87 said:**
> I have tried to use Acidrip, and I have used the instructions of someone which I found on a much older post on this site, but everytime I click start, it pops up with an error stating Mencoder interrupted by user. Can anyone tell me what this means, as I don't do anything to stop it from starting?

Acidrip is unmaintained and that's probably the cause of why you and I can't get it to encode anything anymore; but note that you can't have any spaces in the filename - so don't put spaces in the title of the main feature that you are ripping.

I'd suggest Handbrake (it can't put into an AVI container though) or K9Copy which can rip to disk too.

---

