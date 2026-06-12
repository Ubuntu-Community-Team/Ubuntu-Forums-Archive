---
title: "error loading tiacx100c00 for device 'unknown'"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by timkoop on 2007-04-22
Hi everyone. When Feisty loads, it displays this error:

* Loading hardware drivers...
firmware helper[3599]: main: error loading '/lib/firmware/acx/default/tiacx100c00" for device '/class/firmware/0000:03:00.0' with driver '(unknown)'

I'm not exactly sure what this means, but I think it says that it can't get my network card to work. I have a D-Link AirPlus DWL-650+, which is actually a Texus Instruments acx100.

If someone would like to help me with this, I'm actually trying to use the ndiswrapper instead of the open source acx100 driver.

Using the Package Manager, I downloaded and installed the ndiswrapper gui and used that to install the Windows driver which I downloaded from D-Link's website.

But it still doesn't work. Obviously I'm doing something wrong. I still get that error on start up, so Ubuntu is still probably looking for the open source acx100 driver. I have tried adding "blacklist acx100" to my /etc/modprobe.d/blacklist file, but that doesn't do anything either.

Does anyone have the answer for me? I think there's something I'm not doing, but I don't know what it is. Thanks a lot!

Details:

Error message at startup:
* Loading hardware drivers...
firmware helper[3599]: main: error loading '/lib/firmware/acx/default/tiacx100c00" for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
[ OK ]

# lspci -v -nn

03:00.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]
Subsystem: D-Link System Inc DWL-650+ PC Card cardbus 22Mbs Wireless Adapter [AirPlus] [1186:3b00]
Flags: bus master, medium devsel, latency 64, IRQ 16
I/O ports at 3400 [size=32]
Memory at 48010000 (32-bit, non-prefetchable) [size=4K]
Memory at 48000000 (32-bit, non-prefetchable) [size=64K]
Capabilities: [40] Power Management version 2



# ndiswrapper -l
airplus : driver installed
device (104C:8400) present (alternate driver: acx)

---

### Post by timkoop on 2007-04-22
Any ideas at all?

---

### Post by tturrisi on 2007-04-23
You don't need ndiswrapper for that card.  Use the opensource drivers.

---

### Post by thornomad on 2007-04-24
I haven't seen a fix for this, but apparently something broke in Feisty ... you can view:

[http://ubuntuforums.org/showthread.php?p=2512758#poststop](http://ubuntuforums.org/showthread.php?p=2512758#poststop)

---

