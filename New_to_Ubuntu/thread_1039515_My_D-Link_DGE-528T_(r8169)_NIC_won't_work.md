---
title: "My D-Link DGE-528T (r8169) NIC won't work"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by telekarlsen on 2009-01-14
I'm running 8.10 Desktop (2.6.27-9-generic) on a MOBO with Intel onboard controller. This network is working fine (eth0).

Trouble is I want to have more speed. - So I install my D-Link PCI card which should give me the benefit of running a Gb network.

But the expected eth1 never shows up.

Look at what **dmesg** shows:
```
[   25.975631] r8169 0000:02:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.348024] r8169 0000:02:0b.0: unknown MAC (ffffffff)
[   26.348684] eth1: RTL8169 at 0xf08aae00, ff:ff:ff:ff:ff:ff, XID 7cf0f8ff IRQ 18
```

and **lspci -n**:
```
00:00.0 0600: 8086:1a30 (rev 03)
00:01.0 0604: 8086:1a31 (rev 03)
00:1e.0 0604: 8086:244e (rev 12)
00:1f.0 0601: 8086:2440 (rev 12)
00:1f.1 0101: 8086:244b (rev 12)
00:1f.2 0c03: 8086:2442 (rev 12)
00:1f.3 0c05: 8086:2443 (rev 12)
00:1f.4 0c03: 8086:2444 (rev 12)
00:1f.5 0401: 8086:2445 (rev 12)
01:00.0 0300: 10de:0110 (rev b2)
02:08.0 0200: 8086:2449 (rev 03)
02:0a.0 0c03: 1033:0035 (rev 41)
02:0a.1 0c03: 1033:0035 (rev 41)
02:0a.2 0c03: 1033:00e0 (rev 02)
**02:0b.0 0200: 1186:4200 (rev 10)**
```

I have googled the problem a lot now and have found something. [[COLOR="Blue"]This fix[/COLOR]]("http://www.linuxquestions.org/questions/linux-hardware-18/ethernet-card-dge-528t-and-kernel-2.6-350564/") (edit the r8169.ko) actually gives me the card in dmesg; otherwise not.
(though I had to use **1186:4200** instead of **1186:4300** for obvious reasons)

Kernel or driver problem, anyone?

---

### Post by kestrel1 on 2009-01-14
According to this [LIST]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsDlink")
your card should be supported.
There is one thing that is a little confusing though, in your above post you have put this code ```
[   25.975631] r8169 0000:02:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.348024] r8169 0000:02:0b.0: unknown MAC (ffffffff)
[   26.348684] eth1: RTL8169 at 0xf08aae00, ff:ff:ff:ff:ff:ff, XID 7cf0f8ff IRQ 18
```
This seems to indicate that the MAC address is not known. MAC addresses are coded into the NIC, so therefore should be recognised. Is this card new or are you reusing it from another system.
I wonder if the card has a fault. I could be wrong of course.

---

### Post by telekarlsen on 2009-01-16
You were right, Kestrel, the card was faulty...
I replaced with another DGE-528T and - Voila!

The MAC-address is listed in the dmesg and everything is OK now.

---

### Post by kestrel1 on 2009-01-16
A result then :)
Glad to help.

---

