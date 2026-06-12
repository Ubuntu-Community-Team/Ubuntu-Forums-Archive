---
title: "Sound is almost inaudibly quiet after fresh install"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Tyrsius on 2009-07-25
Just made a fresh install of 9.04, never had this issue before. The sound is so quiet that even with all bars maxed and my ear ON the speaker, I can barely hear anything. I am not sure where to go from here. A number of guides obviouisly exist on this, but I have had trouble using most, and the rest have failed.

Output from aplay -l
NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]

Output from cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC662 rev1

Output from cat /proc/asound/card0/pcm0c/info
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC662 Analog
name: ALC662 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1


If I need to post anything else, just ask. Something is installed, or I wouldn't hear any sound at all. I'm guessing its just a configuration issue, but I don't know how to adjust that other than the ALSA mixer, which I have maxed out already.

---

### Post by Tyrsius on 2009-07-26
anyone?

---

### Post by credobyte on 2009-07-26
Terminal:
```
alsamixer

```

Feel free to play with your sound settings & let us know if changing equalizer settings helped or not !

---

### Post by Tyrsius on 2009-07-26
> **credobyte said:**
> Terminal:
```
alsamixer

```

Feel free to play with your sound settings & let us know if changing equalizer settings helped or not !

Ive already tried this. With all bars maxed and nothing muted, I am only barely able to hear with my ear pressed against the speakers.

---

### Post by Tyrsius on 2009-07-26
still looking for a solution to this, if anyone can help

---

### Post by mc4100 on 2009-07-26
Pulseaudio might be getting in the way, hiding the "real" mixer.
```
alsamixer -Dhw
```

---

### Post by StarkGläubige on 2009-09-20
Hi there,

I have the same very output as Tyrsius from the commands

```
lsmod | grep snd
cat /proc/asound/card0/codec#* | grep Codec
cat /proc/asound/card0/pcm0c/info
```

But my problem is a little bit different. When I'm running Rhythmbox, Amarok or Exaile alone, the music plays well. But when I'm running more apps at the same time, the music runs normal, faster, normal, faster and jumps sometimes. I don't know how to explain, except that the quality is very bad. How do I set priority in the use of the RAM to these kind of apps? Can anyone help me?

Thanks.

---

### Post by callumacrae on 2009-09-20
I had this exact problem.

The problem was the mixer levels for me, try checking all the other tabs and stuff.

~Callum

---

