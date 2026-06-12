---
title: "dmesg: WEP supported, 104-bit key - ME: Not 128-bit???"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by daller on 2005-10-31
I have a problem with my wireless!

When I close the lid, or leave the computer idle for a while, it loses the wireless connection!

Today I found this in dmesg:

[4294703.100000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4294703.106000] orinoco_pci 0.14alpha2 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[4294703.111000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294703.111000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294703.111000] orinoco_pci: Detected device 0000:00:09.0, mem:0xd0401000-0xd0401fff, irq 10
[4294704.056000] eth1: Hardware identity 8013:0000:0001:0000
[4294704.056000] eth1: Station identity  001f:0009:0001:0004
[4294704.056000] eth1: Firmware determined as Intersil 1.4.9
[4294704.056000] eth1: Ad-hoc demo mode supported
[4294704.056000] eth1: IEEE standard IBSS ad-hoc mode supported
[4294704.056000] eth1: WEP supported, 104-bit key
[4294704.056000] eth1: MAC address 00:02:8A:99:50:F4
[4294704.057000] eth1: Station name "Prism  I"
[4294704.057000] eth1: ready

Does the above mean that I can get problems on an 128-bit WEP connection?

---

### Post by mgor on 2005-10-31
> WEP key (secret key) are available in two types, 64-bits and 128-bits. Many times you will see them referenced as 40-bits and 104-bits instead. The reson for this misnomer is that the WEP key ( 40/104 bits ) is concatenated with the initialisation vector ( 24 bits ) resulting in a 64/128 bit total key size.
from [http://www.zyxel.com/support/supportnote/ZyAIR_B1000/app/wep.htm](http://www.zyxel.com/support/supportnote/ZyAIR_B1000/app/wep.htm)

---

### Post by daller on 2005-10-31
Ok, thanks!

Any idea about how to solve my problem?

---

### Post by mgor on 2005-10-31
does it work if you restart the network after you've opened the lid again?
```
sudo /etc/init.d/network restart
```

if so you could check what acpi event opening the lid triggers and if i'm not misstaken you can chose to specify a script to run if that event gets triggered. haven't used acpi events myself, but check [http://www.google.se/linux?q=acpi+events](http://www.google.se/linux?q=acpi+events)

---

