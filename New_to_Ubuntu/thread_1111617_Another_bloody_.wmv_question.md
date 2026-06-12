---
title: "Another bloody .wmv question"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by greenpepper on 2009-03-30
I am a Windows user, but my primary laptop has a busted video card, and I'm borrowing my roommate's Ubuntu computer, running 8.04.

I need to be able to watch .wmv files for class, and am experiencing the following problem: the file will open, and display the first frame, but will not play past the first frame.

I have installed the following:
 ubuntu-restricted-extras
 w32codecs
 libdvdcss2
 mplayer

I have also tried running mplayer with every possible option to the -vo flag (ie, mplayer -vo xv myfile.wmv; mplayer -vo x11 myfile.wmv; etc.)

I'm at my wits end, and dont' know what else to try.

---

### Post by Ms_Angel_D on 2009-03-30
Go to add remove programs, and try installing VLC see if that helps.

[AFTERTHOUGHT]
Are you sure the video is good?
[/AFTERTHOUGHT]

---

### Post by Therion on 2009-03-30
Open Synaptic.
Search on **gstreamer**.
Install the following (of whatever current release number):

[INDENT]gstreamer plugins-ugly
gstreamer plugins-ugly-multiverse
gstreamer plugins-bad
gstreamer plugins-bad-multiverse
gstreamer ffmpeg[/INDENT]
THAT should fix your little red wagon.

---

### Post by aeiah on 2009-03-30
yea you might as well try vlc. i use mplayer for all video though and it performs fine. what does the terminal spit out when the video plays? any errors at all? i think there are command line options to make mplayer reporting more verbose.

and as was mentioned you might want to make sure the videos aren't faulty. since its school they're probably encoded fine, but perhaps the download was corrupt.



for the sake of it id like to state that this wmv file works fine for me under ubuntu:

[http://home.att.net/~cherokee68/wmvtest.html](http://home.att.net/~cherokee68/wmvtest.html)

---

### Post by greenpepper on 2009-03-30
The video played just fine on my Windows computer yesterday, so yes, I am sure the file is good.

It does not play at all in VLC. 

I searched for gstreamer in Synaptic. I did not see plugins-ugly or plugins-bad, however, I already have all the Gstreamer packages that appear in Synaptic installed. 

I have also:

Verified that I have both universe and multiverse in in /etc/apt/sources.list 
Disabled all Desktop Effects

---

### Post by aeiah on 2009-03-30
god just hates you. sorry :(

i presume you've checked out [this bad boy?](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by greenpepper on 2009-03-30
> **aeiah said:**
> 

and as was mentioned you might want to make sure the videos aren't faulty. since its school they're probably encoded fine, but perhaps the download was corrupt.


Checksum is fine, so I don't think it's a corrupt download.

> 
for the sake of it id like to state that this wmv file works fine for me under ubuntu:

[http://home.att.net/~cherokee68/wmvtest.html](http://home.att.net/~cherokee68/wmvtest.html)

That one doesn't work for me either. I wish I knew what I am doing wrong!

---

### Post by Therion on 2009-03-30
> **aeiah said:**
> 

god just hates you. sorry :(
I hate to say this but from what you tell me, I'm almost inclined to agree.  Lets go to the scoreboard...

[INDENT]Ubuntu Restricted Extras installed... Check!
VLC Media Player installed...  Check!
Gstreamer Codec Packs installed...  Check!
w32codecs, libdvdcss2 and Mplayer all installed... Check![/INDENT]

And still nothing? This is sounding karmic.

---

### Post by greenpepper on 2009-03-30
> **aeiah said:**
> god just hates you. sorry :(

i presume you've checked out [this bad boy?](http://ubuntuforums.org/showthread.php?t=766683)

Yes, I have. 

As for mplayer output:

% mplayer -vo x11 7.wmv 
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 7.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 320 x 240 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 320x240 => 320x240 Planar YV12 
[swscaler @ 0x8935770]SwScaler: using unscaled yuv420p -> rgb32 special converter
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
GetOutput r=0x0   size:16384  align:1
StreamCount r=0x0  1  1
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   5.2 V:   5.2 A-V:  0.020 ct:  0.013   6/  6 ??% ??% ??,?% 0 0

---

### Post by greenpepper on 2009-03-30
> **Therion said:**
> I hate to say this but from what you tell me, I'm almost inclined to agree.  Lets go to the scoreboard...

[INDENT]Ubuntu Restricted Extras installed... Check!
VLC Media Player installed...  Check!
Gstreamer Codec Packs installed...  Check!
w32codecs, libdvdcss2 and Mplayer all installed... Check![/INDENT]

And still nothing? This is sounding karmic.


Especially after having the video card on my primary computer up and die on me. I think the universe wants me to drop this class!

So, all the software checklists are complete, and still nothing. I'm thinking possibly a hardware issue? This is an elderly Dell Vostro with an Nvidia video card. Unfortunately I am ubuntu-illiterate and don't know how to check the specific model of my video card.

---

### Post by greenpepper on 2009-03-30
This is going to sound completely moronic, since I come from the Windows world and rebooting should be my first instinct but:

I had to reboot after the Update Manager in the taskbar told me to (after updating some completely unrelated packages). And lo and behold! Mplayer works now. Erm, I am  not used to "reboot it to make it work" being the answer on non-Windows systems. 

I used [this advice]("http://ubuntuforums.org/showthread.php?t=140185&highlight=mplayer+fullscreen") to edit mplayer.conf to get it to play fullscreen, and now have no excuse to not do my homework.

Thank you everyone for your help.

---

### Post by llamabr on 2009-03-30
Sorry to come late to the conversation, but depending on the way you're trying to view them, firefox should put them in your /tmp directory, and call them Flash85ufjg or some such thing.

You can often navigate to that directory, and just run mplayer, or vlc, or xine on them.

Glad it's working.

---

