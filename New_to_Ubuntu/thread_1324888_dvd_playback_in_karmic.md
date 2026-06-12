---
title: "dvd playback in karmic"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-11-12
I installed ubuntu restricted and I get an error while trying to play dvds, when I run vlc from terminal. I get this error.

libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0005878e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00398c9e
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[0x9703f28] main input error: ES_OUT_RESET_PCR called
[0x9703f28] main input error: ES_OUT_RESET_PCR called
libdvdnav: Suspected RCE Region Protection!!!
[0x9703f28] main input error: ES_OUT_RESET_PCR called
[0x9703f28] main input error: ES_OUT_RESET_PCR called

---

### Post by JDShu on 2009-11-13
The actual error makes it sound like the region of your DVD and DVD drive don't match.

---

### Post by LunaticHiatus on 2009-11-13
hm, how do I set the region for my dvd drive?

---

### Post by LunaticHiatus on 2009-11-13
when I run it from terminal using totem, I get this:


libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
** Message: no file info
** Message: Error: Could not read from resource.
resindvdsrc.c(1103): rsn_dvdsrc_step (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Error reading from DVD.

---

### Post by wojox on 2009-11-13
Try:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

That's how I got mine working in vlc.

---

### Post by LunaticHiatus on 2009-11-13
> **wojox said:**
> Try:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

That's how I got mine working in vlc.


didn't work at first, rebooted and updated and it worked. Many thanks.

---

