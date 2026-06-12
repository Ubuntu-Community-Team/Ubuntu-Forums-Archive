---
title: "No sound"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Strider11o7 on 2009-06-15
I just installed 9.04 today, everything seems to work fine except the lack of sound (ALSA still works though). I get an error from my volume control telling me it needs drivers, how would I go about finding out my problem or fixing it?

Oh, and yes they work on my Windows so it's not a hardware problem.

---

### Post by Elfy on 2009-06-15
To allow us to be able to help you could let us know what sound card you have.

Open a terminal - Applications Accessories menu - run the commands and post ther output you get here.

```
lspci
aplay -l
```

There is a troubleshoot here - [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Strider11o7 on 2009-06-15
Okay, inputing that into terminal gives me "device_list:221: no soundcard found...".

According to the troubleshoot guide, I needed to check to see if I have the proper modules installed. I entered "sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic" to get them, but then I recieved the error:

"Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"
No packages will be installed, upgraded, or removed."

---

### Post by rogueleader12345 on 2009-06-15
Perhaps this link will be of some assistance: [http://www.linuxforums.org/forum/ubuntu-help/147037-solved-ubuntu-9-04-sound-problems.html](http://www.linuxforums.org/forum/ubuntu-help/147037-solved-ubuntu-9-04-sound-problems.html)
Let me know how it turns out. Good luck!

---

### Post by halitech on 2009-06-15
what was the output of ```
lspci
```

---

### Post by Strider11o7 on 2009-06-15
Okay, I've been following the guide more by trying to make sure ALSA is using the correct module. Although I'm not sure how many Jack Plugs my soundcard has, there are only a few options anyways so I could easily try them all if needed.

Coincidently, I have the same codec as the guide author, so I added "options snd-hda-intel model=5stack" to my ALSA congif file and saved it, and it said to force restart it with "sudo alsa force-reload", but upon entering that command, I get:

"lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eric/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eric/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload)."

I'm not sure what to do at this point. Also, for Halitech, here's my results for "lspci":

"00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)"

---

