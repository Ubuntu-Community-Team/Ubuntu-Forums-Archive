---
title: "Sound syncrhonization"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by patman0623 on 2009-02-02
I have been having some sound problems on Ubuntu. I would be interested if anyone would know of any remedies:

1) When I have one process open playing sound, it will make sound for other processes not possible. I can't have Pidgen playing a sound when Firefox opens, or I won't have sound for Firefox.
2) The sound often becomes permanently busted until I restart. Right now, my system has no sound: period. I don't know why. On my Suse system, I tried running alsactl, which worked, but I don't want to goof up the settings. Help!

---

### Post by jbrown96 on 2009-02-02
I just posted for another user that is having sound problems. Frequently, pulseaudio seems to be the problem. Try changing your sound devices to ALSA and see if that works better. System--->Preferences--->Sound, and then change everything to ALSA.

---

### Post by patman0623 on 2009-02-02
> **jbrown96 said:**
> I just posted for another user that is having sound problems. Frequently, pulseaudio seems to be the problem. Try changing your sound devices to ALSA and see if that works better. System--->Preferences--->Sound, and then change everything to ALSA.
You're right. It worked. This forums always seems to have the answers I need. Thanks.

---

