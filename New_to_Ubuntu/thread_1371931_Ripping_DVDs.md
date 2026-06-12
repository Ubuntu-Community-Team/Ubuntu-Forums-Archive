---
title: "Ripping DVDs?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by abdullahajj on 2010-01-03
I'm running Ubuntu 9.10

What is the easiest way to rip DVDs to hard drive?

---

### Post by mkoehler on 2010-01-03
There's a multitude of ways, but here's a good tutorial:

[https://help.ubuntu.com/community/DVD::Rip](https://help.ubuntu.com/community/DVD::Rip)

---

### Post by s.fox on 2010-01-04
Hello,

An alternative program that was recently introduced to me is [Handbrake]("http://handbrake.fr/").   :)

-Silver Fox

---

### Post by adelphos on 2010-01-04
> **Silver_fox_ said:**
> Hello,

An alternative program that was recently introduced to me is [Handbrake]("http://handbrake.fr/").   :)

-Silver Fox

Yes. Handbrake seems easier to use, more fully featured, and more stable than the alternatives. A simple and effective way to use ffmpeg via a GUI.

---

### Post by 3rdalbum on 2010-01-04
K9Copy can rip to MPEG-4 (or, I believe, any format FFMPEG can deal with) as well as shrink dual-layer DVDs to fit onto single-layer DVDs.

---

### Post by underquark on 2010-01-04
For us 9.04 luddites, anyone have a link to 0.9.3 (64-bit Deb) download as the Handbrake site only maintains the latest 0.9.4 for ubuntu 9.10?

---

### Post by anaconda on 2010-01-04
acidrip and k9copy are both good.

---

### Post by SuperSonic4 on 2010-01-04
> **3rdalbum said:**
> K9Copy can rip to MPEG-4 (or, I believe, any format FFMPEG can deal with) as well as shrink dual-layer DVDs to fit onto single-layer DVDs.

K9copy usually uses mencoder but you can tell it to use ffmpeg too.

Remember you need *libdvdcss2* from medibuntu

If you are handy with compiling then I'd recommend compiling mencoder (ie: mplayer) with x264 support from VideoLAN (vlc guys). h264 is an excellent encoder albeit a tad slow.

If compiling is not your thing I suggest Handbrake CLI (rather than handbrake GUI - mainly because you can run more than one instance) as it uses an in-house x264 so to speak. For example to rip the longest title to mkv with x264 and ac3 audio:

```
handbrake -i /dev/dvd -L -e x264 -b 1024 -E ac3 -s 1 -o output.mkv
```

As far as I know the main problem with CLI handbrake is that you can only rip one title at a time (although my knowledge is limited) whereas GUI has a queue.


@ underquark, you could still compile (I get mine from SVN)? Although I doubt the 9.10 deb would not work on 9.04

---

### Post by adelphos on 2010-01-04
> **underquark said:**
> For us 9.04 luddites, anyone have a link to 0.9.3 (64-bit Deb) download as the Handbrake site only maintains the latest 0.9.4 for ubuntu 9.10?

This looks like the right package:

[http://old.getdeb.net/app/HandBrake](http://old.getdeb.net/app/HandBrake)

---

### Post by inobe on 2010-01-04
i found serious problems not following this rule "my rule"

1) restricted-extras
2) medibuntu repo
3) ffmpeg
4) handbrake

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

---

### Post by underquark on 2010-01-04
Thank you adelphos!  I did Google away for a while without result (well lots of results but none leading to a suitable download) and have now bookmarked the site you linked to for any future older versions of programs.  I've avoided Karmic just because pretty much everything else I have is OK in Jaunty.  I'll upgrade when next big one comes along.

---

