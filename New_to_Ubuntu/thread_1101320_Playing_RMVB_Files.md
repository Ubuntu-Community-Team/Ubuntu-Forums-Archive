---
title: "Playing RMVB Files"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-03-20
Hi. I'm having trouble trying to play RMVB files in SMPlayer - it loads it, but then defaults to audio mode and gives me sound, but no video. If I open it with MPlayer, I just get an error message.

I've looked around a bit, and downloaded a couple of libraries, but still have the same problem.

---

### Post by Fenris_rising on 2009-03-20
Hi there

Not sure of any technical help for you re what you have and if they can handle the filetype.

I installed realplayer and play my rmvb files no problem at all.

regards

Fenris

---

### Post by rvm4000 on 2009-03-20
> **Azhtabak said:**
> Hi. I'm having trouble trying to play RMVB files in SMPlayer - it loads it, but then defaults to audio mode and gives me sound, but no video. If I open it with MPlayer, I just get an error message.

I've looked around a bit, and downloaded a couple of libraries, but still have the same problem.

Install the package w32codecs (or w64codecs).

---

### Post by Azhtabak on 2009-03-20
That gives me an error message:

```
azhtabak@azhtabak-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
```

---

### Post by rvm4000 on 2009-03-20
That package is in [medibuntu](http://www.medibuntu.org/). Look for it there.

For instance the package for intrepid is here:
[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

---

### Post by Azhtabak on 2009-03-20
Hmm, I can't seem to download that from there - I keep getting an error message. Is it me, or a problem with the download?

---

### Post by bumanie on 2009-03-20
Medibuntu usually works well, you may be doing something wrong. You have to install the[ medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") to your /etc/apt/sources.list (+ the GPG key) before you can download. The instructions are toward the top of the community documentation site. However, as far as I know w32/64 codecs won't play rmvb. You need realplayer or helix player is the open source version that is meant to play rmvb files. You could always convert the rmvb to .avi in something like devede and then nearly any linux player will play them.

---

### Post by Azhtabak on 2009-03-20
Helix player unfortunately doesn't work with them - it redirects me to the linux realplayer for them, but that doesn't download - it either gives me a mac binary file, or a .deb link which opera tries to open o.0

I've installed DeVeDe, so I'll give that a try.

---

### Post by rvm4000 on 2009-03-20
> **Azhtabak said:**
> Hmm, I can't seem to download that from there - I keep getting an error message. Is it me, or a problem with the download?

Doesn't this link work for you?

[http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu3_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu3_i386.deb)

You can also try to add the medibuntu repository to your /etc/apt/sources.list, as explained [here](https://help.ubuntu.com/community/Medibuntu) and then install w32codecs with apt-get as usual.

> **bumanie said:**
> However, as far as I know w32/64 codecs won't play rmvb. You need realplayer or helix player is the open source version that is meant to play rmvb files.

I don't have realplayer or helix player installed, and I can play rmvb files without problems with mplayer.

---

### Post by andrew.46 on 2009-03-20
Hi,

As well as the codecs you may also need libstdc++5. SMplayer and MPlayer will play rmvb's perfectly as RVM has mentioned, I attach a screenshot of [just such a file]("http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/hotel_california_ra5.1_640x480_30s.rmvb") playing.

All the best,

Andrew

---

### Post by SunnyRabbiera on 2009-03-20
Medibuntu should help, also if realplayer doesnt install in mediubuntu try the .deb installer on the realplayer website.

---

### Post by Azhtabak on 2009-03-23
All working now, thanks. Installing it through the command line worked - I'd previously tried downloading the codecs manually as a deb, which got corrupted along the way it seems.

Incidentally, .rmvbs are tiny files o.0

---

