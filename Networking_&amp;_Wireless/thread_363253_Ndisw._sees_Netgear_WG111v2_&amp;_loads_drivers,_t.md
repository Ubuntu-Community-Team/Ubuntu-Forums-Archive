---
title: "Ndisw. sees Netgear WG111v2 &amp; loads drivers, then nothing..."
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by daemonfly on 2007-02-16
Searched tons of posts for setting up the Netgear WG111v2 (Actual version 2) USB wireless adapter. Took info from all the latest ones & tried setting this up.

lsusb shows:
```
Bus 002 Device 006: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

```

Manually installed the latest Ndiswrapper from SourceForge.
```
sudo ndiswrapper -v
utils version: 1.9
driver version:        1.37
vermagic:       2.6.17-11-386 mod_unload 486 REGPARM gcc-4.1
```

Ndis. is fully installed, & loaded as a module ,etc.. I've tried the CD drivers, the 1.3 drivers listed in another guide, and the latest beta drivers, both Win98 and WinXP ones for every version.
```
sudo ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: r8187)
```

Now, every guide assumes at this point that everything is fine if I get that result, then continues and expects iwconfig to list wlan0 and we continue on our merry way in the guides...

My iwconfig doesn't see wlan0
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

This is where I'm stuck. I can't get anything to see it aside from ndis. loading the driver properly.

---

### Post by Floppyjoe on 2007-02-16
Have you looked at Phossals walkthrough?
[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)
It says that the native drivers still seem to get involved even after blacklisting them so he deleted the modules that were causing the conflict.

---

### Post by daemonfly on 2007-02-16
Yeah, tried that as well.


What worked though is  that I had it conencted to the USB ports on my Logitech G15 as it's higher than my PC & would get better reception. I guess the keyboard ports couldn't power it well enough as it worked fine when I plugged it into the PC itself (aside from poor signal..)

---

