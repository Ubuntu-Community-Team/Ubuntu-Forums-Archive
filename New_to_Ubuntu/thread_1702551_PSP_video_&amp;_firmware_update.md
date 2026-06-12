---
title: "PSP video &amp; firmware update"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by D4J0K3R on 2011-03-07
Hi,

I just bought a PSP Go, I can't manage to put videos on it, I tried avidemux with the auto settings to PSP.
40 minutes for a 10 minutes video... & it doesn't work.
I don't understand how to update the firmware, I don't have a memory stick nor a wi-fi connection.
My PSP Go came with 3 free games which I can't play because I need to update the firmware...
Yeah I know this is not really Ubuntu related, but I'm a about to throw that device in the garbage & I don't know where to ask my question because I was looking for a fast answer...

Thanks you!

---

### Post by Paddy Landau on 2011-03-09
I don't know how to update PSP without a Wi-Fi, sorry.

To convert videos, try the following.

[LIST]
[*]In Avidemux:
[LIST=1]
[*]Open the file you wish to convert.
[*]Auto > PSP (H.264).
[*]PSP full res (720*480)
[*]Save with the extension .mp4.
[/LIST]
 
[*]If that still does not work, try ffmpeg.
```
ffmpeg -i <inputfile> -f psp -r 29.97 -b 768k -ar 24000 -ab 64k -s <outputfile>.mp4
```
[/LIST]
The two following links may or may not help:
[http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml](http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml)
[https://help.ubuntu.com/community/PSP#PSP%20Management%20and%20Video%20Encoding](https://help.ubuntu.com/community/PSP#PSP%20Management%20and%20Video%20Encoding)

---

