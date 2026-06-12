---
title: "Sound stopped working"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by knoelle on 2009-01-18
My sound suddenly stopped working.
I've been troublshooting and I'm stuck.

I un-installed everything via
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

and then re-installed via
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

however, this is my result
> charlie@charlie-laptop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-sound-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-sound-base has no installation candidate


I tried to look up the alsa driver BUT it says my chip set isn't supported. 

Which is where I hit a dead end because it seems like every sound troubleshooting anything says I'm SOL here.

If I really and truly am then I will simply wait until the driver comes out. BUT I would like to know why my sound was working previously and then all-of-a-sudden decided to quit on me.

here's my audio device information:
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

        Subsystem: Dell Device 022f

        Flags: bus master, fast devsel, latency 0, IRQ 21

        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>

        Kernel driver in use: HDA Intel

        Kernel modules: snd-hda-intel


Thank you for any help


NOTE: I tried to reboot after it wouldn't re-install but that caused my system to boot into the terminal (which I got help with) I just wanted to add that in case it was significant or pertinent

---

