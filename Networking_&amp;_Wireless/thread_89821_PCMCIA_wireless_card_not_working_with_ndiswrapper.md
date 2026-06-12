---
title: "PCMCIA wireless card not working with ndiswrapper"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by bjk525 on 2005-11-13
I just bought a used IBM thinkpad T21 with a WavePlus WP1200 PCMCIA card in it. The card works perfectly under windows xp but I can not get it to work under  linux. I think the card is being recognized because when I use cardctl ident the card shows up. When I try to use the drivers with ndiswrapper it tells me that it is an invalid driver.  Here is the output: ```
billy@Thinkpad:~$ cardctl ident
Socket 0:
  product info: 
"WavePlus Technology","WLAN PC Card WP1200", "Version 01.00",""
  
manfid: 0x0000, 0x0000

  function: 6 (network)

Socket 1:
  
no product info available

billy@Thinkpad:~$ ndiswrapper -l

Installed ndis drivers:

netwpnds        invalid driver!

billy@Thinkpad:~$ lspci

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)

0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)

0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)

0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)

0000:00:03.1 Serial controller: Lucent Microelectronics LT WinModem (rev 01)

0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)

0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
billy@Thinkpad:~$

```

According to all of the posts I have read about the invalid driver warning, this problem is normally caused by an incorrect path to the driver file but i have checked this multiple times. I have a feeling that the driver is not being associated with the card but I have tried using ndiswrapper -d to fix that but that didn't help either. I am out of ideas for getting this card to work.

Does anyone have any ideas to help me get this card working?

---

