---
title: "No sound in video clip - AMR issue"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by OllieGab on 2009-12-26
Tried to play a video clip with the extension .mp4 but had no sound. I got the message that I need an AMR codec. Searched on this and was advised to install Medibuntu repository - which I did.
Still no luck. Tried to play the clip in MoviePlayer, Chromium and VLC but no sound.
Any suggestions?

Cheers Ollie

---

### Post by 4Orbs on 2009-12-26
Check out [This Link]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by Tankerdog2002 on 2009-12-26
Open synaptic.

See if you have [gstreamer], [mpeg123-esd], and [libalsaplayer] installed.

---

### Post by OllieGab on 2009-12-26
I've tried all the above but still get exactly the same error message! It doesn't matter which player I use, the "react" the same...

---

### Post by AdotB on 2009-12-26
I beieve the medibuntu repository has these amr packages:
amrnb
amrwb
libamrnb3
libamrwb3
libopencore-amrnb0
libopencore-amrwb0

And the medibuntu mplayer is also built with amr support.

I don't know which of those packages is what you need, or if any of them will work at all, but I hope that at least give you something to look for.

---

### Post by mc4man on 2009-12-26
You should really post what version of ubuntu you're using

As noted above mplayer is your best bet, though amr support is possible in most players with some work.

For instance on karmic I have amr thru totem (gstreamer), totem-xine (up to 3gp4), vlc, mplayer

In the upcoming lucid, amr support has been added to gstreamer thru the ugly plug-in, that plug-in can be built and used in karmic ( an i386 .deb for karmic is available to test upon request

---

### Post by OllieGab on 2009-12-27
I'm using 9.10 and I still haven't got it to work. I used the synaptic to add all of the above recommended codecs but I must be doing something wrong.
When I use MPlayer I get: 
"Cannot find codec for format 0x726D6173"

When I use VCL I get:
"No suitable decoder module:
VLC does not support the audio or video format "samr". Unfortunately there is no way for you to fix this.

When I use MoviePlayer I get:
"No packages with the requested plugins found. The requested plugins are:
Adaptive Multi Rate (AMR) decoder"

So, where to now?

---

### Post by andrew.46 on 2009-12-27
Hi OllieGab,

> **OllieGab said:**
> I'm using 9.10 and I still haven't got it to work. I used the synaptic to add all of the above recommended codecs but I must be doing something wrong.

The problem in the past has been that AMR playback involved use of some decidedly unfree software and thus has not been part of most software under Ubuntu, although it has usually been possible to build your own MPlayer and vlc/libavcodec to enable such playback.

It is all changing now, as mc4man has mentioned, as there is an open source implementation of AMR called libopencore-amr and hopefully in lucid playback of these files will be possible 'out of the packet' for MPlayer and vlc.

What is a little new for Karmic is that Medibuntu has recently added in a version of libavcodec that contains the AMR codec:

Package: libavcodec-extra-52 [non-free/libs]
[http://packages.medibuntu.org/karmic/libavcodec-extra-52.html](http://packages.medibuntu.org/karmic/libavcodec-extra-52.html)

and while I have not tested this myself I would imagine that this would allow MPlayer to playback amr files? I will check it out when I have reinstalled Karmic if mc4man does not beat me to it :).

Andrew

---

### Post by andrew.46 on 2009-12-27
Hi again OllieGab,

On a fresh installation of Karmic looks like I was right and the new libavcodec from Medibuntu enables amr playback for MPlayer. Try the following command, just copy the whole thing and paste into the terminal:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && \
sudo apt-get install -y mplayer-nogui smplayer libavcodec-extra-52

```

and then you should be able to open your file with SMPlayer. If you have a 32bit system you might be as well to add:

```
sudo apt-get install w32codecs
```

for the sake of a better and more complete copy of MPlayer although this is not required for amr playback....

All the best,

Andrew

---

### Post by mc4man on 2009-12-28
> hopefully in lucid playback of these files will be possible 'out of the packet' for MPlayer and vlc.

because of some licensing concerns for libavcodec (GPLv2 vs GPLv3 ), it doesn't appear that the repo libavcodec will support amr in lucid, and by extension the repo mplayer and vlc.

It apparently will then be up to medibuntu and or ppa's to offer a non building solution as in karmic.
karmic gstreamer support for [amr]("http://ubuntuforums.org/showthread.php?p=8568097#post8568097")

---

### Post by OllieGab on 2009-12-31
Hey, that worked fine!
Cheers for that!!
 OllieGab

---

### Post by [A]madeus on 2010-01-28
> **andrew.46 said:**
> Hi again OllieGab,

On a fresh installation of Karmic looks like I was right and the new libavcodec from Medibuntu enables amr playback for MPlayer. Try the following command, just copy the whole thing and paste into the terminal:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && \
sudo apt-get install -y mplayer-nogui smplayer libavcodec-extra-52

```and then you should be able to open your file with SMPlayer. If you have a 32bit system you might be as well to add:

```
sudo apt-get install w32codecs
```for the sake of a better and more complete copy of MPlayer although this is not required for amr playback....

All the best,

Andrew

Hi Andrew,
Thank you for your solution.
It works.

Cheers,

---

### Post by andrew.46 on 2010-01-28
Hi Amadeus,

> **'[A]madeus said:**
> Thank you for your solution. It works.

Great news :). Looks like Medibuntu are going to support [the same package ]("http://packages.medibuntu.org/lucid/libavcodec-extra-52.html")for Lucid as well...

Andrew

---

