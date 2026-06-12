---
title: "Problems with pcmcia network card"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by palmtree3000 on 2008-08-25
I have a Network Everywhere Ethernet 10BaseT ethernet network card. After switching from windows 2000 to xubuntu, I found that the card no longer works. I confirmed that pcmciautils is installed. 
Here is the result of lspci:
> palmtree3000@laptop1:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
palmtree3000@laptop1:~$ 
Here is the result of pccardctl ident:
> Socket 0:
no product info available
Socket 1:
product info: "Network Everywhere","Ethernet 10BaseT PC Card", "2.0", " "
manfid: 0x0149, 0xclab
function: 5 (network) 
Based upon the instructions at [http://kernel.org/pub/linux/utils/ke...ia/pcmcia.html](http://kernel.org/pub/linux/utils/ke...ia/pcmcia.html) , I appended "pci=assign-busses" (no quotes) to the end of the boot line, to no avail. Please help!

---

