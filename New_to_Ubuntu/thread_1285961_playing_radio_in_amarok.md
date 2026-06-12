---
title: "playing radio in amarok"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-08
Hi
Got amarok 2.2. Can anyone help me get it to play bbc radio 1? :)
I've tried add stream-> [http://www.bbc.co.uk/radio/listen/live/r1.asx](http://www.bbc.co.uk/radio/listen/live/r1.asx)
When i try and play it though amarok crahes.

---

### Post by andrew.46 on 2009-10-09
Hi Falc7,

I am not such a big fan of Amarok so unfortunately I cannot help out there. The stream itself though plays well enough with MPlayer if you were interested in trying that at some stage:

```

andrew@skamandros~$ [COLOR="Red"]**mplayer -playlist http://www.bbc.co.uk/radio/listen/live/r1.asx**[/COLOR]
[...]
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: BBC Radio 1
 author: BBC Radio 1
 copyright: British Broadcasting Corporation Copyright 2009, all rights reserved.
 comments: BBCMEDR108
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:57748.3 (16:02:28.3) of 2133437440.0 (-24.-8)  0.4% 13%

```

I have snipped some of the MPlayer output as there is some pretty complex navigation before the stream is found.

Andrew

---

### Post by Falc7 on 2009-10-10
ah yes, i've got the stream playing in vlc now, so i guess its just a big with amarok

---

### Post by mc4man on 2009-10-10
Noting that this is on karmic

While I'm no fan at all of amarok2 I have it on a tester and bbc radio 1 seems to play ok (takes awhile to load), used playlist -> add stream initially.
Does seem to be some inconsistencies with amarok2, found best way to reload was thru a m3u.

On my real karmic install I use amarok 1.4  where it was very easy to add to 'radio streams' and loads right up.

m3u that works here (at least today

```
#EXTM3U
#EXTINF:0,BBC Radio 1
mms://wmlive.bbc.net.uk/wms/bbc_ami/radio1/radio1_bb_live_int_eq1_sl0?bbc-uid=94ca3d30ce460f700b59f972212a947f3d4178dca0b041b444df09e75c42dab1&sso2-uid=

```

---

### Post by Falc7 on 2009-10-11
Ah thats working now, is there some way to save this stream so i don't have to copy/paste it every time i want to listen to the radio?

---

