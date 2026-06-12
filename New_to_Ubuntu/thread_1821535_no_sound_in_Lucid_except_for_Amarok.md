---
title: "no sound in Lucid except for Amarok"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by fairy._.queen on 2011-08-09
Hello world!
I have a problem with the sound in Lucid Lynx (I decided to stick to LTS distros): Amarok plays music all right, but everything else doesn't make a sound (e.g. skype, youtube etc.). I checked both pavucontrol and alsamixer and nothing is muted. KMix has nothing muted, too.
Can you please help me? Thanks in advance!

---

### Post by androssofer on 2011-08-09
> **fairy._.queen said:**
> Hello world!
I have a problem with the sound in Lucid Lynx (I decided to stick to LTS distros): Amarok plays music all right, but everything else doesn't make a sound (e.g. skype, youtube etc.). I checked both pavucontrol and alsamixer and nothing is muted. KMix has nothing muted, too.
Can you please help me? Thanks in advance!

is it through standard speakers or HDMI etc? and have u tried pulse audio? it might help...

---

### Post by trinux_bc on 2011-08-09
Have you installed restricted extras?

```
sudo apt-get install ubuntu-restricted-extras
```

Have you checked out the sound problems thread?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

trinux_bc

---

### Post by fairy._.queen on 2011-08-11
ok, a few more information.
1) Yes, i have tried pulseaudio.
2) everything occurred short after the second last kernel update.
3) some hours after i posted, everything changed spontaneously into the opposite: now everything but amarok works. Amarok doesnt make a sound. I didn't reboot, nor did anything that might change the situation.

EDIT: I tried the guide (thanks, i hadn't see it) and typed
aoss amarok
now it's back to where it started: no youtube, no sounds in facebook apps, nothing but amarok...

Thanks a lot for your replies!

P.s.: I haven't tried the restricted areas yet, because i'm a bit puzzled at the problem getting opposite and I would like to read your posts first.

---

