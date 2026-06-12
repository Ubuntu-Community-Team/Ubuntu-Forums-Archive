---
title: "Bypassing GRUB bootloader in dual boot system"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by exwindowsuser2 on 2010-09-19
Hi, I've recently installed Ubuntu 10.04 onto my Lenovo laptop, alongside Windows 7 Ultimate. Unfortunately I need to revert to a system backup of the Windows 7 system, stored on a DVD.

When I installed Windows 7 and Ubuntu I merely placed a bootable DVD in the laptop drive, selected 'boot from IDE DVDRAM' in the bios settings and restarted. Now GRUB loads whenever the machine is restarted and starts up either operating system from the hard disc, ignoring whatever is in the DVD drive, or the bios settings. I cannot now reinstall either Windows 7 or Ubuntu from DVD, both of which I need to do.

Can anyone please suggest a workaround that doesn't involve replacing the laptop's SATA drive?

Thanks in advance!

---

### Post by sikander3786 on 2010-09-19
Doesn't seem to be a problem related to GRUB. Are you sure the DVD is in proper working condition, moreover, are you sure that the DVD is bootable?

What happens if you disable booting from HDD in the Bios? Start with just a single bootable device i.e, your DVD-ROM and see if it boots this time.

---

### Post by wilee-nilee on 2010-09-19
Use the post bios f-key prompt for choice of boot. It is f12 on my computer could be any other of those keys in that row including esc. You just have to be pumping the key as soon as you hit the power button.

If you don't preformat the W7 partition or write over it you may end up with a borked Linux. I have on two occasions had Ubuntu go unallocated with letting W7 format the partition in the install.

I would wonder about the dvd as well but it sounds like a install dvd.

---

