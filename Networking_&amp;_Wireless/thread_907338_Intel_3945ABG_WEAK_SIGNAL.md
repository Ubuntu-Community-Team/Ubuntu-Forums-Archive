---
title: "Intel 3945ABG WEAK SIGNAL"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by qwertyking on 2008-09-01
Hey guys.

I'm being plagued by this problem ever since I installed 8.04 on my laptop. I've got the intel 3945ABG wireless adapter and using the default iwl3945 driver that comes bundled with 8.04

The problem is that the signal strength on any given network is terrible- almost never is it above 80%, even if i am sitting smack in front of the access point. 

Here is the result for lspci -v | less
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 221
        Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

Any idea how to fix this?

---

### Post by mykrob on 2008-09-01
heck, i get plenty of signal, it just drops the connection after about five minutes, even sitting dead in front of the router. Mine is the intel 3954abg rev 2:


```

myk@gateway-m6881:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:95:05:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

---

### Post by qwertyking on 2008-09-01
bump

---

### Post by talent03 on 2008-10-13
/double posted for some odd reason.

---

### Post by talent03 on 2008-10-13
I have exactly the same problem, except that I have the Intel 4965. My problem is that with iwlist or the network manager the signal shows very weak, but once connected, it shows somewhat strong for a bit. I never have this problem when booting into windows. I did not have this problem before, it just started happening one day. It was previously working better than windows. I hope someone can shed some light on this.

One more thing. The network manager shows the bars correctly but when I click on the applet, it shows the signal strength substantially less than the bars. :/

---

### Post by talent03 on 2008-10-15
My problem has been fixed with a new update today through linux-backports-...

---

