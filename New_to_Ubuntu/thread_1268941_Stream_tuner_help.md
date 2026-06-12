---
title: "Stream tuner help"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by RabbitWho on 2009-09-17
Hi hi

How do I get the URL of the streams I want to listen to? 

So for example [http://www.rte.ie/radio/index.html](http://www.rte.ie/radio/index.html) 

The radio stations are on the right, how do I find their URLs? 

RealPlayer isn't working for me. (installed it from bin, probably did a crap job of that) 

Thanks!


(Sorry if this is in the wrong forum.

---

### Post by arochester on 2009-09-17
If you install the Medibuntu Repository than you can install Realplayer 10 through Synaptic.

Try [http://www.listenlive.eu/ireland.html](http://www.listenlive.eu/ireland.html) . RIGHT click on Listen Live and choose Copy Link Location

---

### Post by RabbitWho on 2009-09-17
> **arochester said:**
> If you install the Medibuntu Repository than you can install Realplayer 10 through Synaptic.

Try [http://www.listenlive.eu/ireland.html](http://www.listenlive.eu/ireland.html) . RIGHT click on Listen Live and choose Copy Link Location

Hmmm... Got those links already from right clicking the link on the main website, they don't seem to work in stream tuner. 

No way to do this without real player?

---

### Post by andrew.46 on 2009-10-09
Hi Rabbit,

> **RabbitWho said:**
> How do I get the URL of the streams I want to listen to? 
So for example [http://www.rte.ie/radio/index.html](http://www.rte.ie/radio/index.html) 


If you right-click on these urls, 'copy link' and paste the results you will see something like this:

```

javascript:showPlayer('/radio/liveplayer2_av.html?1_real,**[COLOR="Red"]http://dynamic.rte.ie/av/live/radio/radio1.smil[/COLOR]**,real,200')

```

I have highlighted the actual address in red and this plays well enough in MPlayer:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -playlist http://dynamic.rte.ie/av/live/radio/radio1.smil[/COLOR]**
Resolving dynamic.rte.ie for AF_INET6...
Couldn't resolve name for AF_INET6: dynamic.rte.ie
Resolving dynamic.rte.ie for AF_INET...
Connecting to server dynamic.rte.ie[89.207.56.82]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r29756-4.3.3 (C) 2000-2009 MPlayer Team

Playing **[COLOR="Red"]rtsp://live1.rte.ie/redundant/1516.ra[/COLOR]**.
Resolving live1.rte.ie for AF_INET6...
Couldn't resolve name for AF_INET6: live1.rte.ie
Resolving live1.rte.ie for AF_INET...
Connecting to server live1.rte.ie[89.207.56.7]: 554...
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Clip info:
 copyright: (C) 2004
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4005->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:940661.9 (261:17:41.9) of 0.0 (unknown)  0.7% 18% 

```

I have outlined here as well the *real* address of the stream which MPlayer can also play *directly*:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer rtsp://live1.rte.ie/redundant/1516.ra[/COLOR]**
MPlayer SVN-r29756-4.3.3 (C) 2000-2009 MPlayer Team

Playing rtsp://live1.rte.ie/redundant/1516.ra.
Resolving live1.rte.ie for AF_INET6...
Couldn't resolve name for AF_INET6: live1.rte.ie
Resolving live1.rte.ie for AF_INET...
Connecting to server live1.rte.ie[89.207.56.7]: 554...
Cache size set to 640 KBytes
Cache fill: 18.75% (122880 bytes)   
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Clip info:
 copyright: (C) 2004
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4005->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:940911.4 (261:21:51.3) of 0.0 (unknown)  0.7% 18%

```

I guess you could try plugging either one of those addresses into vlc or your favourite stream player, I am not familiar with stream tuner I'm afraid. BTW I love the accents on those streams :).

Andrew

---

