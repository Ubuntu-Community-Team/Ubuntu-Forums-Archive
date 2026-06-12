---
title: "Ubuntu's latest feature: system freeze for alsa's snd-sb16 module?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by abben on 2009-01-01
Forgive the title, those of you who are less frustrated than me, but Ubuntu had been running brilliantly for my old 800 mghz computer for a couple of years, only to change now. For a while I had one of the 2006 versions of ubuntu (I'm pretty sure 6.04), everything working perfectlym but now with the intrepid ibex, the whole computer utterly freezes after a few seconds audio playback.

Here is what I know
- Common to all ubuntu intrepid distros I have tried- Ubuntu, Xubuntu, even the ubuntu-based Mint Linux
- Not a problem with pulseaudio (Xubuntu doesn't use pulseaudio and I have the same problem), and it's not a problem with having the wrong driver (after all, I am getting perfect audio anywhere from 5 seconds to ten minutes before a crash).
- my sound card is never auto-detected, I always have to add it manually.

A possible hint???: the red "busy cpu" light is on when it freezes, always. 

Another hint?: I am not 100% confident that snd-sb16 is the proper module. However, it has worked for at least a year on a previous install without any problems. Is it possible that specifying the wrong module would lead to actual playback, but then a system freeze?

Any help or guesses whatsoever are appreciated.

---

### Post by nebu on 2009-01-01
myabe its compiz.... itll be kind of processor hungry...

---

### Post by Delever on 2009-01-01
> **nebu said:**
> myabe its compiz.... itll be kind of processor hungry...

My guess is that module may be not fully compatible now. Have you tried google?

---

### Post by abben on 2009-01-01
> **Delever said:**
> My guess is that module may be not fully compatible now. Have you tried google?

I have. I have only seen that other people also do not get sb-16 detected by default, but not that they experience the same problem that I am, of sound freezing the system.

---

### Post by kostkon on 2009-01-01
> **abben said:**
> Here is what I know
- Common to all ubuntu intrepid distros I have tried- Ubuntu, Xubuntu, even the ubuntu-based Mint Linux
- Not a problem with pulseaudio (Xubuntu doesn't use pulseaudio and I have the same problem), and it's not a problem with having the wrong driver (after all, I am getting perfect audio anywhere from 5 seconds to ten minutes before a crash).
Are you sure? I think Xubuntu uses PulseAudio. 

Nevertheless, you could check your logs for clues, especially syslog.

Another possibility is that the card is faulty...
> **abben said:**
> - my sound card is never auto-detected, I always have to add it manually.
Yes, because it is an ISA card, it is not auto-detected. You have to add the *snd-sb16* module to your */etc/modules* file. For more information check [here]("https://help.ubuntu.com/community/HowToSetupSoundCards"), it is easy to fix this.
> **abben said:**
> A possible hint???: the red "busy cpu" light is on when it freezes, always.
Then it seems that the cause of your crashes is not the sound card (or better say, not the driver) but something else. Again, try to check your logs for any error messages.
> **abben said:**
> Another hint?: I am not 100% confident that snd-sb16 is the proper module. However, it has worked for at least a year on a previous install without any problems. Is it possible that specifying the wrong module would lead to actual playback, but then a system freeze?

Any help or guesses whatsoever are appreciated.
Hmmm, I don't really know, if using the wrong module/driver can lead to crashes. Anyway, you could try other modules, the full list is given on the page I have posted above.

But, which card do you have? Try giving
```
aplay -l
```
in a terminal.

---

### Post by abben on 2009-01-01
> **kostkon said:**
> Are you sure? I think Xubuntu uses PulseAudio.

I'm pretty sure. The pulseaudio packages were not installed on my xubuntu computer until I manually added them. Also, lack of pulseaudio is mentioned in most all of the Pulseaudio troubleshooting guides you find in this forum and on the blogs.

> Yes, because it is an ISA card, it is not auto-detected. You have to add the snd-sb16 module to your /etc/modules file. For more information check here, it is easy to fix this.

Though I didn't mention it, I have done that already, hence my ability to play sound, which subsequently leads to the lockup.

> aplay -l
It just gives a description of my soundcard:
```
**** List of PLAYBACK Hardware Devices ****
card 0: S16 [Sound Blaster 16], device 0: SB16 DSP [DSP v4.13]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


> Then it seems that the cause of your crashes is not the sound card (or better say, not the driver) but something else. Again, try to check your logs for any error messages.
Ok. This would make sense.

The error logs were really interesting. This was right before the last crash:

```
Jan  1 05:08:50 abben-desktop last message repeated 9 times
Jan  1 05:09:44 abben-desktop last message repeated 8 times
Jan  1 05:10:54 abben-desktop last message repeated 3 times
Jan  1 05:12:23 abben-desktop modprobe: WARNING: Not loading blacklisted module ipv6
Jan  1 05:12:32 abben-desktop last message repeated 2 times
Jan  1 05:17:01 abben-desktop /USR/SBIN/CRON[5741]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Something about a blacklisted module ipv6, and its a warning being given by modprobe, which I used to configure the sound. It doesn't look related to sound itself, but I'll take a look.

---

