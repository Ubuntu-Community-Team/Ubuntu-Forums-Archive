---
title: "internal speakers no, external speakers yes?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by tc1955 on 2009-05-03
No sound. Not on booting up or anything else. Everything otherwise seems to work. Tried all kinds of posted fixes but no luck.

Older hp laptop. Solo boot on Jaunty. Had sound on Intrepid but suddenly disappeared before upgraded and can't get back.

None of volume control settings are muted.

Surprised to discover get sound with external speakers plugged in.

Is there any possible way to fix?

---

### Post by kostkon on 2009-05-03
What kind of external speakers do you have? Do you mean USB speakers?

---

### Post by tc1955 on 2009-05-03
Yes.

---

### Post by webwiller on 2009-05-03
Try this:

> gksudo gedit /etc/modprobe.d/alsa-base

add this line in the end:

> options snd-hda-intel model=laptop enable=1 index=0

Save, exit and reboot.

Let us know... ;)

---

### Post by kostkon on 2009-05-03
Actually, *tc1955* you will need to install the *PulseAudio Device Chooser* from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the Output Devices tab you should see your USB speakers listed. Just right-click on them and enable the *Default* option to set them as the default output device.

For this to work you'll need to set your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*.

Hope that helps.

---

### Post by tc1955 on 2009-05-03
Thanks for the suggestions.  Unfortunately, neither worked.  Strangely, for the Pulse Audio volume detector, the mute button is on and won't change.  Stuck again.

---

### Post by kostkon on 2009-05-03
> **tc1955 said:**
> Thanks for the suggestions.  Unfortunately, neither worked.  Strangely, for the Pulse Audio volume detector, the mute button is on and won't change.  Stuck again.
Try following this sound solutions thread [here]("http://ubuntuforums.org/showthread.php?t=1130384"), it may help you solve the mute problem that you have.

---

