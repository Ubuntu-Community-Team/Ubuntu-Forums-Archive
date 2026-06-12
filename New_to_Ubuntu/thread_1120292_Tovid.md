---
title: "Tovid"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Fableflame on 2009-04-08
I burned a dvd with Tovid, but the audio and the video doesn't sinc up right, did I do something wrong?

---

### Post by aeiah on 2009-04-08
perhaps. i think the tovid site warns against using ubuntu's default ffmpeg install? perhaps im going mad. i use a script that calls upon tovid stuff and my dvds come out fine, so i dont think it's necessarily tovid's fault per se.

do you get the same errors if you try to just go down the ffmpeg / dvdauthor route?

```

ffmpeg -i inputfile.avi -target pal-dvd -sameq output.mpg

dvdauthor -o DVD_dir/ -t output.mpg

dvdauthor -o DVD_dir/ -T

mkisofs -dvd-video -v -o DVD.iso DVD_dir

```

---

### Post by Hospadar on 2009-04-08
If it's an issue with stock ffmpeg, maybe try the medibuntu version
[http://www.medibuntu.org/](http://www.medibuntu.org/) (go to repository howto)

---

### Post by andrew.46 on 2009-04-09
Hi aeiah,

> **aeiah said:**
> perhaps. i think the tovid site warns against using ubuntu's default ffmpeg install?

Indeed [it does]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu"):

> 
**Caveat**

The ffmpeg from main repositories is likely crippled in some way.


Which is not a great reflection on Ubuntu I feel. There is a new guide that aims at addressing the shortcomings of the Ubuntu FFmpeg here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

This is well worth a read.

Andrew

---

