---
title: "cant get NSV File to play"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Cpyles07 on 2009-02-10
I been trying to play a NSV file but in mplayer i Get video but no audio and vlc I get audio but no video am i missing a codec or somthing?? Any help is appreciated thanks:)

---

### Post by andrew.46 on 2009-02-10
Hi,

Try this sample file:

```
wget http://download.nullsoft.com/nsv/samples/witchblade-213kbps.nsv
```

which FFmpeg identifies as:

```
Input #0, nsv, from 'witchblade-213kbps.nsv':
Duration: 00:01:00.42, start: 0.000000, bitrate: 213 kb/s
Stream #0.0: **[COLOR="Red"]Video: vp3[/COLOR]**, yuv420p, 320x240, 29.97 tb(r)
Stream #0.1: **[COLOR="Red"]Audio: mp3[/COLOR]**, 22050 Hz, mono, s16, 24 kb/s
```

MPlayer and FFplay had no trouble with this one, I attach a screenshot of SMPlayer playing it. If your copy of MPlayer fails with this file can you post the results of:

```
mplayer -v witchblade-213kbps.nsv
```

Andrew

---

### Post by Cpyles07 on 2009-02-10
Thanks for the reply. I just decided to get it in another format. Never really liked nsv anyways.

---

