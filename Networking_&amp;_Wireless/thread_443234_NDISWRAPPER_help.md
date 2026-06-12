---
title: "NDISWRAPPER help"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by soopisgoodfood on 2007-05-14
"To identify the driver that you need from List, first identify the card you have with lspci and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card by running lspci -n and locating the entry corresponding to the first column of lspci output. The PCI ID is third column or fourth in some distributions and of the form 104c:8400. "

i did lspci and i got a big list and saw nothing to do with wireless or pci except PCI Bridge (is that it?) and i remember when i got internet to finally work on this computer when it was running windows i had to enable "Ethernet Controller" in device manager (but i cant remember if this was before i had wireless..) and now i see 2 Ethernet Controllers listed on lspci. could one of those be this "PCI ID" or is there supposed to be something that says "PCI ID"???:confused: ](*,)

---

### Post by Kobalt on 2007-05-14
Yes one of these two must be your wifi card. You can post the output of lspci here is you want, and we can point out the wireless card...

---

### Post by soopisgoodfood on 2007-05-14
> **Kobalt said:**
> Yes one of these two must be your wifi card. You can post the output of lspci here is you want, and we can point out the wireless card...

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
01:01.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
01:02.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)



i think the last one is the right one but i'm not sure...

EDIT: 
"Installed ndis drivers:
e100exp invalid driver!"
i installed the bottom Intel 82562EZ and that's what it says for ndiswrapper -l 

so now i will try the atheros..

---

### Post by Gina on 2007-05-14
There appear to be just two network adapters and the last entry is a wired one so the wireless must be

01:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

---

### Post by stchman on 2007-05-14
> **soopisgoodfood said:**
> "To identify the driver that you need from List, first identify the card you have with lspci and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card by running lspci -n and locating the entry corresponding to the first column of lspci output. The PCI ID is third column or fourth in some distributions and of the form 104c:8400. "

i did lspci and i got a big list and saw nothing to do with wireless or pci except PCI Bridge (is that it?) and i remember when i got internet to finally work on this computer when it was running windows i had to enable "Ethernet Controller" in device manager (but i cant remember if this was before i had wireless..) and now i see 2 Ethernet Controllers listed on lspci. could one of those be this "PCI ID" or is there supposed to be something that says "PCI ID"???:confused: ](*,)

Use the procedure laid out on my website to get madwifi working for Atheros.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked on my laptop.

---

### Post by soopisgoodfood on 2007-05-14
> **stchman said:**
> Use the procedure laid out on my website to get madwifi working for Atheros.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked on my laptop.

before i waste time on another tutorial (no offense), do i need to be connected to the internet to do ANY part of this procedure? to download a package or anything?

---

