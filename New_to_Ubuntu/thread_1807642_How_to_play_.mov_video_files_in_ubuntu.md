---
title: "How to play .mov video files in ubuntu?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Prescilla on 2011-07-19
I have tried playing a .mov video file with vlc but all i get was the audio no video. When I tried playing the same .mov video file with banshee and totem movie player it played the video but no audio. Can anyone suggest or recommend a video player for ubuntu that plays .mov file? By the way I know .mov is a container, the video file i am trying to view/play has Apple Graphics (smc) codec.

---

### Post by androssofer on 2011-07-19
got restricted extras installed?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by raja.genupula on 2011-07-19
[http://ubuntuforums.org/showthread.php?t=969051](http://ubuntuforums.org/showthread.php?t=969051)

---

### Post by jepong on 2011-08-03
I highly recommend to add the medibuntu repos ([http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)) and install non-free-codecs.

---

### Post by Prescilla on 2011-08-11
Yes, I have restricted areas installed. I tried using mplayer but there's still no video only the audio. When i add -demuxer mov it played the video but the audio was gone. Please can someone help me. I need to be able to watch these tutorials coz I need it at school.

---

### Post by andrew.46 on 2011-08-11
> **Prescilla said:**
> I need to be able to watch these tutorials coz I need it at school.

Can you give a link to one of these tutorials? Certainly MPlayer should have no trouble with the video:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i 'smc'[/COLOR]**
ffsmc       ffmpeg    working   Apple Graphics (SMC) codec  [smc]

```

as you have already found, it would be interesting to know what audio is contained.

---

### Post by jepong on 2011-08-12
> **Prescilla said:**
> Yes, I have restricted areas installed. I tried using mplayer but there's still no video only the audio. When i add -demuxer mov it played the video but the audio was gone. Please can someone help me. I need to be able to watch these tutorials coz I need it at school.

have you tried watching using VLC? VLC plays lots of video formats. Hopefully it can play .mov.

---

