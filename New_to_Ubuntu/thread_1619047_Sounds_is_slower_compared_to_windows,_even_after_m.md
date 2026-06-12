---
title: "Sounds is slower compared to windows, even after maxed"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by ALF102 on 2010-11-11
Hi there, I'm using a laptop eMachines D525...and I don't really know what my sound card is. But when I use my laptop speakers in ubuntu, the sound is much fainter than when I use it in windows even after I maxed it out.

---

### Post by SlugSlug on 2010-11-11
I have much better sound uninstalling pulse and installing alsa,

---

### Post by NightwishFan on 2010-11-11
Try checking the sound levels by running alsamixer in the terminal. Also if you are running 10.04, try installing alsa backports. (Just set search to "Name" and look for "alsa backports generic" in Synaptic).

---

### Post by ALF102 on 2010-11-11
I'm using 10.10 and currently using alsa, I even got alsa-mixer but it seems the volume is still quite slow even if its maxed out.

---

### Post by NightwishFan on 2010-11-11
Try searching for information about your card. Perhaps someone has found a fix. To find the model run this in a terminal:
```
sudo lshw -C sound
```

I think this is just a limitation in alsa (for now), bad luck chap. :(

---

### Post by ALF102 on 2010-11-11
description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:43 memory:f0700000-f0703fff

---

### Post by NightwishFan on 2010-11-11
Well I did not mean show **me**. I am not an alsa expert, google is. :) However it turns out we have the same exact device. Never tried Windows, though in 10.10 my sound is blasting loud so I dont know what wrong on your end. (Though this card is terrible in general).

Perhaps try updating alsa, though I do not recommend this solution, as I did not test it myself.
[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

---

### Post by SlugSlug on 2010-11-11
make sure PCM is set high in alsamixer

---

### Post by ALF102 on 2010-11-11
uhm, how do I check again if my audio is either alsa or pulse?

---

### Post by NightwishFan on 2010-11-11
If you are using Ubuntu without removing it yourself, you are using Pulse. Though alsa routes through it and is still an integral part.

---

### Post by ALF102 on 2010-11-11
without removing it, you meant something like not-doing-any-changes-to-the defualt-sound-driver?

If thats so, then that means, I'm using Pulse right now

---

### Post by ALF102 on 2010-11-11
Ugh..this is bad, I've tried the scirpt for the alsa update and the result is that I got no sound at all.

---

### Post by ALF102 on 2010-11-11
oh wait, there is sounds..but it seems I can't control the volume from my keyboard shortcut

---

### Post by ALF102 on 2010-11-11
More bad news, sounds output is just the same before I run the script.

---

