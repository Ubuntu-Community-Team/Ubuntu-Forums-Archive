---
title: "Dlink DWL-G510 6.10 Issues"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by Gerg on 2006-12-06
Okay so I recently got a Dlink DWL-G510 Rev-B wifi card from Newegg . Originally I had 6.06 (Dapper Drake) installed and everything worked fine but I decided I wanted to try 6.10 (Edgy Eft). So I updated my installation to 6.10 and now I can no longer enable my network card even though it shows up in system=>admin=>networking. How do I fix this? Thanks

---

### Post by ReaderRat on 2006-12-06
check & see if this can help...scroll down to your model#....
**[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)**

---

### Post by Gerg on 2006-12-06
I doesn't really help me much. I does say though that my card should be supported and that the v2.11 drivers work. I have those drivers on CD now how do I install them?

---

### Post by FrodoB on 2006-12-06
What is the output of:

lspci -v

We need to see which one it is.

---

### Post by Gerg on 2006-12-06
Here it is

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-feffffff
        Prefetchable memory behind bridge: f9000000-f9ffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at ffa0 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dce0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:0e.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at ff000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: Dell Optiplex GX1 Onboard Display Adapter
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 9
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=256]
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <access denied>
```

---

