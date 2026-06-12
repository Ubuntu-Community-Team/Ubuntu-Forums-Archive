---
title: "Bluetooth USB dongle - not functioning correctly in Ubuntu 22.04"
date: 2024-01-17
forum: Networking &amp; Wireless
---

### Post by hal9000cta on 2024-01-17
I recently built a new PC and installed Ubuntu 22.04 (dual-booted with Windows 11). My motherboard does not have in-built bluetooth. I purchased a bluetooth USB dongle. It generally works very well. However, whenever I reboot my machine, I always have to disable and re-enable bluetooth through the desktop GUI (settings) in order for it to work properly. Once I do this, it works great. If I don't do this, it isn't the case that it doesn't work exactly, but it appears extremely sluggish in its scan for nearby devices. Barely any are picked up, and there is barely any output to see in bluetoothctl. Something just isn't right. As soon as I disable/re-enable, as described, a flood of devices are discovered and there is a healthy stream of output in bluetoothctl. If left idle for a while, the scan sometimes needs to be resuscitated again using the same enable/disable trick.

The packages I installed before using the dongle were:

bluez
bluez-tools
pulseaudio 
pulseaudio-module-bluetooth 
pavucontrol 

I was hoping to be able to mimic the behaviour completely in the terminal (bluetoothctl), but I can only get it to work probably through disabling/re-enabling in settings. Which begs the question, what this is doing exactly. My hunch is that it involves an rfkill block/unblock, but I can't be sure and I didn't find the journalctl output too helpful here.

Just after some pointers or similar experience really. It's not a massive deal, but I'd like to get to the bottom of it.

The tests I've done so far are:
1) Connecting my phone to my PC and playing music from my phone through my headphones which are wired to the PC.
2) Connecting my PC to a bluetooth speaker and playing music through them from the PC.
3) Connecting to a raspberry-pi which controls an LED sports-scoreboard.

This all works fine.

---

### Post by hal9000cta on 2024-01-17
The issue could be related to the power management of the USB port. The disable/re-enable 'trick' in settings is probably a red-herring. The 'trick' to getting it to work can also be effected by simply unplugging and re-inserting the dongle. 

The behaviour I'm seeing on start-up, of tardy performance, could be explained by an insufficiency of power to the USB port (the dongle has been placed in a low-power state). When you disable/re-enable in settings, I suspect the underlying hardware is being power-cycled (switched off and on). When it is left idle for a while I suspect the device is being placed back into a low power state.

USB autosuspend (which manages this process of power switching between low-power states and normal power states) can be suspended as follows:

```
sudo nano /etc/default/grub
```

Find the line starting with GRUB_CMDLINE_LINUX_DEFAULT and add usbcore.autosuspend=-1 to the options. Save the file and run:

```
sudo update-grub
```

And then reboot.

Interestingly, simply doing bluetoothctl power on/off does not cut it.

This is obviously not a fix, but it could explain what is going on.

---

### Post by deadflowr on 2024-01-17
What's the dongle?

---

### Post by hal9000cta on 2024-01-17
It's this guy:

[https://www.amazon.co.uk/Bluetooth-ZEXMTE-Keyboard-Transmitter-Receiver/dp/B09MZ8715D/ref=mp_s_a_1_49?crid=91P71SH7GYIF&keywords=bluetooth+dongle&qid=1705530997&sprefix=long+range+bluetooth+dongle%2Caps%2C105&sr=8-49](https://www.amazon.co.uk/Bluetooth-ZEXMTE-Keyboard-Transmitter-Receiver/dp/B09MZ8715D/ref=mp_s_a_1_49?crid=91P71SH7GYIF&keywords=bluetooth+dongle&qid=1705530997&sprefix=long+range+bluetooth+dongle%2Caps%2C105&sr=8-49)

---

### Post by hal9000cta on 2024-01-17
Also this one: 

[https://www.amazon.co.uk/TP-Link-Bluetooth-Adapter-Multiple-Receiver/dp/B09S15RLH5/ref=mp_s_a_1_2?crid=2Y9IAN5DYPJL0&keywords=tp+link+bluetooth+adapter&qid=1705531180&sprefix=tp+link+%2Caps%2C96&sr=8-2](https://www.amazon.co.uk/TP-Link-Bluetooth-Adapter-Multiple-Receiver/dp/B09S15RLH5/ref=mp_s_a_1_2?crid=2Y9IAN5DYPJL0&keywords=tp+link+bluetooth+adapter&qid=1705531180&sprefix=tp+link+%2Caps%2C96&sr=8-2)

But they use the same driver (rtl8761bu_fw.bin) so not too surprising.

---

