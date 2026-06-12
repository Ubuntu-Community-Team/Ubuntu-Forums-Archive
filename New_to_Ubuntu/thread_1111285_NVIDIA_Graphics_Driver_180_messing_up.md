---
title: "NVIDIA Graphics Driver 180 messing up"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by joey-elijah on 2009-03-30
Hearing about how bug-stompingly awesome the new stable driver from NVIDIA is, i installed it from Synaptic (and everything else related to the 180 driver).

Rebooted, no graphic card was enabled so hardware drives > checked the 180 (which now said recommened) and rebooted and was presented with a slow boot up and low graphics mode... so i reboot again this time choosing 'recovery mode'. recover x server (or whatever the exact wording is) and reusme normal boot. It boots into my desktop, again, with no graphics enabled... so i enable the recommended driver (180) and am prompted to reboot.. and...

can you tell where this is going? How do i get out of this cycle?! Surely if the driver is no stable AND recommended it should work okay? How do i get the 180 driver working without being driven insane?

---

### Post by TheLions on 2009-03-30
try installing drivers from here:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

first kernel-source then libvdpau then glx

---

### Post by joey-elijah on 2009-03-30
> **TheLions said:**
> try installing drivers from here:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

first kernel-source then libvdpau then glx

okay! Done that - it now happily boots into a normal looking desktop.. only it seems i'm really dumb at using linux because compositing/desktop effects won't enable. 

I should stick to Windows i think. I can't even install a simple graphics driver without screwing my desktop up... Even the driver says 

> If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some gamesyet mine won't enable so i've obviously screwed something up along the way. :confused:

(I don't just use my graphics card for Compiz, but for HD movie playback etc) 

Any ideas what i've done wrong? 

The 180 driver is enabled in 'hardware drivers' and 'currently in use'.

---

