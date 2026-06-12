---
title: "No wireless?"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by doctorgreg on 2008-04-24
I installed hardy on my fiance's laptop through the wubi installer just so she could try it out.  Everything works fine except the internet(wireless).  I cannot enable the device with the wireless button just above the keyboard.  So I rebooted back into vista to make sure it was enabled there and then rebooted back into ubuntu.  But it just does not want to enable.  Any suggestions?

---

### Post by Monicker on 2008-04-24
Please run lspci -v from a terminal while you are in ubuntu, and paste the results here.  Details about the wireless card in the laptop are need.

---

### Post by doctorgreg on 2008-04-25
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Subsystem: Hewlett-Packard COmpany Unknown devive 1363
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at 50000000 (32-bit, non-prefetchable) [size=16k]
Capabilities: <access denied>

---

### Post by doctorgreg on 2008-04-25
all good now.  just opened terminal and did sudo apt-get install b43-fwcutter then reboot.

---

### Post by gba3 on 2010-01-10
The same problem. Fresh Ubuntu 64bit install on hp dv2000 (AMD Turion 64 x2 mobile TL-50; NVIDIA GeForce 6150 chipset)

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Hewlett-Packard Company Device 1363
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

I did the same "sudo apt-get install b43-fwcutter then reboot" and it worked for me too.

---

