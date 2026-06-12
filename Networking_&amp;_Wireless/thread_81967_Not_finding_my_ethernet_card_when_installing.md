---
title: "Not finding my ethernet card when installing"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by bete on 2005-10-25
When i try to install ubuntu on my second computer, it wont recognise the ethernet card..

I baught a brand new card for this pc because it diddnt have one from before.

The ethernet card i baught was a "soho 10/100 PCI lan card".

I would guess ubuntu would find easily when installing.. But it couldnt find it, instead it "thought" it found something it called a firewire ethernet card.. I was a bit confused :P, because my computer does not have a firewire card at all..

Anyhows.. I carried on with the installation hoping i can install the ethernet card later with the diskette i got when i baught it.

Could anyone tell me how i install the driver for this card?

---

### Post by JPZ on 2005-10-25
The lspci command displays the PCI devices on your system. Post the output of 

sudo lspci -vv

so we can see what Ubuntu thinks is there.

-Jeff

---

### Post by krishnanv on 2006-01-31
I am facing a similar problm with my PC. I have an ADSL net connection. But Ubuntu 5.10 could not detect my ethernet card on installation (it detected a firewire ethernet card which I don't have) and now I am not able to connect to net.
Following is the output od lspci command:
0000:00:00.0 Host bridge: Intel Corp. 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82850 850 (Tehama) Chipset AGP Bridge (rev 02)

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 04)

0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 04)

0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 04)

0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 04)

0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 04)

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

0000:02:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

0000:02:0c.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)


Thanks in advance.


[QUOTE=JPZ]The lspci command displays the PCI devices on your system. Post the output of 

sudo lspci -vv

so we can see what Ubuntu thinks is there.

-Jeff[/QUOTE]

---

