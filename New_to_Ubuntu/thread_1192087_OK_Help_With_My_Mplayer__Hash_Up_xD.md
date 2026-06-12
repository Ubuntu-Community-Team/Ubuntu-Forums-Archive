---
title: "OK Help With My Mplayer  Hash Up xD"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-19
Ok well I've tried to mix this Mplayer build guide to use CoreAVC:

> [http://ubuntuforums.org/showthread.php?t=1034075](http://ubuntuforums.org/showthread.php?t=1034075)

with this guide to building the latest Mplayer on jaunty along with another bit to enable wmv9 sound on x64 bit Ubuntu

> [http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

bit that enables wmv9 audio:

> svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
cp wmapro/wma* libavcodec
patch -p0 <wmapro/audioframesize.patch
patch -p0 <wmapro/mplayer.patch
patch -p0 <wmapro/wmapro_ffmpeg.patch

so if you got your head round that my actual problem is that Mplayer is installed but when I go to install SMplayer it wants me to install Mplayer yet I've just compiled....:lolflag:

Please help:KS

---

### Post by Bachstelze on 2009-06-19
You can't install SMplayer with DEB packages if you have compiled MPlayer. You have to compile SMplayer as well.

---

### Post by kamitsukai on 2009-06-19
> **HymnToLife said:**
> You can't install SMplayer with DEB packages if you have compiled MPlayer. You have to compile SMplayer as well.

ah I see:p

thank you =]

PS: Do you happen to have a guide to installing smplayer from source...?

---

### Post by andrew.46 on 2009-06-20
Hi kamitsukai,

> **kamitsukai said:**
>  my actual problem is that Mplayer is installed but when I go to install SMplayer it wants me to install Mplayer yet I've just compiled....:lolflag:

I suspect that in following HymnToLife's excellent guide you have installed MPlayer using *sudo make install*. This will mean that when you install SMPlayer from the Ubuntu repository it will not *see* that its dependency of MPlayer has already been satisfied. You could follow HymnToLife's suggestion and compile SMPlayer as well or you could experiment a little with the checkinstall syntax of one of the other guides and use something like:

```
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
```

in place of *sudo make install* to tell the package manager that you actually do have a copy of MPlayer installed. Bear in mind as well that you are also installing MEncoder while using any of these guides. Or I guess you could, as HymToLife has suggested in his guide, build a *proper* debian package. Good to have so many choices :-).

Andrew

---

### Post by kamitsukai on 2009-06-20
Well I managed to build smplayer in the end but for some reason playback is still choppy although if i play the same file from command line in mplayer it will work fine =/ is there some kind of option in the smplayer prefferences which i have to enable?

---

