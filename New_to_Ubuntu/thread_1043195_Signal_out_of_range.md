---
title: "Signal out of range"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by nick3295 on 2009-01-18
I'm trying to install Ubuntu to a Compaq Deskpro Pentium 3, but after the intstallation, my monitor says "Signal out of range", and gives the settings "H=58.8kHz V=73.5Hz". The graphics card in this computer is a Matrox MGA-G200A-D2. I know everything works, because it previously had XP installed on it.

---

### Post by cmnorton on 2009-01-18
This happened to me, when I tried adding a Thinkpad T61p into a KVM environment that has an Acer AL1914 (not too sure about the model #, but it is a 19" Acer flat screen).

I had to do a couple of things, so the Thinkpad could work in the KVM and play standalone. 

1) I had to change to the Vesa driver, even though the Thinkpad has Nvidia.

2) I had to create other resolutions, and choose the highest that would work standalone and in the KVM.

To do this, I stopped using restricted drivers. Did this from System --> Administration.

I rebooted, but went into recovery mode.

Entered dpkg-reconfigure xserver-xorg

Took all default answers, except driver --chose vesa -- and I also created several resolutions, even if I did not think I could use them.

You might not have to change drivers, but your settings in Ubuntu are out of range for the monitor. You can try to fix this without booting into recovery mode. I found I had little time to do this, because the monitor would shut itself off to avoid being damaged.

---

### Post by ZipoTe on 2009-01-22
I have the same trouble as you... and many users here. What the hell is going on? Long time since I used "Ubuntu" for the last time, and now I try this new release (8.10) and I have to edit the xorg.conf manualy like 5 years ago... is this a joke???

Fresh install here, using the nvidia controller ubuntu recommends. I supose I'll be playing around with de X server...



Sorry if it sounds very rude but I'm SO disappointed seeing so many people with the same trouble on a modern Linux distribution.


Thanks.

---

