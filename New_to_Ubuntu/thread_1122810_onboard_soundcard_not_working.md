---
title: "onboard soundcard not working"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by rockerphil on 2009-04-11
ok, here's the deal. i found this old Dell OptiPlex G1 at a yard sale for $5 and was setting it up for my girlfriend, but i can't seem to get any sound going through the integrated sound card and i've been googling and searching for the past 2 days so hopefully someone can give me some assistance. here's some terminal output that might help.

```
lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (
rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (re
v 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01
)
00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24
)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (rev 3a)
```

```
 lsusb
Bus 001 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
```

```
 aplay -l
aplay: device_list:204: no soundcards found...
```

this seems to be a common problem with this particular model of computer, but i just can't seem to get it worked out. much thanks in advance,

Phil

---

### Post by supersonicdarky on 2009-04-11
[http://www.linuxforums.org/forum/mandriva-linux-help/56670-getting-sound-working.html](http://www.linuxforums.org/forum/mandriva-linux-help/56670-getting-sound-working.html) ?

---

### Post by cariboo on 2009-04-11
Have you checked the BIOS to see if the sound card is enabled?

Jim

---

### Post by rockerphil on 2009-04-11
thanks for the speedy responses guys, and yes, the sound card is enabled in the BIOS, and i'm currently reading through the link provided above. any more suggestions is greatly appreciated. 

Phil

---

