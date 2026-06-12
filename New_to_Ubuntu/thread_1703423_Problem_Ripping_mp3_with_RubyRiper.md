---
title: "Problem Ripping mp3 with RubyRiper"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by sobeitjedi on 2011-03-09
Hi.

I'm getting the error "Encoding to mp3 exited with an error with track" ... this is what's in the log (see attached log file) ...

Anyone offer any suggestions?

---

### Post by gmargo on 2011-03-09
I wonder if it's because %s and %n are not quoted, and there are spaces in the names?

Anyway, lame is obviously failing for some reason, and rubyripper is not printing any actual error.  I would temporarily replace **lame** with a shell script so you can check the arguments passed to it.

---

### Post by sobeitjedi on 2011-03-09
The line ...

"-V2 --add-id3v2 --pad-id3v2 --ta "%a" --tt "%t" --tg "%m" --tl "%g" --ty "%y" --tn "%n" %s %d"

Was copied from my Windows machine which uses EAC and works fine.

I'm not sure how to replace lame with a shell script. I'm new to Ubuntu. I want to use it to replace Windows.

---

### Post by ron999 on 2011-03-09
Hi
Your log shows settings:-
-mp3	-> -V2 --add-id3v2 --pad-id3v2 --ta "%a" --tt "%t" --tg "%m" --tl "%g" --ty "%y" --tn "%n" %s %d


My log shows settings:-
-mp3	-> -q 0 -V 0 --id3v2-only

So look in RubyRipper > Preferences > Codecs and try again with trimmed options **-V 2 --id3v2-only** (or similar).

---

### Post by gmargo on 2011-03-09
> 
"-V2 --add-id3v2 --pad-id3v2 --ta "%a" --tt "%t" --tg "%m" --tl "%g" --ty "%y" --tn "%n" %s %d"
Was copied from my Windows machine which uses EAC and works fine.
That line will not work in RubyRipper.

I checked the source code.... RubyRipper does all the work building up arguments to **lame**.  The extra argument strings you've added never get expanded like you think.  So follow ron999's suggestion and reset the arguments to the default (or at least don't use any %X expansions.)

You can see this in the RubyRipper source code in /usr/lib/rubyripper/rr_lib.rb in the mp3() function, about line 2374.

---

### Post by sobeitjedi on 2011-03-09
> **ron999 said:**
> Hi
Your log shows settings:-
-mp3    -> -V2 --add-id3v2 --pad-id3v2 --ta "%a" --tt "%t" --tg "%m" --tl "%g" --ty "%y" --tn "%n" %s %d


My log shows settings:-
-mp3    -> -q 0 -V 0 --id3v2-only

So look in RubyRipper > Preferences > Codecs and try again with trimmed options **-V 2 --id3v2-only** (or similar).

Thanks. While these settings do work and the album rips to mp3 ... when I go to the properties of each file, the bitrate says 104kbps, then 92kbps for another track, 144kbps, 112 kbps, etc etc. I think using my EAC on Windows, I had a variable bitrate of 192kbps. How can this be done with rubyripper?

---

### Post by ron999 on 2011-03-09
> **sobeitjedi said:**
> ...my EAC on Windows, I had a variable bitrate of 192kbps. How can this be done with rubyripper?

The **V** settings for lame set the quality of the rip.
It uses variable bitrate.
So each track shows a different bitrate property.

If you definitely want a variable bitrate of 192k then replace the **-V 2** with:-

**--abr 192k**


That abr option uses variable bitrate, but aims for target 192k.

:D

---

### Post by gmargo on 2011-03-09
I use these Variable Bitrate options for lame:
-h -v -b 192 -V 0

---

### Post by heyho on 2011-03-09
Is rubyripper even current?  I remember having to build it last time I used it.

It doesn't answer the question, but I would recommend using asunder or ripperx.

---

