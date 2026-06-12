---
title: "Can't enable Nvidia drivers in 2.6.27-11"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-15
I did a large update earlier and now when I boot into the new kernel 2.6.27-11 I get errors saying that I don't have the nvidia driver.
Well I checked Synaptic and it IS installed. I tried uninstalling and re-installing but nothing seems to work. No matter what I do I can't get Ubuntu to use the driver.

When I start nvidia-settings it says I should run nvidia-xconfig as root, so I do. But then when I restart and try to run nvidia-settings it just complains about the same thing!

I tried downloading the drivers from nvidia's website and when I run the installer, first it says it found the precompiled libraries, then when it tries to download it says it CAN'T find them after all, then it says it can't figure out what kernel I have because I don't have the source.

What? It seriously wants to recompile the kernel JUST to install these drivers?

There MUST be an easier way.

---

### Post by Volt9000 on 2009-03-16
Ok I somehow got it working, unfortunately I have no idea how. :( All I did was boot using the previous kernel and reinstall the drivers there (since I uninstalled the drivers from the new kernel and that messed up the old one.) Now all of a sudden it's working in both. :???:

---

