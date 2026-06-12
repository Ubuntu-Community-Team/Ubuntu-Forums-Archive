---
title: "No Sound, 8.10, Toshiba Satellite"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by atngplusultra on 2008-12-21
This is all happening on Intrepid, running on a Toshiba Satellite a135-s4677

It started when I realized that I had no sound thru headphones. I remembered that under 7.10, I had to download some old alsa drivers to get this to work, so, I constantly tried to do that all night.
However, in the meantime, something somewhere went wrong (I probably should've taken notes as to what steps I took) and now I have no sound at all.

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

```
aplay: device_list:215: no soundcards found...
```

and, no matter which drivers I try to install (be they old or the most recent), I get this error:
```

sudo make
make dep
make[1]: Entering directory `/home/andrew/alsa-driver-1.0.14'
make[2]: Entering directory `/home/andrew/alsa-driver-1.0.14/acore'
copying file alsa-kernel/core/init.c
/home/andrew/alsa-driver-1.0.14/utils/patch-alsa: 24: patch: not found
make[2]: *** [init.c] Error 1
make[2]: Leaving directory `/home/andrew/alsa-driver-1.0.14/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/andrew/alsa-driver-1.0.14'
make: *** [include/sndversions.h] Error 2
```

So, in all likelihood, it's a soundcard issue, but, the only thing I can think to do is reinstall Intrepid.

thanks.

---

### Post by 73ckn797 on 2008-12-21
I will assume that you already tried to set volume levels via clicking on the speaker icon on top task bar and setting preferences for sound levels.

---

### Post by atngplusultra on 2008-12-21
yes, the error message I get with that is:
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

---

### Post by atngplusultra on 2008-12-22
after a re-install, I again tried updating my alsa-base file, and that's done nothing still.

my biggest obstacle, I think, is getting the drivers to compile the right way.

---

### Post by 73ckn797 on 2008-12-23
I will have to pass from here. I have had no sound problems on my Toshiba (see specs below).

---

### Post by Raynman37 on 2008-12-23
Here's two good threads on audio that you could check out:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I used the second when I couldn't get my USB headphones to play any audio.  Hope you find what you need!

---

### Post by mapes12 on 2008-12-23
> **atngplusultra said:**
> This is all happening on Intrepid, running on a Toshiba Satellite a135-s4677

It started when I realized that I had no sound thru headphones. I remembered that under 7.10, I had to download some old alsa drivers to get this to work, so, I constantly tried to do that all night.
However, in the meantime, something somewhere went wrong (I probably should've taken notes as to what steps I took) and now I have no sound at all.

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

```
aplay: device_list:215: no soundcards found...
```

and, no matter which drivers I try to install (be they old or the most recent), I get this error:
```

sudo make
make dep
make[1]: Entering directory `/home/andrew/alsa-driver-1.0.14'
make[2]: Entering directory `/home/andrew/alsa-driver-1.0.14/acore'
copying file alsa-kernel/core/init.c
/home/andrew/alsa-driver-1.0.14/utils/patch-alsa: 24: patch: not found
make[2]: *** [init.c] Error 1
make[2]: Leaving directory `/home/andrew/alsa-driver-1.0.14/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/andrew/alsa-driver-1.0.14'
make: *** [include/sndversions.h] Error 2
```

So, in all likelihood, it's a soundcard issue, but, the only thing I can think to do is reinstall Intrepid.

thanks.

7.10 used Alsa to configure sound but from 8.04 onwards (which clearly includes 8.10) Pulseaudio has taken its place. I can't help further on this but you may want to search for Pulseaudio troubleshooting for the solution to your problem.

---

