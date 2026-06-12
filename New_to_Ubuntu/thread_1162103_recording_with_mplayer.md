---
title: "recording with mplayer"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by jobyzz on 2009-05-17
hey...anyone know how to record an audio stream using mplayer and have it in mp3 format?
thanks

---

### Post by logos34 on 2009-05-17
if it's an .mp3 internet radio stream:
> 
$ mplayer <URL> -dumpstream -dumpfile stream.mp3

---

### Post by andrew.46 on 2009-05-18
and if it is *not* an mp3 stream save it as wav:

```
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
```

and *then* convert it to mp3 with lame.

Andrew

---

