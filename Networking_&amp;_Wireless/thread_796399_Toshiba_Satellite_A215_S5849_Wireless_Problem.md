---
title: "Toshiba Satellite A215 S5849 Wireless Problem"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by bkief12 on 2008-05-16
I am trying to configure the wireless on my new laptop. Follow this guide [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526) it said to restart my system after the restart when i loged in the system hanged then gave this error mesg ```
 There was an error starting the GNOME Settting daemon	

Some things such as themes, sounds or background settings may not work 
correctly.

The last error message was: 

Did not receive a reply. Possible causes include: the remote application did not 
send a reply, the message bus security policy block the reply, the reply timeout 
expired or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

```

There is not sound and the display parts like the start menu go to an older looking display.  

After a while the boot sound will go off and the start menu will return to the newer look. 

the driver i used was from the driver .exe from the Toshiba site 
```
ndiswrapper -l
net8187b : driver installed

```


Thanks,
bkief12

---

### Post by Tom--d on 2008-05-16
Go on the link on my Signature. That should work for your wireless.

The toshiba Wireless driver is the Vista driver. At the moment, ndiswrapper doesnt support the vista drvier.

---

### Post by bkief12 on 2008-05-16
I don't have the same wireless card as the one in the tutorial
here is my lspci
```
 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by bkief12 on 2008-05-16
Installed this atheros driver and it says that hardware is found but when i unlock the network setting it stays grayed out. And on rebooting still have the same problem that i described in the original post

---

