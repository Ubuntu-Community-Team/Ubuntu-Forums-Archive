---
title: "No sound in any program, but am getting test sounds"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by KillerSponge on 2009-04-22
I have a problem that is, probably, very easy to solve... I just installed a new soundcard (Audiotrak Prodigy HD2), and it is giving sound: in system->preferences->sound it is giving me test signals from Alsa, Pulseaudio and the autodetect, and I get the little sound when the login screen appears. 

However, none of the applications (or the system itself for that matter) seem to be playing sound. I don't get any error messages or anything, but I just don't hear anything. De volume in the alsa-mixer is set correctly, I think. I also tried setting my new soundcard as the default one by giving it index=0 in the alsa configuration. Doesn't seem to work.

Anyone to help me out? :)

Edit:
I just noticed that all the sound is _still_ coming from my old (onboard) soundcard... Looks like the defaulting is not working as it should?

Another edit:
I 'sort of' fixed it by disabling my onboard sound card through the blacklisting of the driver. Not really neat, but hey, it works...

---

### Post by willz06jw on 2009-04-22
You should report the bug on the bug list so they'll fix it for ya.

---

