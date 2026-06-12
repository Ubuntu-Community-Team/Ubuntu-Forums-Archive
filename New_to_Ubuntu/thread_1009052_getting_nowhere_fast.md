---
title: "getting nowhere fast"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by iminhell on 2008-12-12
Still having DVD playing issues. 
I have done everything I can find to resolve the issues and now get a boxy/pixilated moving image.
VLC had said it was something with not being able to crack the CSS, on a DVD from 1997? (Kiss the Girls)
I honestly think that it's not a CSS issue but one where the program is using it wrong or not at all.

How can I make sure things are where they should be and being used appropriately?

running 8.10 and using the xine player (VLC is 2 channel and I wish to avoid that)

---

### Post by s.fox on 2008-12-12
Hi,

Have you added this?

```
sudo apt-get install libdvdcss2
```You could also add medibuntu

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by damis648 on 2008-12-12
> **Ash R said:**
> Hi,

Have you added this?

```
sudo apt-get install libdvdcss2
```

Note this may be illegal in some parts of the world.

---

### Post by s.fox on 2008-12-12
> **damis648 said:**
> Note this may be illegal in some parts of the world.

Really?   I wasn't aware of that. Where?

---

### Post by iminhell on 2008-12-12
legal schmegal (region 1 btw). They are store bought and paid for RIAA kiss my bottom.

... and yes I have done all the media ubuntu stuff as well as a patch I found. Have libdvdread3, libdvdnav4 and libdvdcss2. Nothing works, no one has any clue as to why.

---

### Post by jespdj on 2008-12-12
There are multiple reasons why it might be illegal in certain parts of the world. Not only is it so that your local law might forbid circumventing the copy protection on the DVD, also in some countries you have to pay royalties for the patents on the codec (the USA for example, as far as I know).

If you live in a country where this applies, you're officially supposed to buy the codecs, you could for example buy the [Fluendo Complete Playback Pack](http://shop.canonical.com/product_info.php?products_id=244) from the Canonical shop.

---

### Post by iminhell on 2008-12-12
I have to restart and try a few dvd's but i think i may finally have this thing won.
Came across this thread:  [http://ubuntuforums.org/showthread.php?t=740682](http://ubuntuforums.org/showthread.php?t=740682)
while searching and when I got to page 4 and ran the export command I SAW REAL MOVING PICTURES.

Time will tell.

---

### Post by iminhell on 2008-12-12
After restart I am back in the same boat. So what does that say?

Xine, VLC, Totem and Mplayer will all play the same garbled video though, with errors of course.


This is what I got as output from the code:

> john@ubuntu:~$ export DVDCSS_METHOD=title && mplayer dvd://
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 3200+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 24 titles on this DVD.
There are 21 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 2 language: en
subtitle ( sid ): 3 language: es
number of subtitles on disk: 2
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:   0.7 V:   0.6 A-V:  0.079 ct:  0.043  17/ 14 43%  7%  1.1% 3 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
No bind found for key 'MOUSE_BTN2'.                         5% 4 0 
No bind found for key 'MOUSE_BTN2'.                         9% 4 0 
GNOME screensaver enabled.007 ct:  0.127 4994/4991 10%  8%  2.4% 4 0 

Exiting... (Quit)



I hope something in that helps.

---

### Post by iminhell on 2008-12-13
Anyone?

---

### Post by Michael.Godawski on 2008-12-13
```
 sudo apt-get install libdvdread3 gstreamer0.10-plugins-ugly
```and then
```
 sudo /usr/share/doc/libdvdread3/install-css.sh
```if you haven't done this before.

---

### Post by billgoldberg on 2008-12-13
Sorry, I don't know what is causing the problem if all the codecs are installed.

However I have some questions.

What version of Ubuntu are you using? (if you are not sure, in a terminal do "uname -a" and post it here)

Does the dvd play on other pc's/dvd players?

Do other dvd's work on the same computer?

Did you try disabling compiz-fusion and try it then (press "alt+f2" and do "metacity --replace") play the dvd?

Have you tried some other programs like ogle, mplayer, ... ?

--

Just to be safe, copy/paste this in your terminal and try again:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by iminhell on 2008-12-13
[quote=terminal]john@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux[/quote]

I had the -9 but I felt it may be a problem and removed it. Both did the same thing though. I also thought maybe there was a conflict between the two, which there hasn't seemed to be.



[quote=billgoldberg]
However I have some questions.

1. What version of Ubuntu are you using? (if you are not sure, in a terminal do "uname -a" and post it here)

2. Does the dvd play on other pc's/dvd players?

3. Do other dvd's work on the same computer?

4. Did you try disabling compiz-fusion and try it then (press "alt+f2" and do "metacity --replace") play the dvd?

5. Have you tried some other programs like ogle, mplayer, ... ?[/quote]


1. read above

2. Yes. Plays on a Toshiba laptop running Vista Home Premium and this machine which has Vista Basic (dual boot).

3. I am able to look at ant file on any disc, but playback is garbled with and video media disc.

4. I just tried that and no difference what so ever.

5. Yes. Currently I have Xine, VLC, Mplayer and Totem on here. Playback is the same with all of them and the same with any disc, encrypted or otherwise. Which should mean it isn't an issue with CSS, I would think.

---

### Post by iminhell on 2008-12-13
ripped a dvd to the HDD and tried playback that way, same thing. Tried turning the video driver off, same. tried the other driver (96) same thing.
Card is a geforce fx 5500 pci 128mb ddr that works just fine under windows, shows no errors.

---

### Post by iminhell on 2008-12-13
All players work via the command line only. Must be a bug in the GUI somewhere. Reported to launchpad --> [https://answers.launchpad.net/ubuntu/+question/54351](https://answers.launchpad.net/ubuntu/+question/54351)

---

