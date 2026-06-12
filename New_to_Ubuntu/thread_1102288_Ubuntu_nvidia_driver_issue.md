---
title: "Ubuntu nvidia driver issue"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by lxnvk on 2009-03-21
Hello, I'm a bit new to this forum and I'm also kinda new to ubuntu. I have a problem with my nvidia graphic drivers and I tried solving it with other threads posted on this forum, but none work. My computer configuration is:
CPU: Intel Core 2 Quad Q6600
Mobo: Asus P5N-T Deluxe
Ram: Mushkin 800 MHz, 4GB
Gfx: Two nVidia 9600 GT in SLI.

WHen I install Ubuntu, everything works, except 3D stuff, like desktop effects, Second Life, google earth etc. THen I tried installing nVIdia drivers that were recomended to me by the Ubuntu notifier, the nVidia 180 driver. But when I restart my computer, it stop booting with: "Detecting battery configuration" THen nothing more happens. I tried modifying the drivers, and got it to work without the x server for some time, but then no 3d effects work again. ANy ideas?

THanks in advance
Alex

---

### Post by lxnvk on 2009-03-22
Well I installed the 180.37 drivers that Ubuntu hardware drivers option offered and made it work by adding the:
Busid: "PCI:4:0:0" line and REMOVING the Option "sli" "auto" line. Now everything works fine, but something is telling me SLI doesn't work. Or am I worng? If it doesn't, how could I fix this?


Alex

---

### Post by labedra on 2009-04-06
sudo nvidia-xconfig --sli=on

---

