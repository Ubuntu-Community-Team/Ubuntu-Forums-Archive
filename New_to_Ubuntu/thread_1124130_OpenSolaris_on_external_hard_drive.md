---
title: "OpenSolaris on external hard drive"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Agent.Logic_ on 2009-04-13
Hi guys,

I have Ubuntu and Windows XP installed on my desktop PC, and everything is going great. I thought I'd try out OpenSolaris, but I don't have any space left on my hard disk, so I'm thinking of installing OpenSolaris on my USB external hard drive. I'm just wondering if I'd be able to directly boot into the external hard drive, with OpenSolaris installed in it (by setting the BIOS to check for USB boot before HDD boot), or would I need to change some GRUB settings on my current install for it to work?

---

### Post by bumanie on 2009-04-13
As long as you have boot from usb available in bios and set it to boot as the first device, you should, in theory, be able to boot the external drive directly.I have ubuntu on an external and boot no problems when bios is set to boot from usb-hdd. I set grub to (hd0,0) on the external drive and did not change any of my desktop OS settings.

---

### Post by Agent.Logic_ on 2009-04-13
Ah, just like I thought. Thanks for the confirmation mate, cheers!

P.S. your signature = win! :D

---

### Post by Agent.Logic_ on 2009-04-16
Well, I installed OpenSolaris and everything went well. That is, until I had to reboot. When I plug in the external hard drive before my PC boots, the OpenSolaris version of GRUB shows up (with the typical blue background and the OpenSolaris logo). When I select the first entry, OpenSolaris, the loading screen shows up with a marqueeing bar. Before the bar can reach half way, my PC reboots automatically. This sequence keeps happening until I unplug my external hard drive, so that the GRUB on my regular hard drive can show up so I could boot into Ubuntu or Windows.

I managed to learn it has something to do with GRUB needing to know how to boot a ZFS filesystem. But the instructions I found on the internet went way over my head. What do I need to do in order to get OpenSolaris running? I tried using the OpenSolaris LiveCD, and even then I cannot mount my external hard drive (where OpenSolaris is installed) to modify any entries.

---

