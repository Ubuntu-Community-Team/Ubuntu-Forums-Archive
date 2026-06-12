---
title: "sound problem"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by rejith on 2009-07-25
i am a user of ubuntu ultimate ,my sound driver is detected while hardware testing but no beep sound is producing at that time .also i can't play music in some players like amaroke,xine,etc.the error message is the output device is busy...

---

### Post by zeroseven0183 on 2009-07-25
Restart PulseAudio using the Terminal:
```
sudo killall pulseaudio
```

Then press Alt+F2 and type: **pulseaudio**

I also found same issues that were resolved. Check out these three links:

1. [Launchpad: Audio output unavailable; the device is busy.]("https://answers.launchpad.net/ubuntu/+source/amarok/+question/8271")
2. [Amarok: audio output unavailable; the device is busy]("http://ubuntuforums.org/showthread.php?t=825668")
3. [audio output unavailable - the device is busy]("http://ubuntuforums.org/archive/index.php/t-1011613.html")

Let us know if sound is OK.

By the way, I don't think there's Ubuntu Ultimate. We're talking Linux here not Microsoft.
Maybe --- Ultimately, Ubuntu!

---

