---
title: "X-Fi Fatal1ty Pro Sound Card Stopped Working"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Commander_Bob on 2010-02-23
I have a X-Fi Fatal1ty Pro and it was working fine. I am running Ubuntu 9.04 and to install the driver I followed [this great guide]("http://ubuntuforums.org/showthread.php?t=870001").

The problem now is that while I was in Windows playing COD Windows crashed (what a surprise). When I rebooted my sound card no longer worked, in ether OS. Windows fails to recognize my sound card at all but in Ubuntu lspci give
```
01:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
	Subsystem: Creative Labs Device 0020
	Flags: bus master, fast devsel, latency 0, IRQ 15
	Memory at f7ff0000 (64-bit, non-prefetchable) [size=64K]
	Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f7000000 (64-bit, non-prefetchable) [size=8M]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [100] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
	Capabilities: [300] Advanced Error Reporting <?>
	Kernel modules: ctxfi

```

Normally the subsystem in 0043, not 0020, but Creative assured me that that can be changed by a change in the drivers. After them telling me to basically re-install the driver three times I though I would ask on here. Do you think this is a hardware or software problem? What could cause such a random change?

I've tried different PCIe slots and I get the same result.

My setup is as follows
Intel i7 920
P6T mother board
6GB DDR3
GTX285
X-Fi Fatal1ty Pro
750W PS

Any help would be great.

Thanks,
Justin

---

