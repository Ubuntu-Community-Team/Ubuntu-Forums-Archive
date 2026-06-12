---
title: "Wireless internet connection"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by RGarcias on 2009-03-31
Hi, I've recently installed Ubuntu and my Internet connection doesn't always work. Sometimes it connects perfectly, right at start up, but sometimes it keeps asking for the password (although it's already specified) and ends up not making the connection.

And if I try it with Windows, it works perfectly.

Could you please explain to me (a "for dummies" explanation please) what might be causing this?

Thanks in advance! :)

---

### Post by 3rdalbum on 2009-03-31
What's the wireless chipset of the card? You can find out with "lspci" or "lsusb".

---

### Post by RGarcias on 2009-04-01
When I did lspci the information that appeared was basically:

Host bridge: ATI Technologies Inc RS690 Host Bridge
PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge
SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
USB Controller: ATI Technologies Inc SB600 USB
USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
IDE interface: ATI Technologies Inc SB600 IDE
ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Thanks for your help!

---

### Post by Scunnered on 2009-04-01
I have a similar experience to you with my connection.  99% of the time when I boot the system it will effect a connection.  When it calls for the password what I find best is to enter again the password. It will again search for the connection and fail but this time shut down the system. Do not restart, you must shut down the system and give it 20-30 seconds and then boot the system.

You should find that this will resolve the problem.

Trust this assists

---

### Post by aeiah on 2009-04-01
the useful bit is this line:

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

that's your wireless card, naturally. atheros cards are usually very well supported but obviously something isnt right. next time your connection drops, open a terminal and type:
```
dmesg
```

this'll give you your message buffer. its useful for error reporting of things like this. anything that looks related to wireless or just scary to you paste it here and we'll see what's causing the issue

---

### Post by lisati on 2009-04-01
The OP's chipset is similar to that in one of my laptops. One possibility to pencil in for the "check this out" list is a clash with a wireless signal from a neighbour's system. 

I recently had spontaneous disconnects and reconnects and eventually solved it by changing the wireless channel from the default to another - a neighbour's gear was putting out its signal on the same channel. This was roughly analogous to two radio stations broadcasting on the same frequency in the same area, and causing confusion at the receiver, and the solution was to get one of the stations to broadcasting on a different frequency.

---

### Post by RGarcias on 2009-04-01
I did the dmesg and here is the information that caught my attention:

[    0.620097] pnp 00:08: io resource (0x530-0x537) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling 
[    0.644254] ACPI: ACPI bus type pnp unregistered 
[    0.648063] pci 0000:00:05.0: BAR 7: can't allocate resource 
[    0.673044] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.673075] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved 
[    0.678456] pci 0000:00:05.0:   IO window: disabled 
[    0.678459] pci 0000:00:05.0:   MEM window: disabled 
[    0.678462] pci 0000:00:05.0:   PREFETCH window: disabled 
[    1.577572] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.577574] EDD information not available. 
[    2.229722] No dock devices found. 
[    2.728538] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit 
[    3.380047] ata3: failed due to HW bug, retry pmp=0 
[   15.859668] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps 
[   15.859677] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 
[   15.859681] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps 
[   15.859690] wifi0: H/W encryption support: WEP AES AES_CCM TKIP 
[   15.859694] wifi0: mac 10.2 phy 6.1 radio 10.2 
[   15.859698] wifi0: Use hw queue 1 for WME_AC_BE traffic 
[   15.859700] wifi0: Use hw queue 0 for WME_AC_BK traffic 
[   15.859702] wifi0: Use hw queue 2 for WME_AC_VI traffic 
[   15.859704] wifi0: Use hw queue 3 for WME_AC_VO traffic 
[   15.859706] wifi0: Use hw queue 8 for CAB traffic 
[   15.859707] wifi0: Use hw queue 9 for beacons 
[   16.044869] input: PC Speaker as /devices/platform/pcspkr/input/input6 
[   16.120856] wifi0: Atheros 5424/2424: mem=0xf8200000, irq=19 
[   17.620032] ACPI: EC: missing confirmations, switch off interrupt mode. 
[   18.013626] lp: driver loaded but no devices found 
[   21.506892] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[  121.285582] ath_rate_sample: no rates for 00:1b:9e:f5:f2:f3? 
[  121.285600] wifi0: invalid TX rate 0 (ath_tx_start: 7122) 


I also noticed that, like Scunnered said, the internet connects when I start the computer but doesn't when I do a restart.

Thanks again!

---

