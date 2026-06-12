---
title: "PulseAudio Issues"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by skymera on 2010-02-27
Hi

PulseAudio doesn't start correctly during boot or login. Only recently has this been happening.

To temporarily solve the issue I need to delete the .pulse folder in my /home then kill X and log back in. Only after this, does PulseAudio work.

I use the PulseAudio equalizer from a PPA, though I don't think this would be the reason.

Anyone else experiencing this?

---

### Post by Psumi on 2010-03-16
Switch to alsa?

Unless you need pulseaudio for some special reason (IE: GTK-Recordmydesktop) then there isn't really any use for it.

---

### Post by ibuclaw on 2010-03-16
Check what applications are using the sound device:

```
sudo lsof /dev/snd/*
```

Typically, this is what you will see with pulseaudio:
```

COMMAND     PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi  2137 jstdio   22u   CHR  116,0      0t0 4108 /dev/snd/controlC0
pulseaudi  2137 jstdio   29u   CHR  116,0      0t0 4108 /dev/snd/controlC0

```

If different, please post here.

Regards
Iain

---

### Post by psyke83 on 2010-03-20
> **skymera said:**
> Hi

PulseAudio doesn't start correctly during boot or login. Only recently has this been happening.

To temporarily solve the issue I need to delete the .pulse folder in my /home then kill X and log back in. Only after this, does PulseAudio work.

I use the PulseAudio equalizer from a PPA, though I don't think this would be the reason.

Anyone else experiencing this?

The equalizer actually can cause this problem (if you're using the "Keep Settings" option).

The next time it happens, and before you delete the ~/.pulse folder, generate some debug output:

```
$ pulseaudio-equalizer debug
```

---

### Post by skymera on 2010-03-20
> **psyke83 said:**
> The equalizer actually can cause this problem (if you're using the "Keep Settings" option).

The next time it happens, and before you delete the ~/.pulse folder, generate some debug output:

```
$ pulseaudio-equalizer debug
```

Yes, i realised this not long ago, i wasn't entirely sure if this was the case though.

I set the equalizer manually ever time i use Ubuntu now.

Thanks for confirming this! :D

---

