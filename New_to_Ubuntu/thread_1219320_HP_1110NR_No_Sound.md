---
title: "HP 1110NR No Sound"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by k8fox1 on 2009-07-21
I purchased an HP 1110NR netbook and installed Ubuntu 9.04. Everything is cool except the sound.....there is none. Being rather inexperienced I am struggling to fix this. Where do I begin? Thanks in advance for any help as well as patience.

-Mike

---

### Post by mikewhatever on 2009-07-21
Try this fix -> [https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44).
Here is some more info on this. [http://www.psychocats.net/ubuntucat/vanilla-ubuntu-on-the-hp-mini-1120nr/](http://www.psychocats.net/ubuntucat/vanilla-ubuntu-on-the-hp-mini-1120nr/)

---

### Post by swoll1980 on 2009-07-21
Start with the easy stuff first. Open the volume control by right clicking the icon in the task bar. Then raise the volume levels. See if that works, then post back.

---

### Post by k8fox1 on 2009-07-23
1) Ok I checked and all volume levels are turned up to max.

2) I checked the device listed under my Volume Control and it reads Null Output (PulseAudio Mixer) is this correct?

3) I performed the installation as suggested by Mikewhatever but was unable to edit the /etc/alsa/alsa-source.conf as the system told me my privileges were not sufficient. Not sure why that was.  

Where do I go from here?

Thanks,

Mike

---

### Post by linux_tech on 2009-07-23
try stopping pulseaudio ```
sudo killall pulseaudio
```

---

### Post by k8fox1 on 2009-07-23
Have done ll the above but still no audio. The following playback devices are listed:

HDA Intel (Alsa Mizer)
IDT 92HD75B2X5 (PulseAudio Mixer)
Playback: HDA Intel- STAC92xx Analog (PulseAudio Mixer)

At this point I am nor even sure which device should be selected?

Thanks.

---

### Post by k8fox1 on 2009-08-30
Folks this issue is still unsolved. Is there anyone else out there that can help me?

Thanks

---

