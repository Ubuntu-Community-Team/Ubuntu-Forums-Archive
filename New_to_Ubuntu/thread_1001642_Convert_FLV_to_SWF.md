---
title: "Convert FLV to SWF"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Flirtilizer on 2008-12-04
Is there a linux tool for coverting FLV files to SWF?

Thanks!

---

### Post by fernandohleme on 2008-12-04
I'd use ffmpeg.
It is a text mode tool incredibly usefull
To install it, open a console and type:
# sudo apt-get install ffmpeg
then, in the same console, find your files directory and:
# ffmpeg -i inputname.flv outputname.swf

There's only one question, i've never tried it with swf, i'd rather mpeg instead.

Hope i've helped.

---

### Post by Michael.Godawski on 2008-12-04
Perhaps you can also check out this:

[http://www.biggmatt.com/winff/](http://www.biggmatt.com/winff/)

it is a graphical front end for the ffmpeg.

---

### Post by FakeOutdoorsman on 2008-12-04
You can probably just copy the audio and video streams from flv to swf without needing to re-encode.  Saves time and preserves quality:
```
ffmpeg -i input.flv -acodec copy -vcodec copy output.swf
```

---

### Post by jayachandranm on 2010-10-17
Using ffmpeg gave me a fast moving video :-(

But I could convert AVI to swf using mencoder and it worked nicely!

> mencoder Test.avi -lavfopts format=swf  -oac mp3lame -of lavf -ovc lavc -lavcopts vcodec=flv:acodec=mp3:vbitrate=500:abitrate=56 -srate 22050 -o Test.swf


Found the options from,
[http://lists.mplayerhq.hu/pipermail/mencoder-users/2009-May/010386.html](http://lists.mplayerhq.hu/pipermail/mencoder-users/2009-May/010386.html)
with the fix,
[http://lists.mplayerhq.hu/pipermail/mencoder-users/2009-May/010389.html](http://lists.mplayerhq.hu/pipermail/mencoder-users/2009-May/010389.html)

---

### Post by Greydog56 on 2011-03-15
> **fernandohleme said:**
> I'd use ffmpeg.
It is a text mode tool incredibly usefull
To install it, open a console and type:
# sudo apt-get install ffmpeg
then, in the same console, find your files directory and:
# ffmpeg -i inputname.flv outputname.swf

There's only one question, i've never tried it with swf, i'd rather mpeg instead.

Hope i've helped.


You sure have helped. The video quality is some less than original but I'm excited it works. My video was  4 mins long and it played fine, the time it shows for length of video in VLC is 37 mins. When the 4 min video was done playing, it stopped normally. Just wondered if anyone had experienced inaccurate duration values.

---

### Post by ~Hinterland on 2011-03-15
> **FakeOutdoorsman said:**
> You can probably just copy the audio and video streams from flv to swf without needing to re-encode.  Saves time and preserves quality:
```
ffmpeg -i input.flv -acodec copy -vcodec copy output.swf
```
This a better way of doing the conversion as it copies the video and audio codec from the input file, so try this instead.

---

### Post by sunilbaj on 2011-10-13
ffmpeg -i input.flv -acodec copy -vcodec copy output.swf


This code converts into swf but it plays so fast. With the other method , the quality is low.Is there any other option?

---

