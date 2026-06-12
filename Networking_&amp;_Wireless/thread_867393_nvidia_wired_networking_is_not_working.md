---
title: "nvidia wired networking is not working"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by ProbablyX on 2008-07-22
Hello!

I just got a new motherboard and reinstalled hardy, the problem is that my networkcard (built into it) isnt working,

Knetworkmanager shows this:

Device: Unknown (0x0760)
Vendor: nVidia Corporation
Interface: eth0
Bandwidth: 100Mbit/s
Active: yes
Carrier detect: supported

Ifup eth0 shows:
"Ignoring unknown interface eth0=eth0."

lshw -class NETWORK:
desc: Ethernet interface
product: nVidia
vendor: nVidia
physical id: a
bus info: pci@0000:00:0a.0
local name: eth0
verseion: a2
serial: *code*
width: 32bit
clock: 66Mhz
capabilities: bus_master cap_list ethernet physical
configruation: broadcast=yes driver=forceddeth driverver=0.61 latncy=0 maxalt=20 mignt=1 module=forcedeth multicast=yes

Sorry if Ive shortened down some terms above, typing from laptop. I enabled ACPI2 earlier, can that be causing this?

Thanks

---

### Post by ProbablyX on 2008-07-22
BTW the chipset is nForce 730a, if it matters. Thanks!

UPDATE:
lspci says:
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 07600 (rev a2)

---

### Post by ProbablyX on 2008-07-23
Hello!

I just got a new motherboard and reinstalled hardy, the problem is that my networkcard (built into it) isnt working,

Knetworkmanager shows this:

Device: Unknown (0x0760)
Vendor: nVidia Corporation
Interface: eth0
Bandwidth: 100Mbit/s
Active: yes
Carrier detect: supported

Ifup eth0 shows:
"Ignoring unknown interface eth0=eth0."

lshw -class NETWORK:
desc: Ethernet interface
product: nVidia
vendor: nVidia
physical id: a
bus info: pci@0000:00:0a.0
local name: eth0
verseion: a2
serial: *code*
width: 32bit
clock: 66Mhz
capabilities: bus_master cap_list ethernet physical
configruation: broadcast=yes driver=forceddeth driverver=0.61 latncy=0 maxalt=20 mignt=1 module=forcedeth multicast=yes

Sorry if Ive shortened down some terms above, typing from laptop. 
lspci says:
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 07600 (rev a2)

The chipset is nForce 730a, of what I can understand its based on "MCP78"

Thanks

---

### Post by overdrank on 2008-07-23
Threads merged.
Just a thought but have you checked bios to insure that the nic is enabled?

---

### Post by ProbablyX on 2008-07-23
> **overdrank said:**
> Threads merged.
Just a thought but have you checked bios to insure that the nic is enabled?

Yes I have, it is actually detected by Linux - just not working.

I read that my chipset isn't 100% supported yet. And as I've been having trouble with my PC for over two weeks now I got fed up and bought a Deltaco Gigabit PCI card (Realtek chip). It works like a charm :)
Thanks anyway.

---

