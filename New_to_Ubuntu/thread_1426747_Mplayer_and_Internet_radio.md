---
title: "Mplayer and Internet radio"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by anandamide on 2010-03-10
OK, I must be missing something really basic from my configuration here:

I like listening to internet radio via the command line, partly because I can set up cron alarms easier. But since upgrading to 9.10 I can't invoke internet radio from the command line. Rythmbox is happy, mplayer-via-firefox is happy, and even totem from the command line is happy; but mplayer just gives:

```
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://www.gaydarradio.co.uk/listenlive/playlist.m3u?rate=128.
Resolving www.gaydarradio.co.uk for AF_INET...
Connecting to server www.gaydarradio.co.uk[85.158.9.14]: 80...
Cache size set to 320 KBytes
Cache fill:  0.04% (134 bytes)   


Exiting... (End of file)

```

Any ideas? I need an annoying dance music alarm!

---

### Post by andrew.46 on 2010-03-11
Hi anandamide,

> **anandamide said:**
> Any ideas? I need an annoying dance music alarm!

It is not all that annoying :).

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -playlist 'http://www.gaydarradio.co.uk/listenlive/playlist.m3u?rate=128'[/COLOR]**
Resolving www.gaydarradio.co.uk for AF_INET6...
Couldn't resolve name for AF_INET6: www.gaydarradio.co.uk
Resolving www.gaydarradio.co.uk for AF_INET...
Connecting to server www.gaydarradio.co.uk[85.158.9.14]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r30881-4.3.3 (C) 2000-2010 MPlayer Team

Playing http://mp31.gaydarradio.com/gaydarradio_high_1?memberid=&session=.
Resolving mp31.gaydarradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mp31.gaydarradio.com
Resolving mp31.gaydarradio.com for AF_INET...
Connecting to server mp31.gaydarradio.com[85.158.9.40]: 80...
Public : no
Bitrate: 128kbit/s
Cache size set to 320 KBytes
Cache fill:  2.50% (8192 bytes)   
ICY Info: StreamTitle='JES - Love Song ';
Cache fill: 15.00% (49152 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  10.5 (10.4) of -0.0 (unknown)  0.8% 24%

```

All the best,

Andrew

---

### Post by anandamide on 2010-03-16
Ahah! Thank you so much!

This goes to show how utterly disorganised I am - I actually plugged that workaround into an alias definition but after messing around with my bashrc I lost it and promptly forgot about it... nothing to do with Karmic at all.

Correlation, causation, whatever.

---

### Post by HermanAB on 2010-03-16
Howdy,

You should install streamtuner and streamripper.  That it the totally easiest way to find gazillions of internet radio stations.

---

### Post by andrew.46 on 2010-03-16
Hi anandamide,

> **anandamide said:**
> Ahah! Thank you so much!

No problems :). I hope that one day MPlayer will recognise playlists without the need to place *-playlist* in the commandline...

Andrew

---

