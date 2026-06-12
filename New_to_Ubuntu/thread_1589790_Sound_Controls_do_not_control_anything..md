---
title: "Sound Controls do not control anything."
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-10-06
Okay, you you remember that little megaphone in your (default) indicator applet panel? And you remember how you can set key commands to operate it to control the volume? I love that feature more than life itself.

So it stopped working. I can still do volume up, volume down, mute, and the indicator applet shows my changes accordingly, but it does NOT affect the volume in ANY WAY. I can have it on mute, with the little headphone displaying dashes next to it, and still have every single sound causing event be INCREDIBLY LOUD on my computer.

The only things I can think may have caused this were installing pavucontrols (which has since been uninstalled, but the indicator still doesn't work), and upgrading alsa (the controls continued to work fine for quite some time after this, so I doubt this is correct either).

Any ideas?

---

### Post by Locke_99GS on 2010-10-06
PulseAudio setting are likely messed up. Reinstall pavucontrol and correct the Pulse settings. Afterwhich, you can remove pavucontrol again.

---

### Post by Zeppelin! on 2010-10-07
So I reinstalled it and took a look. The only thing I could find odd was that my input volume was somehow down to 22%. Everything else looks to be in order, as far as I can tell.

After further examination, the problem seems to be that somehow (since I try to avoid messing with my audio settings, this is probably my fault in some way of completely not knowing how this would have happened) the indicator applet's settings got set to trying to put sound through my sound card instead of the speakers. Of course, this still doesn't explain why I can't get any sound out of my headphone jack (note: I have never been able to get sound out of my headphone jack with Ubuntu. The temporary Windows install could put sound through them).

---

### Post by Locke_99GS on 2010-10-07
I don't know if audio is supposed to switch automagickally to the front jacks when you plug in headphones. It's never functioned that way in my Linux machines, I have to switch it myself when I want to use the front jacks. It could be a shortcoming of Linux, though.

Also, check the settings in *alsamixer*.

---

