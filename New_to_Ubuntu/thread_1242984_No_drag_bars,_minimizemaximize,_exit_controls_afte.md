---
title: "No drag bars, minimize/maximize, exit controls after NVIDIA driver update."
date: 2009-08-17
forum: New to Ubuntu
---

### Post by richg813 on 2009-08-17
Please help...

I've just used the Synaptic Package Manager and to install the nvidia driver for my Geforce 7800 GT and I have no normal window controls like:

No drag bars, minimize/maximize, exit controls after NVIDIA driver (nvidia-glx-96) update!

The display looks awesome, but geesh, I don't know what happened to them.

Please, any help???

Rich Guagliardo

---

### Post by northern lights on 2009-08-17
The 96.XX.XX does support your GPU, but you don't need a legacy driver. Even the newest nvidia linux driver offered at [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html") supports your card.

Anyhow, the correct driver should have been offered to you out of the box. Uninstall manually installed graphics driver(s) and check under 'System Administration > Hardware Drivers' in the gnome menu.

---

### Post by richg813 on 2009-08-17
Thank-you so much, Northern Lights!

Is there instructions anywhere to "manually" uninstall a graphics driver?

---

### Post by northern lights on 2009-08-17
```
sudo aptitude purge nvidia-glx-96
```Further post the output of ```
aptitude search nvidia
```

---

### Post by richg813 on 2009-08-17
It worked!!! YOU ROCK!!!

---

