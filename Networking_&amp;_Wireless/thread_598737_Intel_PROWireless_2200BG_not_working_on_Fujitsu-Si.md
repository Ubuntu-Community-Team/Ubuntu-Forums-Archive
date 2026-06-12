---
title: "Intel PRO/Wireless 2200BG not working on Fujitsu-Siemens AMILO Pro V2020"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by Masapena on 2007-10-31
I have no clue what I should do.

Here's some information that I got by using lspci -v.

01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
 Subsystem: Intel Corporation Unknown device 2702
 Flags: bus master, medium devsel, latency 64, IRQ 18
 Memory at e00fe000 (32-bit, non-prefetchable) [size=4K]
 Capabilities: <access denied>

---

### Post by aysiu on 2007-10-31
That's funny. I get the same output, but my wireless works fine: ```
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2701
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
``` Can you explain more what "not working" means? Are you using Network Manager? Network manual settings? Wifi-Radar? Does it *appear* to connect but not actually connect? Or does it not appear able to connect at all?

Please be as descriptive as possible. I'm not 100% sure I can help, but if you describe a bit more what's going on, someone else may be able to.

---

