---
title: "Wlan doesn't install"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by dekket on 2005-07-27
I just finished installing Ubuntu on my laptop, and the wlan adapter did not install. The wired ethernet installed fine, but not the wlan, which makes it kinda useless in my work...

I'm using an HP/Compaq nx6110. If anyone has a solution I'd be most grateful.
The wlan card has the following output by lspci:
[B]0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 12fa
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at d0000000 (32-bit, non-prefetchable) [size=8K][/B]

---

### Post by majikstreet on 2005-07-27
[QUOTE=dekket]I just finished installing Ubuntu on my laptop, and the wlan adapter did not install. The wired ethernet installed fine, but not the wlan, which makes it kinda useless in my work...

I'm using an HP/Compaq nx6110. If anyone has a solution I'd be most grateful.
The wlan card has the following output by lspci:
[B]0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 12fa
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at d0000000 (32-bit, non-prefetchable) [size=8K][/B][/QUOTE]
 Check this howto: [http://ubuntuforums.org/showthread.php?t=25683&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=25683&highlight=BCM4306)

---

