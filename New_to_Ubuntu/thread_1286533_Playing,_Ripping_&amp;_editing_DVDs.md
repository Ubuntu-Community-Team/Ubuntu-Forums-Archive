---
title: "Playing, Ripping &amp; editing DVDs"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-09
I need to play a DVD, rip it (or import into video editor) then edit it (output little clips of flv files).

I did this on Windows XP with Pinnacle Studio.

What would I need for Ubuntu: PLAYING, RIPPING & EDITING?

I am guessing I will need separate apps and new codecs but would love to hear if people can point me in the right direction.

The DVDs will have no protection.

---

### Post by canadiandude007 on 2009-10-09
Lots of choice out there, but have a look at:

DeVeDe [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

Kino and DVDStyler are also good:

[http://www.linuxjournal.com/article/8413](http://www.linuxjournal.com/article/8413)

Hope that helps!

---

### Post by smileyguy on 2009-10-09
Creating DVDs is something I actually don't want to do (yet).

I basically want to output small clips from large DVD titles (not necessarily commercial DVDs) so I need to RIP/import the DVDs then edit the footage and output as flv (or other format and convert to flv).

In Windows I used to use Pinnacle Studio to IMPORT a DVD then edit the imported mpeg clips as I liked.

---

### Post by 3rdalbum on 2009-10-09
To play DVDs, use VLC.

To rip DVDs into uncompressed VOB, you might want to use Acidrip on "copy" settings. Or, better yet, put spaces in the destination filename in Acidrip, and then go to the /tmp directory and you'll see a plain unencrypted VOB there. And you can just drag it into...

...Kdenlive, which is a reasonably easy-to-use video editor for Linux. It can output to Flash Video. It can output into almost any format I've heard of.

---

### Post by smileyguy on 2009-10-10
Thanks 3rdalbum.

---

### Post by MrWES on 2009-10-10
> **smileyguy said:**
> I need to play a DVD, rip it (or import into video editor) then edit it (output little clips of flv files).

I did this on Windows XP with Pinnacle Studio.

What would I need for Ubuntu: PLAYING, RIPPING & EDITING?

I am guessing I will need separate apps and new codecs but would love to hear if people can point me in the right direction.

The DVDs will have no protection.

There are so many ways to rip and manipulate video in Ubuntu, command line and GUI apps, you would spend months trying them all! First I would make sure you have the ubuntu-restricted-extras package installed; this will give you the codecs you'll need.
```
sudo apt-get install ubuntu-restricted-extras
```
I would also look into ffmepg, and either compile or installed the unlocked version, which contains EVERYTHING you'd every need to convert video and audio files. FFmpeg can be run from the command line, or there are several frontend GUIs like Handbrake or WinFF
[http://winff.org/html_new/]("http://winff.org/html_new/")
[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")
[http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs]("http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs")
[http://handbrake.fr/]("http://handbrake.fr/")
For me, I generally rip the main title from a DVD using the command line and vobcopy.
```
sudo apt-get install vobcopy
```
The man pages for vobcopy are pretty straight forward. I then either use Handbrake and/or Avidemux for editing and converting.

Well that's just a start, if you're an audio and videophile Ubuntu has some lean and mean tools and this is just a start. 

~Bill

---

### Post by e.m.fields on 2009-11-06
**@ Bill**
> **MrWES said:**
> 
[...]
I would also look into ffmepg, and either compile or installed the unlocked version, which contains EVERYTHING you'd every need to convert video and audio files. FFmpeg can be run from the command line, or there are several frontend GUIs like Handbrake or WinFF
[http://winff.org/html_new/]("http://winff.org/html_new/")
[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")
[http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs]("http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs")
[http://handbrake.fr/]("http://handbrake.fr/")
For me, I generally rip the main title from a DVD using the command line and vobcopy.
```
sudo apt-get install vobcopy
```
The man pages for vobcopy are pretty straight forward. I then either use Handbrake and/or Avidemux for editing and converting.

**Dude, that's a concise but extremely informative post, thanks.**  You probably don't even know, but I've been searching MASSIVE amounts of forums for hours, and this is the first time I've learned that you have to compile an "unlocked version".  If you have time to give me a clue where to start besides "RTFM", it would save me many more hours.

SINCERELY,

---

