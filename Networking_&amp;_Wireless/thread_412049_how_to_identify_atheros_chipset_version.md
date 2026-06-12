---
title: "how to identify atheros chipset version"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by benanzo on 2007-04-17
Hi!

I have a first-gen macbook (core duo) which has an Atheros wireless adapter.  Everything works great.  I was wondering how I can identify the specific chipset version in the adapter.  And aside from that, does anyone know if the madwifi-ng driver that ships with Feisty supports the creation of Virtual Access Points and packet injection for this card?  I apt-getted the madwifi-tools and have been playing around with wlanconfig but am have trouble putting the card into Monitor mode or ad hoc mode.

Any help would be great.

lspci -v

```
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Apple Computer Inc. Unknown device 0086
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
```

---

### Post by dmizer on 2007-04-17
in terminal type:
```
lspci
```
it will give the chipset version.

---

### Post by benanzo on 2007-04-18
I did lspci -v but it gives:
```
Unknown device 001c
```

is there another way to find the chipset version?

---

### Post by Linuturk on 2007-04-22
how did you get your wireless working. I appear to have the same chipset as you. The wireless worked on the live CD, but doesn't after installation.

---

### Post by benanzo on 2007-05-03
sorry for the  delayed post, I haven't checked this thread in awhile.

I actually didn't have to do anything to with the wireless.  Feisty ships with the madwifi drivers that include support for this chipset out of the box.

What kind of problems are you having?

---

### Post by Linuturk on 2007-05-03
I'm not sure what happened. The first install I tried worked on the Live CD, but didn't work after the install. I eventually reinstalled, and it worked! I just don't know.

---

### Post by tturrisi on 2007-05-03
Atheros devices can be put into monitopr mode very easily, but packet injection won't work w/ madwifi drivers unless you patch them using the patch from aircrack-ng site.  Multiple virtual devices are also supported well.

---

