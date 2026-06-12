---
title: "USB Antenna compatibility with Ubuntu 16.04"
date: 2017-08-14
forum: Networking &amp; Wireless
---

### Post by AbleTassie on 2017-08-14
I have a Lenovo Y510 and am using Lubuntu 16.04.2 LTS. I am on vacation and I am having trouble pulling in a WiFi signal (2 bars, sporadic) from a  neighbor's home (who has given us the password). And I am thinking of adding a USB antenna to my laptop. Do I need to take special precautions (e.g., particular antennas or software drivers) to be sure an antenna works with the OS (lubuntu 16.04.2) I have?    Thanks,  A.

---

### Post by TheFu on 2017-08-14
Honestly, if I where you and on vacation, I'd take this as an opportunity to disconnect.  "Nothing I could do about it" is what I'd tell the boss, when I got home.

There isn't anything called a "usb antenna."
I think you are looking for an "external USB wifi network adapter."

Not all "USB wifi NICs" are compatible with Linux, so you'll want to do some research.

Also, if the internal NIC is having issues, it is likely that an external one will also have the issue, but with some models, you can build a better, directional, antenna using a pringle's chip can and some aluminum foil. [http://www.makeuseof.com/tag/how-to-make-a-wifi-antenna-out-of-a-pringles-can-nb/](http://www.makeuseof.com/tag/how-to-make-a-wifi-antenna-out-of-a-pringles-can-nb/) is a how-to. There are many, many, others.

If you do go this direction, you'll need to disabled the on-board USB wifi adapter in the BIOS.

Just be on vacation and be happy, about a year ago I visited some fairly remote places and wasn't connected very much for about 2 weeks.  It was good.   For example, I visited here: [http://explore.org/live-cams/player/river-watch-brown-bear-salmon-cams](http://explore.org/live-cams/player/river-watch-brown-bear-salmon-cams)

---

### Post by praseodym on 2017-08-14
You may need to update the BIOS/UEFI because of the device whitelist then

---

### Post by AbleTassie on 2017-08-19
Thanks for the advice Fu & praseodym. Fu, I get it about not being connected all the time. I will mark this thread as SOLVED.  A.

---

### Post by TheFu on 2017-08-19
Lenovo is known for locking down certain addon devices in the BIOS to be only those they approved.  I've never heard of this from USB connected devices, but it could happen.

I assume you've searched for fixes for the specific wifi card inside your machine.  Often there are just driver options that help a bunch.  Use **sudo lshw -C network** to see which wifi adapter is used in your specific machine.  Then you can search for solutions. The wifi card that is advertised isn't always the one shipped.

---

