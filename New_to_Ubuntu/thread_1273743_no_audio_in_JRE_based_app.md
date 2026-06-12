---
title: "no audio in JRE based app"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by clementmunns on 2009-09-23
Pretty much a novice here, but have been through all the forums looking for an answer to this issue:

Want to use my logictech headset with a Java based program called Elluminate (uses the JRE 6).
 
I can get sound with either the OSS or ALSA sound drivers when testing the headset.

I learned how to kill the pulseaudio processes that were stopping the ASLA drivers.

But no how can I get sound or mic usage with this application, which is annoying as it makes me have 
to boot up in XP just to use an app which is supposedly OS agnostic. BTW: the app launches, and works fine, just no sound.

Was thinking it might be a security/permissions thing as the app is launched via a URL download, then does autorun.




Any help would be greatly appreciated~

---

### Post by paultag on 2009-09-23
Howabout pulse?

Perhaps you can ( if you are using pulse ) use the pulse device app to redirect the stream

---

### Post by paultag on 2009-09-23
The app name is `padevchooser`

Perhaps fiddle with that?

If it works with OSS / ALSA, it will work with pulse

---

### Post by clementmunns on 2009-09-23
> **paultag said:**
> The app name is `padevchooser`

Perhaps fiddle with that?

If it works with OSS / ALSA, it will work with pulse

will that give me control of what the JRE 6 app can do?

---

### Post by paultag on 2009-09-23
Yes. JRE will act as a client to the Pulse Daemon. It won't matter if it's Java, C, C++ or Brainfsck :)

---

### Post by clementmunns on 2009-09-24
Still no luck. The mic worked but the sound never did. Was wondering if it could have something to do with the Intel HD driver (RealTek); in some of my
XP programs I have to disable the onboard sound to use the USB mic/headset.

I've tried to disable the Intel sound in the BIOS, but it still shows as an
option in the sound prefs.

Is there any way to unistall this driver in Ubuntu without hosing the whole
works?

---

### Post by clementmunns on 2009-09-25
bump

---

