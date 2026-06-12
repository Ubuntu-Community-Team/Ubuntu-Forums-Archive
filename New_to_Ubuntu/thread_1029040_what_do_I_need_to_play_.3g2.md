---
title: "what do I need to play .3g2"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by jayef on 2009-01-03
I tried VLC, Totem, and mplayer. None of which would play the videos I have that are .3g2 I have mplayer right now, and would just be fine staying with that. But if I need to switch again, that'd be fine.
I've looked through some other posts, but couldn't find anything that worked out exactly to what the problem I had, although I may have missed a post, in which case sorry :P
Also, I'm running Ubuntu 8.10
Thanks in advance!

---

### Post by andrew.46 on 2009-01-03
Hi jayef,

There are a few choices here and the best may be to get hold of the version of MPlayer that is held in the Medibuntu repositories. This is a more fully featured version and should be able to play your files.

To enable the Medibuntu Reposiories have a look at this page:

------------------------------------------------------
Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
------------------------------------------------------

and when this is done run:

```
$ sudo apt-get install mplayer
```

Can I suggest a slightly different tack as well? The gui for MPlayer is pretty bad. If you are interested in a better gui try the following instead:

```
$ sudo apt-get install mplayer-nogui smplayer
```

Hope this helps? BTW could someone congratulate me for my 1,000th post on these forums :-).

Andrew

---

### Post by jayef on 2009-01-03
First of all congradulations on your 1,000th post!!
I'm truly happy to be apart of it :)

Second, I like the gui but the problem persists. Also, this happened before I just forgot to mention it. But at points in the videos that do play, the video will lag at points and screw the audio/video synch. I can correct the lag by clicking in the timeline, but that tends  to get annoying and I'd rather fix it a different way.

---

### Post by andrew.46 on 2009-01-03
Hi jayef,

> **jayef said:**
> First of all congradulations on your 1,000th post!!
I'm truly happy to be apart of it :)

It is something of a milestone :-).

> Second, I like the gui but the problem persists. Also, this happened before I just forgot to mention it. But at points in the videos that do play, the video will lag at points and screw the audio/video synch. I can correct the lag by clicking in the timeline, but that tends  to get annoying and I'd rather fix it a different way.

Hmmm.... I wonder if you could run the following command in a terminal on one of these troublesome files:

```
$ mplayer -identify -frames 0 **[COLOR="Red"]yourfile.3gp[/COLOR]**
```

and paste the whole result, including the command into a post? This will give some information on the file itself and a little bit about the copy of MPlayer that you are using. Of course you need to make the obvious substitution of *your own* filename where I have put **[COLOR="Red"]yourfile.3gp[/COLOR]** :-).

All the best,

Andrew

**Edit:** Perhaps you could also take a look at the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") which has been very popular? It is not an approach I use myself but 200,000 page views cannot be wrong :-).

---

### Post by jayef on 2009-01-03
> and paste the whole result, including the command into a post?

$ mplayer -identify -frames 0 1203081512.3g2
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 1203081512.3g2.
File not found: '1203081512.3g2'
Failed to open 1203081512.3g2.


Exiting... (End of file)

I will also add that the video plays. It's just the audio that is lacking.

---

### Post by andrew.46 on 2009-01-04
Hi jayef,

> **jayef said:**
> $ mplayer -identify -frames 0 1203081512.3g2 [...]
[B][COLOR="Red"]Playing 1203081512.3g2.
File not found: '1203081512.3g2'
Failed to open 1203081512.3g2.[/COLOR][/B]

Unfortunately you may have misfired a little and missed the correct path to your file :-).

> I will also add that the video plays. It's just the audio that is lacking.

The audio must either be aac or amr_nb and support for both of these is missing from your copy of MPlayer. Did you manage the Medibuntu version of MPlayer? This would be your safest bet as well as going through Nathan's guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

All the best,

Andrew

**Edit:** You might be interested to see the results of the newest svn MPlayer with a typical h263 / amr_nb file:

```

andrew@skamandros:~/Desktop$ mplayer shakingthe_luqbp387.3gp 
MPlayer dev-SVN-r28239-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing shakingthe_luqbp387.3gp.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [s263]  176x144  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
**[COLOR="Red"]Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+ decoder)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 0.0 kbit/0.00% (ratio: 0->16000)
**[COLOR="Red"]Selected audio codec: [ffamrnb] afm: ffmpeg (AMR Narrowband)[/COLOR]**
==========================================================================
AO: [oss] 8000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 176x144 => 192x144 Planar YV12 
A:  59.1 V:  59.1 A-V:  0.000 ct: -0.000   0/  0  0%  0%  0.4% 1 0 

Exiting... (End of file)
andrew@skamandros:~/Desktop$ 

```

---

