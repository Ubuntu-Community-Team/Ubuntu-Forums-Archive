---
title: "Wireless won't work, am I using the wrong driver? How to tell?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by carrotsoup on 2010-08-10
My wireless no longer works after installing Ubuntu. I searched around on the forums, but I'm not sure if it's the problem I'm having. I put this in the command prompt ```
lspci -v
```

In order to figure out what my wireless card is. It came up with this. I'm only guessing this is what I'm looking for, I'm not sure what it means but it seemed the most relevant. 

```
 
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1355
    Flags: bus master, fast devsel, latency 64, IRQ 21
    Memory at c0200000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb 
```

How do I know if I'm using the wrong driver, and how can I get one that will get my wireless working again?

---

### Post by carrotsoup on 2010-08-10
I also tried this solution with no luck :


[LIST]
[*]Check in *System > Administration > Hardware Drivers*  for a binary driver.  For instance, many Broadcom cards will work with  the Broadcom STA driver.  Unfortunately, the driver is proprietary (the  source code is not freely available), and so cannot be installed  automatically as part of Ubuntu.  If you are willing to accept this  limitation, activate the driver. 

[/LIST]

Basically, I can only connect to the internet if I'm actually plugged in. When I unplug it, the wireless doesn't pick up any of the networks that my other laptop running on windows picks up.

---

### Post by anewguy on 2010-08-10
Before looking for a restricted driver in System/Administration/Hardware Drivers, you should try the following:

- hard-wire your connection as you say you are able to

- open a terminal window and type:

sudo apt-get update <press enter>

Wait for that to finish.

Now look in System/Administration/Hardware Drivers and see if a driver shows - if so enable it.

Disconnect the hard-wire connection (physically).

Right-click on the network manager icon and check to see if "Enable Wireless" is checked - if not, check it to enable.

Wait a couple of minutes, then left-click on the network manager icon and see if any networks show.

Let us know how that goes.  There are alternative ways as well, but this is normally the easiest.

Dave

---

### Post by carrotsoup on 2010-08-10
Perfect solution, thank you so much!

---

### Post by anewguy on 2010-08-10
Just glad it's working!

Enjoy ubuntu!

Dave ;)

---

