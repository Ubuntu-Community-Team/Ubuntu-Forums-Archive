---
title: "Intel Wifilink 5300"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by uPWarrior on 2008-08-14
I recently bought a new LG S510 laptop and I'm in trouble configuring the wireless card.

The system detects it as:

08:00.0 Network controller: Intel Corporation Unknown device 4235
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

I've tried ndiswrapper, but couldn't make any of the Windows drivers to work. (first time I used it, so it can actually be my fault)

Any idea on how to make it work properly?


Sorry if this was already answered, couldn't find an answer searching here or google.

---

### Post by uPWarrior on 2008-08-15
Bump!

---

### Post by sreyan on 2008-08-27
I think intel added the drivers for that card into wireless-2.6.git. You might want to look and the compat-wireless project and see if that helps you get native drivers.

---

### Post by pytheas22 on 2008-09-03
I don't know if you solved this yet, but the solution in [this thread]("http://ubuntuforums.org/showthread.php?t=906865") seems to work for people so far (see post #4 in particular).  Please give it a shot and let us know if it helps you too.

---

