---
title: "rm to mp3"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by baroudi on 2009-09-07
hi
i'm a new in linux,
i tried winff but it says "unsupported format" and ffmpeg doesn't work!!:confused:

---

### Post by andrew.46 on 2009-09-07
Hi baroudi,

> **baroudi said:**
> i tried winff but it says "unsupported format" and ffmpeg doesn't work!!:confused:

I see you already have a copy of FFmpeg on your system. Could you try the following suggestions to get the full potential from your copy:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then identify your troublesome file from the commandline as follows:

```
ffmpeg -i ***[COLOR="Red"]my_file.rm[/COLOR]***
```

If you post the fill terminal output I am sure the correct syntax for conversion can be suggested for this file.

All the best,

Andrew

---

### Post by stumbleUpon on 2009-09-07
See if the script in this thread is useful to you

[http://ubuntuforums.org/showthread.php?t=1110872](http://ubuntuforums.org/showthread.php?t=1110872)

---

### Post by baroudi on 2009-09-07
Well it worked thx Andrew.

---

### Post by andrew.46 on 2009-09-07
Hi barudi,

> **baroudi said:**
> Well it worked thx Andrew.

If you mean the script thanks are for stumbleUpon who did most of the initial work :-). Last time I looked at the script and my modifications it was still a little rough around the edges...

And of course if you meant the FFmpeg page FakeOutdorsman is your man!

Andrew

---

### Post by llamabr on 2009-09-07
Also vsound is written for this purpose:

[http://www.vsound.org/](http://www.vsound.org/)

---

### Post by andrew.46 on 2009-09-08
Hi again barudi,

I will admit that I have not tried this application but I see Medibuntu has a package that should fit the bill for you:

Package: rmconverter [non-free/sound]
[http://packages.medibuntu.org/jaunty/rmconverter.html](http://packages.medibuntu.org/jaunty/rmconverter.html)

The best way to get this program would be to add the Medibuntu repository to your repository list. Details here:

Medibuntu - Ubuntu Community Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I would be interested to hear how you find this program, I am just in the process of installing it myself :).

Andrew

---

