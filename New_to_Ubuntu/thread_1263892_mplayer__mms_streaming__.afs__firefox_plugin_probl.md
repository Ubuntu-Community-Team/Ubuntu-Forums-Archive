---
title: "mplayer / mms streaming / .afs / firefox plugin problem"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Inge_k on 2009-09-11
Hi all,

Sorry for my rather general title, but the more I search, the less I know where the problem is.

I want to play this stream (Dutch TV) with Mplayer: [http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf](http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf)

With the firefox plugin, I first get a gray screen, then when I right-click and say "play", it says Getting Playlist, then something I can't read, because it soon says "Stopped" and that's it.

In the mplayer GUI, I get the error: "Couldn't resolve name for AF_INET06:cgi.omroep.nl"

When running from a terminal, I get:
[FONT=Courier New]inge@ubuntu:~$ mplayer [http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf](http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf)
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Atom(TM) CPU N280   @ 1.66GHz (Family: 6, Model: 28, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf](http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf).
Resolving cgi.omroep.nl for AF_INET6...
Couldn't resolve name for AF_INET6: cgi.omroep.nl
Resolving cgi.omroep.nl for AF_INET...
Connecting to server cgi.omroep.nl[145.58.30.12]: 80...
STREAM_ASF, URL: [http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf](http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf)
Resolving cgi.omroep.nl for AF_INET6...
Couldn't resolve name for AF_INET6: cgi.omroep.nl
Resolving cgi.omroep.nl for AF_INET...
Connecting to server cgi.omroep.nl[145.58.30.12]: 80...
Stream not seekable!


Exiting... (End of file)

[/FONT][FONT=Verdana]It plays well in Windows Media Player and I had it sort of running in Ubuntu with VLC (but wasn't satisfied because I had no control environment or what-do-you-call-it, sliders and start-stop buttons etc).

I thought it might be something with the w32codecs package but my system can't find a package with that name? (All repositories but source code included) In all my attempts I downloaded a lot of other stuff in which I think it was included anyway.

Your help would be greatly appreciated. Any other recommendations for multimedia players are welcome too, just want something that plays everything (as VLC seemd to do) and that I can pause or forward easily if I want to ;-)

Thanks in advance!

EDIT: To clarify, I read some places where people are able to watch the stream after the "[/FONT][FONT=Courier New]Couldn't resolve name for AF_INET6"[/FONT][FONT=Verdana] message. I cannot. Also, I read this: [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841) but that may be outdated, because I don't have a [/FONT]*/etc/modprobe.d/aliases *to edit..

---

### Post by andrew.46 on 2009-09-11
Hi Inge_k,

The good news is that MPlayer can play that stream quite easily, I attach a screenshot of my own copy playing it quite happily. By default MPlayer will use an external codec for this as you suspected (in the screenshot you will see wmv9dmo being loaded for the video) and to find this you need to manually add the Medibuntu repositories. Details of how to do this are here:

Medibuntu - Ubuntu Community Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and then run:

```
sudo apt-get install w32codecs
```

Hopefully you are not running a 64bit installation? Mind you if your copy of MPlayer was a little more recent you would not need these codecs as there is a native implementation:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc ffwmv3 -cache 2048 -cache-min 80 'http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf'[/COLOR]**
MPlayer SVN-r29665-4.3.3 (C) 2000-2009 MPlayer Team

Playing http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf.
Resolving cgi.omroep.nl for AF_INET6...
Couldn't resolve name for AF_INET6: cgi.omroep.nl
Resolving cgi.omroep.nl for AF_INET...
Connecting to server cgi.omroep.nl[145.58.30.12]: 80...
STREAM_ASF, URL: http://cgi.omroep.nl/legacy/player?/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf
Resolving cgi.omroep.nl for AF_INET6...
Couldn't resolve name for AF_INET6: cgi.omroep.nl
Resolving cgi.omroep.nl for AF_INET...
Connecting to server cgi.omroep.nl[145.58.30.12]: 80...


Playing mms://wm-ondemand07.omroep.nl/ug-ondemand-wm3/wm3c1/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf.
STREAM_ASF, URL: mms://wm-ondemand07.omroep.nl/ug-ondemand-wm3/wm3c1/ceres/ncrv/rest/2009/NCRV_1342084/bb.20090908.asf
Resolving wm-ondemand07.omroep.nl for AF_INET6...
Couldn't resolve name for AF_INET6: wm-ondemand07.omroep.nl
Resolving wm-ondemand07.omroep.nl for AF_INET...
Connecting to server wm-ondemand07.omroep.nl[145.58.33.13]: 1755...
Connected
unknown object
file object, packet length = 6250 (6250)
unknown object
unknown object
unknown object
stream object, stream ID: 1
stream object, stream ID: 2
unknown object
data object
mmst packet_length = 6250
Cache size set to 2048 KBytes
Cache fill: 78.91% (1654784 bytes)   
ASF file format detected.
[asfheader] Video stream found, -vid 1
[asfheader] Audio stream found, -aid 2
VIDEO:  [WMV3]  320x180  24bpp  1000.000 fps  452.0 kbps (55.2 kbyte/s)
Clip info:
 title: 
==========================================================================
[B][COLOR="Red"]Forced video codec: ffwmv3
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==============================================================[/COLOR][/B]============
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 180 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x180 => 320x180 Planar YV12 
A:   7.2 V:   7.2 A-V: -0.004 ct: -0.043  83/ 83  4%  0%  0.5% 1 0 87% 
Exiting... (Quit)

```

All the best with this :)

Andrew

---

### Post by Inge_k on 2009-09-13
Thank you Andrew, I got a bit further (I think) but still haven't got it running..

I had the Meditubuntu repositories added already, without knowing that what I installed where repositories from which I could get the package. I installed the w32 codecs now and rebooted, but still have the same error ("Stream not seekable"). Uh?

How do I check if I have a 32 bit or 64 bit installation?

---

### Post by Inge_k on 2009-09-13
BTW, the installing of the w32codecs was definitely successful; I am now able to listen to streamed radio.. That didn't work at first either :)

EDIT: Even more successes: I got the video streams running in Kaffeine now. And the website itself offers some help for Ubuntu users too, they recommend Moonlight.

So if it is just mplayer not liking me, I can put up with that.

---

### Post by andrew.46 on 2009-09-13
Hi Inge_k,

> **Inge_k said:**
>  I got the video streams running in Kaffeine now. And the website itself offers some help for Ubuntu users too, they recommend Moonlight.

So if it is just mplayer not liking me, I can put up with that.

Well, it sounds like success of a sort anyway :). There could be a couple of reasons why MPlayer is not working but of you can see your streams in another player...

Andrew

---

