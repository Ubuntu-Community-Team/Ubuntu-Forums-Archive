---
title: "Combining Video Files"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Tman5293 on 2009-08-15
Hi,

I have a movie thats split up into ten parts and would like to know how to combine all ten files into one.

The Video files are .mp4

Any Help Is Appreciated! :guitar:

---

### Post by andrew.46 on 2009-08-15
Hi Tman,

> **Tman5293 said:**
> I have a movie thats split up into ten parts and would like to know how to combine all ten files into one.

If you are interested in FFmpeg have a quick look at this entry in the FFmpeg FAQs:

3.18 How can I join video files?
[http://ffmpeg.org/faq.html#SEC30](http://ffmpeg.org/faq.html#SEC30)

If you think this looks promising you can optimise your own copy of FFmpeg by following this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

### Post by 3rdalbum on 2009-08-15
Some video files can, surprisingly, be joined just by using "cat". Video decoders can cope with garbage data being inserted into video (as I've discovered) so the sudden inclusion of another video file's header should pose no problems.

---

