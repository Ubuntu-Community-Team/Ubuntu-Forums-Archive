---
title: "gtick metronome problem"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2010-10-01
I just installed gtick, a metronome program and i get the error ```
Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.
``` can anyone help me with this? i looked in /dev and there doesn't seem to be a file named dsp which is where the program is looking for its sound, i think...

---

### Post by Phil D. on 2010-10-01
A few ideas from the [GTick Site]("http://www.antcom.de/gtick/")

> Q: Sound doesn't work, what can I do?

Some ideas:

Make sure /dev/dsp* (e.g. /dev/dsp0) exists and GTick is configured to use it
Set the following volume controls to a high value: Master and PCM in your Mixer (e.g. gnome-alsamixer), and also the volume control in GTick. Don't forget to connect and switch on your speakers
Try another sound application that uses OSS (supported by ALSA in compatibility layer) to make sure your sound subsystem works
Try using the stock kernel that was shipped with your OS, in contrast to a self compiled one
Try using it with Debian (as I did when testing)
Try on another machine, maybe the sound hardware/driver is broken

---

### Post by e1ektrob0y on 2010-10-02
> **Phil D. said:**
> A few ideas from the [GTick Site]("http://www.antcom.de/gtick/")
yeah i checked that. the part where it says make sure /dev/dsp exists. it doesn't exist and i don't know how to make it exist. that is the problem. does anyone know how to create it and what sort of file it is supposed to be?

---

### Post by Phil D. on 2010-10-04
[http://ubuntuforums.org/showthread.php?t=859607]("http://ubuntuforums.org/showthread.php?t=859607")

Have a look in this thread - and try [this]("http://ubuntuforums.org/showpost.php?p=9622737&postcount=6")

---

### Post by e1ektrob0y on 2010-10-05
great, that worked. thankyou :)

---

### Post by dulbirakan on 2011-04-29
Adding padsp before the command worked for me too...

```
padsp gtick
```

You can also change the launcher so that you can launch it from the GUI

---

