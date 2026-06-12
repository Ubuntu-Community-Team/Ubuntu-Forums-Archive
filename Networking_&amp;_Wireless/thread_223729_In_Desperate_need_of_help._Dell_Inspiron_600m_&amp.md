---
title: "In Desperate need of help. Dell Inspiron 600m &amp; Dapper: No Wireless"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by diamond on 2006-07-26
Please help me.

I used to have Breezy installed on my Inspiron 600m, and I was able to get ndiswrapper to work just fine with the wireless card. Now I've upgraded to Dapper, and it just won't work.

I've gone through all of the steps: install ndiswrapper and ndisgtk from Synaptic, get Windows drivers, install Windows drivers with "Windows Wireless  Drivers" utility (I used the driver bcmwl5.inf). But the wireless connection refuses to enable. If I try to enable it with a static IP (my preferred configuration), I get the message "Could not enable the interface eth1", and my syslog has the following lines:

```

Jul 26 18:42:56 localhost firmware_helper[7578]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
Jul 26 18:42:56 localhost kernel: [17180425.300000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jul 26 18:43:12 localhost firmware_helper[7598]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
Jul 26 18:43:12 localhost kernel: [17180441.364000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jul 26 18:43:12 localhost firmware_helper[7601]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
Jul 26 18:43:12 localhost kernel: [17180441.376000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

If I try to enable eth1 with DHCP, it just gives me the "enabling eth1" message forever, until I finally give up and close it.

I'm totally stuck here. Please, please, for God's sake, somebody help me out.

---

### Post by loupy on 2006-07-26
if you want to use ndiswrapper you need to remove the broadcom module.

sudo gedit /etc/modprobe.d/blacklist

add:  "blacklist bcm43xx" (no quotes) and save the file

from the command line type in:

sudo modprobe -r bcm43xx

then

sudo modprobe ndiswrapper

that should do it.

---

### Post by diamond on 2006-07-27
> **loupy said:**
> if you want to use ndiswrapper you need to remove the broadcom module.

sudo gedit /etc/modprobe.d/blacklist

add:  "blacklist bcm43xx" (no quotes) and save the file

from the command line type in:

sudo modprobe -r bcm43xx

then

sudo modprobe ndiswrapper

that should do it.

I tried that before, and all that happened was that the eth1 interface completely disappeared off of my network devices. Is there something else I need to do?

---

### Post by diamond on 2006-07-27
> **loupy said:**
> if you want to use ndiswrapper you need to remove the broadcom module.

sudo gedit /etc/modprobe.d/blacklist

add:  "blacklist bcm43xx" (no quotes) and save the file

from the command line type in:

sudo modprobe -r bcm43xx

then

sudo modprobe ndiswrapper

that should do it.

OK, it finally worked; this did it. I don't know what I did wrong last time, but it's up now. Thank you very much.

One thing I've noticed, though: the wifi-radar utility doesn't seem to be working. I have a correct profile set for my home wireless network, but it's not showing any signal within wifi-radar (even though I am connected with a very strong signal). Any reason why this might be happening? Is wifi-radar broken, or does it not play well with the other network configuration tools?

---

### Post by MarkSheely on 2006-07-27
I have heard that wireless radar doesn't play well with some Broadcom cards.  I would really recommend that you use network manager.  It's worth the time spent getting it to work.  Another possibility would be to use wireless assitant - it is very similar to wireless radar.

Good luck,
Mark

---

