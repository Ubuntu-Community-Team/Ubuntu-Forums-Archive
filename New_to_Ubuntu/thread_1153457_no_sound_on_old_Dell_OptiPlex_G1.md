---
title: "no sound on old Dell OptiPlex G1"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by rockerphil on 2009-05-08
ok, quick rundown. i've got this old Dell OptiPlex G1 running a 350 MHz Intel chip and 256 MB of PC100 SD RAM that i got from a yard sale for $5 running Windows 2k, so i threw Xubuntu 9.04 on it, and it runs fine, but i've got no sound, and i've tried googling till my fingers bleed, and searching high and low on the forums, and this seems to be a pretty commen problem with this particular sound card, but i can't seem to find a solution that works, so i'm hoping that i can get some help on this one. here's what lspci gives me:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (rev 3a)
```

i'm guessing that the sound card is the "Digital Equipment Corporation DECchip 21152 (rev 03)" any suggestions is greatly appreciated, and much thanks in advance,

Phil

---

### Post by halitech on 2009-05-08
I had one of these old systems a while ago and if I remember right, it actually uses an ISA based onboard sound card. You might be better off picking up a cheap PCI sound card and installing that instead.

---

### Post by durand on 2009-05-08
You might want to try an OS better optimised for old computers like deli linux.

---

