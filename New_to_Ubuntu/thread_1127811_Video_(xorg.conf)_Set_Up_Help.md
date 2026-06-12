---
title: "Video (xorg.conf) Set Up Help"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by dougalg on 2009-04-16
Hi there, I have used linux before, although never Ubuntu, and have never had to set up video settings, hence my post in the beginner discussion, since I essentially know nothing about this. This is on Ubuntu 8.10, btw.

Currently, my school has no tech person, so I've been asked to set up the multimedia room computer. This is a NEC Valuestar something-or-other, with

Intel Corporation 82G965 Integrated Graphics Controller (rev 02)

The main monitor is a NEC but, unfortunately is from Japan so I can't find the monitor product line...

Additionally, we have connected to a TV/projector as a second monitor. I have been able to correctly set the NEC monitor to display properly, but when I try to set the TV output to 640x480 or 800x600, I get an error saying that I need to set my "virtual resolution". If I do this, it invariably makes no monitor function...

My xorg.conf looks like this:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

If you can give me any advice on where to head I'd be greatly appreciative. If we could use this projector (it's been defunct for a year now) I'd be soo happy!

Thanks!

---

### Post by dougalg on 2009-04-16
Update, here's the monitor is a NEC F20wZ20, but I can't find any detailed specs on it...

Also, I just noticed, that if I have the cable to the TV/Projector plugged in at startup, then the NEC monitor only recognizes standard width rather than wide-screen.

Cheers, and thanks!

---

