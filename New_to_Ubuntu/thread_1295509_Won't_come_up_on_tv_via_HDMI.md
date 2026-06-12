---
title: "Won't come up on tv via HDMI"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by nobbydog on 2009-10-19
Hi
Just completely gone over to jaunty(deleted vista), everything great internet,email compiz,special effects, multi media.
But when i plug in to my hd tv via a HDMI CABLE IT WILL NOT COME UP ON TELLY.
Any ideas please
Regards 
Nobby

---

### Post by OffAxis on 2009-10-19
what video card do you have?
What's the connection type on the card to the cable?

How about the cable to the tv?

Have you installed the 'Hardware Driver' for the video card?

---

### Post by nobbydog on 2009-10-19
GeForce 8400M GS
hdmi
hdmi
Ithink so because video play back in movie player works ok 
nobby

---

### Post by OffAxis on 2009-10-19
Make sure you're using the Restricted Driver for that card, it's under
System-->Administration-->Hardware Drivers.

This'll also give you access to the nvidia configuration tool, so you can make some adjustments with that if need be.

The easiest thing to try (if you're not already doing this) is to boot with the hd tv hooked up and let it auto detect.

---

### Post by m_duck on 2009-10-19
My HTPC has to be switched off before being connected to the TV. If it starts booting/is booted before it's connected, it does not recognise the TV attached via HDMI and therefore displays no picture.

---

### Post by Hospadar on 2009-10-19
If you have an nvidia card with nvidia drivers, I suggest you use their configuration tool to set up multiple/cloned/different monitors

Alt-F2 "nvidia-settings"

---

