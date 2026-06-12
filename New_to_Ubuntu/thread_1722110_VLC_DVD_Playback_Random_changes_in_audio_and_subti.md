---
title: "VLC DVD Playback: Random changes in audio and subtitle tracks"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by gidra on 2011-04-05
I'm experiencing the following problem with VLC media player only; whenever I play a DVD from disc, at some point in time the audio and subtitle track automatically switch to some other track (so therefore I'm left without any audio and subs). I restore the tracks from the vlc menu and after some time it happens again.

I also notice that when the problem occurs, the list of audio and sub tracks is quite numerous (say 8 audio tracks which seem to crop up out of nowhere). I tried several discs which resulted in the same issue on playback. If I stop playback and restart the dvd, it initiates with one audio track(as it must) and the problem reoccurs at the same point in time. I'd greatly appreciate some kind of help

---

### Post by Daniel0108 on 2011-04-05
> **gidra said:**
> I'm experiencing the following problem with VLC media player only; whenever I play a DVD from disc, at some point in time the audio and subtitle track automatically switch to some other track (so therefore I'm left without any audio and subs). I restore the tracks from the vlc menu and after some time it happens again.

I also notice that when the problem occurs, the list of audio and sub tracks is quite numerous (say 8 audio tracks which seem to crop up out of nowhere). I tried several discs which resulted in the same issue on playback. If I stop playback and restart the dvd, it initiates with one audio track(as it must) and the problem reoccurs at the same point in time. I'd greatly appreciate some kind of help

Try installing another media player and tell me if it works, I think this problem has to do with VLC.

Yours,
Daniel

---

### Post by gidra on 2011-04-05
Thanks Daniel for getting back. As I already said I have only experienced this trait in VLC. I tried DVD playback on other players, which I'm sorry to say they don't compare to VLC (more functionality and portability). So I'd prefer to stick to VLC an try to find a solution to the problem, I'm sure there should be some tweak or something which resolves the issue at hand.

---

### Post by Daniel0108 on 2011-04-05
> **gidra said:**
> Thanks Daniel for getting back. As I already said I have only experienced this trait in VLC. I tried DVD playback on other players, which I'm sorry to say they don't compare to VLC (more functionality and portability). So I'd prefer to stick to VLC an try to find a solution to the problem, I'm sure there should be some tweak or something which resolves the issue at hand.

oh okay, try:
```
sudo apt-get remove vlc && sudo apt-get update && sudo apt-get install vlc
```
to remove vlc and install the latest version of vlc :)

Yours,
Daniel

---

### Post by gidra on 2011-04-05
Tried that my friend. Still no go

---

