---
title: "USB keyboard won't install"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-10-21
I checked the BIOS and usb is enabled, a few of my keys aren't working so I'm going to use a USB Keyboard until it's fixed, any ideas on how to fix it? As far as I'm aware it doesn't need drivers

---

### Post by coolbrook on 2009-10-21
You're right.  You should be able to hotplug a USB keyboard and tap away.  Who is the manufacturer of the keyboard and what is its model number?

What do you see with this terminal command?
```

lsusb
```

---

### Post by Rave Gloves on 2009-10-21
us 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:c302 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


technika 
 Model: WKEO3

---

### Post by staticextasy on 2009-10-21
If you're using 9.10,

I had an issue where my USB wouldn't work until i restarted but it was just a random occurance i think. Have you tried restarting at all with it plugged in?

---

### Post by coolbrook on 2009-10-21
Is that a wireless keyboard (wkey03) ?  Are you running it off of a port on a USB hub or a USB port connected directly to the motherboard?  If you're running it off of a hub, then consider trying the motherboard's USB port.

---

### Post by Rave Gloves on 2009-10-22
I didn't know there was a Mother board USB it is not wireless and I don't think I have a USB hub. and I have tried restarting with it plugged in.

---

