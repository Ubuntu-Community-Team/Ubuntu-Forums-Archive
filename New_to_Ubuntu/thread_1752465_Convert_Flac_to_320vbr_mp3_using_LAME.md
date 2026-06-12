---
title: "Convert Flac to 320vbr mp3 using LAME"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Rhyzome on 2011-05-07
I'm fairly new to Ubuntu. I'm using 10.04 Lucid Lynx. I have downloaded gigs of FLAC files and want to know the best/fastest/easiest way to turn them all into 320 vbr mp3 files using LAME. I'd already downloaded FLAC and LAME using synaptic before I spent an hour looking through forum pages and other google results. I can make sense out of some of the results but none really seem to let me know I'd be using LAME. I was used to turning the files into wav files in batches with the FLAC prog, then using EAC/LAME to mp3 them and correcting them as needed in winamp.

Thanks for any help.

---

### Post by Rhyzome on 2011-05-07
One more thing: I want the original files to remain as I downloaded them from a private server and want to keep sharing them. Oh, and try not to go over my head, I'm still a n00b (any explanations will be GREATLY appreciated as a learning experience).

---

### Post by wolfen69 on 2011-05-07
I use CDex for ripping. It is an open source app made for windows, but works great with wine. If you use this, download 1.51 version. [http://www.oldapps.com/CDex.php](http://www.oldapps.com/CDex.php)

---

### Post by K_45 on 2011-05-07
Just check 

```
man lame
```

and work out the right switches, although I'd use vorbis.

---

### Post by Rhyzome on 2011-05-07
looking at man lame makes me wish I started using linux 20 years ago.

---

### Post by ExileAmongYou on 2011-05-07
Have you tried "Sound Converter" from the Software Center? It's very easy to use, although it might not have enough options for you if you're really particular about the conversion options.

---

### Post by tgalati4 on 2011-05-07
Go into the directory that has your music:

lame --vbr-new -b 320 *.flac *.mp3

Stand back and watch your laptop melt in amazement.

You have no time to waste.

I don't have any flac files to test if lame can read them.  If not, then use sox:

sudo apt-get install sox

Then use sox to convert flac to wav and lame from wav to vbr320.

man sox

for details.  You can do weird stuff like:

play "|rec -d pitch -200"

---

### Post by Rhyzome on 2011-05-07
ok, so i had terminal open the directory and when I typed in " lame --vbr-new -b 320 *.flac *.mp3" 
lame: excess arg Motown Singles - CD01-03 - Eddie Holland - Merry-Go-Round.flac is what it told me.

---

### Post by tgalati4 on 2011-05-07
You need to write a script that recurses through the directories, converting them--sort of search and destroy.

Put this in the google search bar:

linux script recurse flac mp3 convert

This thread in particular:

[http://ubuntuforums.org/showthread.php?t=1658680&page=2](http://ubuntuforums.org/showthread.php?t=1658680&page=2)

Which links to:

[http://code.google.com/p/music-collection-sync/](http://code.google.com/p/music-collection-sync/)

---

### Post by andrew.46 on 2011-05-08
Don't forget that lame will not accept flac files as input, you will need to convert to an intermediate format, or let FFmpeg do it for you as [shantiq demonstrates]("http://ubuntuforums.org/showpost.php?p=10323818&postcount=19") in the thread mentioned.

---

### Post by stoian on 2012-02-14
here is a script which works:

[http://pastebin.com/i50iQdeA](http://pastebin.com/i50iQdeA)

you only have to change the lame options, as now it only does 320 kbps cbr.

---

