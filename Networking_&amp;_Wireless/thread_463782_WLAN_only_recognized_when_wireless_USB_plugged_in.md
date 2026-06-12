---
title: "WLAN only recognized when wireless USB plugged in"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by skoalman88 on 2007-06-04
Anyone know why this would happen?

---

### Post by Adapted.Cat on 2007-06-04
Not quite sure what you're getting at here...

When the wireless USB has not yet been plugged in, is there any reason (e.g. a PCI wireless card on the same machine) for your computer to have a WLAN link?

When you plug in a wireless USB device, the USB host sends a connect signal to the OS, which queries the device, and auto-loads any relevant kernel modules it knows about, and then may automatically enable the link, depending on your configuration.

When you take the wireless USB out, the USB host sends a disconnect signal to the OS, which may then take down the link (depending on the driver, perhaps). Sometimes you have to rmmod the module to get it to disappear.

If you unplug a memory card reader, not only the mounted filesystems but also all the /dev/sd? storage devices go away.

If this did not happen, then you could plug in your USB WLAN device to all the USB jacks in turn, and end up with half a dozen different WLAN devices registered with the kernel, and you wouldn't know which one to use.

Does that answer the question, or were you asking a different question?

---

### Post by Trackieman on 2007-06-04
Hi, I'm a little intrigued and puzzled by your question.
It would seem that if you are connecting to a Wireless LAN (WLAN) with a USB device that the action of the
Wireless LAN not showing until you plug the adapter in perfectly logical.
Is it that you want to configure a wireless connection so that it's all nice and ready before you plug in your USB
wireless device? If this is what you want to do then I think it could be doable by editing network config files first. 
But you'd basically have to fake Linux into thinking it's seen your USB device before and this is its config.
That's a lota work. Have I missed your point entirely?

---

