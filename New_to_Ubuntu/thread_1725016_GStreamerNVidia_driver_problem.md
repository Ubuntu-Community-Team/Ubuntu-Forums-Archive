---
title: "GStreamer/NVidia driver problem"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by maximo1010 on 2011-04-09
Hello, I have a problem with GStreamer. Pure-black bold text and Flash applets (or whatever they're called >_<) appear very glitchy. This is not screenshotable, I've tried to screenshot it but it appears completely normal on the screenshot. Well, the pure-black text is white inside it and Flash graphics are also glitchy. I'm assuming this is a driver problem, not a GStreamer problem, though. This sseems to not be there first, but soon it appears. It's annoying me to hell. Looks like it appears when I use Flash.

Thanks in advance!
PS: I own an Acer Aspire 8930G with an NVIDIA 9700M GT, if that means something.
Edit: SOLVED! Disabled hardware acceleration in Flash and goodbye white blackness! :KS

---

### Post by taseedorf on 2011-04-09
Try turning off all effects such as compiz and such.

ALSO, try compiling the NVidia drivers from Nvidia....

---

### Post by maximo1010 on 2011-04-17
> **taseedorf said:**
> Try turning off all effects such as compiz and such.

ALSO, try compiling the NVidia drivers from Nvidia....

Turning off Compiz didn't help, however, they're basically essential for me, and believe it or not, the main reason I actually use Linux. And how do I compile? I don't want to risk screwing up my video. ./configure make sudo make install didn't help.

---

### Post by carnytom on 2011-04-25
I was having same issue.. seems like I fixed it. I open nvdia x control panel, sent the display size from auto to the size I want and set the hrz to 60 instead of auto.. hit apply and the glitchy text and images seem to be corrected.

---

