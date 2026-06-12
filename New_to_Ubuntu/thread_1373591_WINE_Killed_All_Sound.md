---
title: "WINE Killed All Sound"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by BarfBag on 2010-01-05
I have a friend who's having big trouble with WINE.  He switched the audio driver in WineCFG from ALSA to OSS.  Now, no sound is working.  Nothing, on his entire system.  He's running Ubuntu 9.04, and the latest development version of WINE.  Any idea how to fix this?  Thanks, in advance.

---

### Post by BarfBag on 2010-01-06
Bump.

---

### Post by Methuselah on 2010-01-06
Did he try switching it back to ALSA and restarting?
Maybe wine is trying to hold exclusive access to the sound device.
Most distributions use ALSA + PulseAudio these days not OSS.

---

### Post by adam814 on 2010-01-06
He might also want to run alsamixer in the terminal and make sure there aren't any muted sound channels.  I've had odd apps here and there mute my PCM channel and I get no sound until I un-mute it.

---

