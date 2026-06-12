---
title: "Wireless card not detected"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by joeblow1102 on 2007-05-29
I just purchased a D-Link WDA-1320 desktop adapter and installed it in my computer.  The funny thing is that the power LED is blinking, however, Ubuntu can't locate the device.

Below are the results from my lspci:
> 
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:08.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

EDIT: I put this as resolved, but it is resolved in Edgy so far, and hopefully Feisty soon.

---

### Post by tturrisi on 2007-05-29
That card has an atheros chipset.  It needs the madwifi drivers.  Install the linux-restricted-modules for your kernel via Synaptic.

---

### Post by joeblow1102 on 2007-05-29
I think you're referring to the attachments, and they seem to be installed.  I'll try reinstalling all of the above, and see what happens.  But even if the driver wasn't installed, the card should still show up under lspci, shouldn't it?

---

### Post by joeblow1102 on 2007-05-30
I followed the instructions here: [http://eureka.emmgee.com/2006/12/ubuntu-610-setting-up-wireless-network.html]("http://eureka.emmgee.com/2006/12/ubuntu-610-setting-up-wireless-network.html")

in Edgy and it works now.  I'm using internet on the computer with the installed card.  Tomorrow, I may or may not try the same steps in Feisty and see if I'm so lucky.

---

### Post by misfitpierce on 2007-05-30
If none of the madwifi works you could always try NDISWRAPPER utils through install and console and install the windowsdriver.inf file into it and see if it runs.

---

