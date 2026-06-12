---
title: "Jensen wireless (realtek 8180L)"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by jon armand on 2008-08-08
Hello, fellow citizens of the free world!

I have a Jensen pcmcia wireless adapter, which has a realtek chip inside (RTL8180L).
 It works fine under 6.06 and 6.10 and Vector, but not under 7.04 and up.
lspci returns the following:
jon@jon-laptop:~$ sudo lspci
Password:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)




How do I make this pcmcia wifi card work under 7.04?

P.S.
Under 7.04 I have a D-link usb device that works, but I have only one USB connection, and would like to use this for an external hdd.

P.P.S.
Under 7.10 and 8.04 none of the above work, and I have no wire connection on the pc.

Any suggestion is appreciated!






b.t.w. my pc is an old dell laptop (latitude cpx 500 with 384 MB ram)

---

