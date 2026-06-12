---
title: "Realtek 8191S adapter (r8712u / rtl8192su) Ubuntu 14.04 poor performance"
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by Dino_Jakolis on 2015-12-07
Hello everyone, 

as the thread says, I'm experiencing poor performance with this USB adapter. 

I haven't installed any drivers for it, it was recognized perfectly right away. Worked like a charm for one day... (e.g. max download speed was 8.5mbps, upload speed was 8.5mbps also) (now: down 0.95mbps, up 2.5mbps)
I've looked online for solutions and found files on GitHub, but couldn't not get them installed due to compile error. 

So maybe someone has different approach to this problem and is willing to help. 

What I have tried already:
1) Installed git, build-essential, linux-headers-generic >>> compile error (downloaded rtl8192su.git file using terminal)
2) Reinstalled latest linux image (3.19.0.39-generic) >>> compile error (booted to version 37 and used Synaptics to reinstall latest version)
3) Downloaded firmware-realtek_0.36+wheezy.1_all.deb package which includes all the drivers(?) >>> couldn't install due to error 'subprocess paste was killed by signal (broken pipe)'

So yeah, I greatly appreciate any help. I do have another mini PCIE WiFi card here, but that is for another thread.

EDIT: The name of the adapter in title section is from the dropdown menu in Ubuntu that I see on my computer. Adapter name is probably Realtek 8191SU.

---

