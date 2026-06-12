---
title: "How to use installation cds in ubuntu?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by carrotsoup on 2010-08-10
I was having problems with my vox external harddrive, so I put in the cd with the drivers on it, in the hopes that installing it would fix the problem of the drive not being recognized.
When I put the cd in, I had some issues...

- If click on the vox icon that appears on the desktop, all I get is the cd contents. 

-If I go to the file browser and click "media/install" on the side panel, the disc tray pops out.

-If I right click on the cd icon on the desktop and click "open with autorun prompt", it will say "Error running autorun software. Cannot find the autorun program"

Any suggestions? I can't find any vox drivers in synaptic, so I thought this was worth a shot.

---

### Post by MasterGamerJK on 2010-08-10
the Cd drivers are most likely for windows  only (lame, i know) try the manufactures website for Linux drivers, or maby a forums somewhere in which explains how to configure it w/o drivers, as most Linux devices operate

---

### Post by carrotsoup on 2010-08-10
Aw shoot, that sucks. I checked out their site first, but the domain is down. I'll keep looking around on the forums though, thank you.

---

### Post by -kg- on 2010-08-10
That's very odd.  An external hard drive should be recognized upon being plugged in.  How are you hooking it up to your system...USB or eSATA?

Have you tried opening terminal and issuing the command:

```
sudo fdisk -l
```

(that's a lower case "L")?

Any hard- or flash drive I've ever plugged in was recognized immediately.  You shouldn't need a driver for that.

---

### Post by carrotsoup on 2010-08-10
It's connected with a USB cable. 

I thought it was a little weird too, but it doesn't seem to be a problem with the actual cable; I've been testing it on other computers without a problem. 

I plugged that command in, but all that came up was the internal hard drive. Really odd that this thing isn't even getting picked up...

---

### Post by LowSky on 2010-08-10
Does the device show up with this terminal command?

```
lsusb
```

if yes we might have some luck

---

### Post by carrotsoup on 2010-08-10
I don't think it did. All I got was 

```

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by -kg- on 2010-08-10
You're right.  Here's the output from my terminal, external drive highlighted in red:

> Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 001 Device 005: ID 045e:000b Microsoft Corp. Natural Keyboard Elite
[COLOR="Red"]Bus 001 Device 003: ID 1058:1102 Western Digital Technologies, Inc.[/COLOR] 
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


An experiment:  Try installing GParted from the repos (if you haven't already) and launch it (from "System/Administration").  See if GParted can see it.  That, or use GParted from the Live CD.

There is something wrong here, and I'm starting to think it's hardware.  You might want to check the USB cable to start with.  Do you have another computer that you can try it on?  Do you have Windows in dual-boot that you can try it with?  Was it working then stopped working, or have you never been able to get it to work?

---

### Post by carrotsoup on 2010-08-10
Gparted didn't pick the external up, but I just tested it out on another laptop running windows and there weren't any problems. 

It was working just yesterday on this computer [running Ubuntu], but now it won't anymore.. I thought it might have been a hardware issue too, but I tried a few different usb cables with the same results.

---

### Post by carrotsoup on 2010-08-10
Another thing I tried:
I thought the problem might have actually been in my laptop's usb hubs, so I plugged my ipod in to check if my computer would pick that up.

It did. So the problem isn't a hardware issue with the external's usb cable [as it's working on another laptop as I speak] and it isn't with the usb hub [as I have an ipod plugged in that appeared right away].

---

