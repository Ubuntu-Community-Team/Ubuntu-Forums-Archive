---
title: "Problem after installing NVIDIA drivers"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by mike2365 on 2010-02-16
Dual boot XP/Ubuntu system. ASROCK 330 ION. I'm new to Ubuntu, installed three days ago and was working fine. I installed NVIDIA drivers as recommended by the system and restarted the system as instructed-disaster. boot fails with a fails to synch error (plus lots of other messages that are meaningless to me. starting in protected mode leaves me in a command prompt. Help

---

### Post by Greenwidth on 2010-02-16
If you are using karmic (9.10), from the command prompt type:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
and reboot.

The above renames the settings for the x server so that it is not loaded at boot but configures 'on the fly' - which should bring you back to where you were before, ie no Nvidia driver.

I would recommend using a later driver than the recommended one as it supports many new features, VDPAU &c. The easiest way is to add nvidia's ppa, this also means you will not have to reinstall the driver when you get a kernel upgrade.

Open synaptic package manager from:
System > Admin > Synaptic

Settings > Repositories > Other Software tab > Add button
paste: ppa:nvidia-vdpau/ppa

Reload

Quick search for nvidia-190 (or 195 - these are beta but work fine)
mark install kernel source

Reboot. Enjoy!

You might also be interested in XBMC - a media centre which uses VDPAU to off load to the GPU.

---

