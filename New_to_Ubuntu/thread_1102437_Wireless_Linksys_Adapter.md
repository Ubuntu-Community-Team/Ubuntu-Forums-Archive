---
title: "Wireless Linksys Adapter"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Roadbloc on 2009-03-21
I have recently been given a Linsys wireless-g notebook wireless adapter and it ubuntu doesn't appear to recognize it. It there a way it could be made to work???

---

### Post by coolbrook on 2009-03-21
What is the model number of this device?

What is the output of the terminal command:
```

lspci
```

---

### Post by halitech on 2009-03-21
is it USB or PCMCIA?

if it is USB, post the output of
```
lsusb
```

---

### Post by Roadbloc on 2009-03-23
its PCMCIA. is that a problem?

---

### Post by halitech on 2009-03-23
in that case, post the output of
```
lspci
```and that will tell us the chipset

---

### Post by Roadbloc on 2009-03-24
ok. this is the output i get from lspci.

```
daniel@captain-slow:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:09.0 Ethernet controller: Conexant HCF 56k Modem (rev 08)
00:09.1 Communication controller: Conexant HCF 56k Modem (rev 05)
00:0a.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```

Hope you can help me. :)

---

### Post by halitech on 2009-03-25
this is your card: 

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


Looks like this should help

[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

---

### Post by Roadbloc on 2009-03-26
Thanks. I'll try that tonight. :)

---

### Post by oldrocker99 on 2009-10-22
I just trid it and it works, using ndiswrapper and the XP driver for the card, Thanks for the tip!

:guitar:

---

