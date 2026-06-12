---
title: "Ricoh Card reader doesn't do anything."
date: 2011-07-21
forum: New to Ubuntu
---

### Post by b_rodrigues on 2011-07-21
Hi, I have a Dell Studio XPS 1645 with Ubuntu 11.04.

My camera's sd card is Sony's Memory Stick PRO Duo and it definitely worked when I used Windows 7 but now, with Natty, when I plug in the card, nothing happens. I found some old fixes online for Ricoh card readers but nothing has actually fixed my problem.

bryan@ubuntu:~$ lspci | grep Ricoh
09:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
09:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
09:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
09:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)

bryan@ubuntu:~$ lspci -v
(...other stuff...)
09:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
	Subsystem: Dell Device 02fe
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0b00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [800] Advanced Error Reporting
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
	Subsystem: Dell Device 02fe
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0c00800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting

09:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
	Subsystem: Dell Device 02fe
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0c00c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting

09:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01) (prog-if 10 [OHCI])
	Subsystem: Dell Device 02fe
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at f0c00000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

That's everything I've found on the Ricoh device but I haven't been able to find a fix for it yet.

Is there a driver that I need to download perhaps?

---

### Post by mixmastamyk on 2011-09-06
Makes two of us.  Nothing in dmesg either.  

I did find this post that mentions that only memory stick doesn't work when connected via PCI.  No idea if it is correct:

[https://bbs.archlinux.org/viewtopic.php?pid=402485#p402485](https://bbs.archlinux.org/viewtopic.php?pid=402485#p402485)

---

### Post by DaveWard on 2012-03-01
Sorry to resurrect an old thread but did you come up with anything to fix this, I have exactly the same issue on a Dell 1557 laptop I recently acquired. Doesn't show anything in dmesg when a card is inserted, and the only odd thing in dmesg is "mmc0: no vmmc regulator found".

---

