---
title: "what is the best movie player"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by eddski on 2011-04-29
I need a movie player that plays flv, mmp4, swf,mov, avi,etc. Any suggestions?

---

### Post by jrozo17 on 2011-04-29
How about VLC? That seems to read a lot of differant formats.

---

### Post by andymorton on 2011-04-29
I'd say VLC as well. It seems to be able to play just about anything.

---

### Post by abnordude on 2011-04-29
Well, just as everyone said. 
VLC is the best player.
It can play almost anything.

---

### Post by kaldor on 2011-04-29
Another vote for VLC.

---

### Post by 3rdalbum on 2011-04-29
Apart from VLC, all the video players on Linux actually use the codecs on the system, rather than each have their own set of codecs. If you're having trouble playing videos, then you're missing some system-wide codecs (and you should install "ubuntu-restricted-extras" from the repositories).

---

### Post by fparri on 2011-04-29
VLC, for me too!

---

### Post by computerandu on 2011-04-29
VLC....the best Video player ever...plays almost all types of video...

---

### Post by SunnyRabbiera on 2011-04-29
VLC here too as its pretty much a Swiss army knife.

---

### Post by hakermania on 2011-04-29
V L S
no no, kidding
VLC
xD

---

### Post by beew on 2011-04-29
mplayer. It has different GUIS and I recommend Umplayer (or Smplayer) (don't know about the version in the Ubuntu repo, but you can get multithreaded versions of mplayer from ppas and they are much better than VLC for high definition movies)

VLC is good but mplayer is much better if you have a Nvidia card or a multicore machine since VLC doesn't use vdpau and it uses only a single core. So high definition movies stutter and freeze even in dual core machines as VLC maxes out one core without using another, whereas playback in mplayer  (ppa version) is smooth as butter. I am told this will change soon because ffmpeg-mt has been merged into the main library in March and new builds of VLC should reflect that.

I don't know how well does vlc use VAAPI if you have an AMD/ATI card. Maybe you should then install vlc from this ppa. 
[URL="https://launchpad.net/%7Edtl131/+archive/catalysthacks"]
https://launchpad.net/~dtl131/+archive/catalysthacks[/URL]

---

