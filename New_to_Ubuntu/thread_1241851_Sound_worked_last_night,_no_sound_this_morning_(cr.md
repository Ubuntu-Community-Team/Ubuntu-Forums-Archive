---
title: "Sound worked last night, no sound this morning (crackling)"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by mangurt on 2009-08-16
Greetings all,
I don't know what happened....I had sound last night (watched a movie via Hulu).  I got up this morning, and I have no sound...all I get is crackling....No sound via alsa, no sound with pulse audio...any ideas?

---

### Post by nhasian on 2009-08-16
i know you may have already tried this but, does rebooting resolve your problem?

---

### Post by mangurt on 2009-08-16
I've rebooted twice.  One time was via restart, the second time I did a complete power down....and left the system off for 2 hours...

---

### Post by mangurt on 2009-08-16
Ok, my head is really hurtinging now.  I have sound if I use gizmo5, but everything else is crackle....no sound..

---

### Post by rirad on 2009-08-29
I had a similar problem with my system (Ubuntu 9.04_64). Sound also suddenly broke and I could only hear crackling sound. This happened after a restart from some package updates. Initially I thought my sound card broke. When I switched to OSS (System-Preferences-Sound) I got sound working again (except for apps that do not support OSS) so this was more like a work around than a fix. So the problem was with Alsa.

I finally got it fixed by opening the volume Control (right click speaker icon) and set PCM (which was set to 0%) to 100%.

In the end this problem was not caused by a package update but most likely by a faulty system shutdown.

---

### Post by szadek_ on 2009-08-29
Try to remove pulseaudio , it removes ubuntu-desktop package , but nothing that stops the system to work , and try to use only alsa .When sound problmes happen on here , i just remove pulseaudio and it goes fine again.

---

