---
title: "Atheros AR5B225 @ 14.04"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by skaunov on 2014-10-26
Hello.

Found out that there is no BT in my new Asus EB1505. I changed the wireless card to Atheros [COLOR=#333333][FONT=Roboto]AR5B225 , but it works only as Wi-Fi. I tried everything I know to make it live(compiled ath3k, installed additional antenna), though I'm not a BT expert.

Asus Eeebox has only standard Wi-Fi antenna in the back. [/FONT][/COLOR][COLOR=#333333][FONT=Roboto]AR5B225 has two pigtails 'main' and 'alt'. I tried to add [/FONT][/COLOR]
Airgain N2420 IPEX antenna[COLOR=#333333][FONT=Roboto] to the 'alt' pigtail, but it didn't help. Should I try some different kind of antenna, or problem is in another direction?[/FONT][/COLOR]

---

### Post by jeremy31 on 2014-10-26
I don't know if it can be made to work but what do you see from ```
lsusb
```

---

### Post by skaunov on 2014-10-27
> **jeremy31 said:**
> I don't know if it can be made to work but what do you see from ```
lsusb
```
Here it is. But why USB? It's an microPCI card pluged into mother-board.
```
Bus 002 Device 003: ID 0ac8:c40a Z-Star Microelectronics Corp. Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 004: ID 046a:0011 Cherry GmbH G83 (RS 6000) Keyboard
Bus 001 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jeremy31 on 2014-10-27
> **skaunov said:**
> Here it is. But why USB? It's an microPCI card pluged into mother-board.
```
Bus 002 Device 003: ID 0ac8:c40a Z-Star Microelectronics Corp. Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 004: ID 046a:0011 Cherry GmbH G83 (RS 6000) Keyboard
Bus 001 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

They normally show up as usb devices but nothing is listed.  What do you have for pci?```
lspci
```

---

### Post by skaunov on 2014-10-27
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
04:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```

---

### Post by jeremy31 on 2014-10-28
Strange that it didn't find the bluetooth chipset.  ```
dmesg | grep -e Bluetooth -e Alaska
```

The Atheros wifi card I have in a Lenovo is reported as AR9485 like yours but in the lsusb it shows AR3012 bluetooth..hopefully dmesg finds something of use

---

### Post by skaunov on 2014-10-28
BTW, I bought it used, but recently I mailed the seller and he confirmed that BT worked in his laptop(Dell,AFAIR). May be he just lies, but I had no option of any money back at this moment, so it's completely pointless to him.
```

[   21.668367] Bluetooth: Core ver 2.17
[   21.668416] Bluetooth: HCI device and connection manager initialized
[   21.668978] Bluetooth: HCI socket layer initialized
[   21.668985] Bluetooth: L2CAP socket layer initialized
[   21.668996] Bluetooth: SCO socket layer initialized
[   21.684446] Bluetooth: RFCOMM TTY layer initialized
[   21.684465] Bluetooth: RFCOMM socket layer initialized
[   21.684475] Bluetooth: RFCOMM ver 1.11
[   22.005656] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.005663] Bluetooth: BNEP filters: protocol multicast
[   22.005677] Bluetooth: BNEP socket layer initialized

```

---

### Post by jeremy31 on 2014-10-28
> **skaunov said:**
> BTW, I bought it used, but recently I mailed the seller and he confirmed that BT worked in his laptop(Dell,AFAIR). May be he just lies, but I had no option of any money back at this moment, so it's completely pointless to him.
```

[   21.668367] Bluetooth: Core ver 2.17
[   21.668416] Bluetooth: HCI device and connection manager initialized
[   21.668978] Bluetooth: HCI socket layer initialized
[   21.668985] Bluetooth: L2CAP socket layer initialized
[   21.668996] Bluetooth: SCO socket layer initialized
[   21.684446] Bluetooth: RFCOMM TTY layer initialized
[   21.684465] Bluetooth: RFCOMM socket layer initialized
[   21.684475] Bluetooth: RFCOMM ver 1.11
[   22.005656] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.005663] Bluetooth: BNEP filters: protocol multicast
[   22.005677] Bluetooth: BNEP socket layer initialized

```

It most likely did have working bluetooth in windows but there seems to be no sign of it being found in linux.  It could be an issue with a module for USB, someday I might have some time to mess around more with my toshiba as it doesn't find the bluetooth with my intel or atheros wifi cards

---

### Post by skaunov on 2014-10-28
> **jeremy31 said:**
> It most likely did have working bluetooth in windows but there seems to be no sign of it being found in linux.  It could be an issue with a module for USB, someday I might have some time to mess around more with my toshiba as it doesn't find the bluetooth with my intel or atheros wifi cards
I mean that there possibility that BT is just broken. Though it's very small since there is no visual damage of card, and confirmation of seller that he used it. I think he used it inWindows, yepp. =)

---

### Post by jeremy31 on 2014-10-28
> **skaunov said:**
> Hello.

Found out that there is no BT in my new Asus EB1505. I changed the wireless card to Atheros [COLOR=#333333][FONT=Roboto]AR5B225 , but it works only as Wi-Fi. I tried everything I know to make it live(compiled ath3k, installed additional antenna), though I'm not a BT expert.

Asus Eeebox has only standard Wi-Fi antenna in the back. [/FONT][/COLOR][COLOR=#333333][FONT=Roboto]AR5B225 has two pigtails 'main' and 'alt'. I tried to add [/FONT][/COLOR]
Airgain N2420 IPEX antenna[COLOR=#333333][FONT=Roboto] to the 'alt' pigtail, but it didn't help. Should I try some different kind of antenna, or problem is in another direction?[/FONT][/COLOR]

The issue might be that you added the Atheros card to the Asus, unless there is some setting in BIOS and it might even be a USB setting that keeps it from working.  I looked when I got home and it is the exact card I have(according to the label) but I can't find bluetooth at all when I install it in another computer

---

### Post by skaunov on 2014-10-28
I'll check my BIOS settings twice! Did I get you right: on the other computer you didn't manage to get BT working?

---

### Post by jeremy31 on 2014-10-29
> **skaunov said:**
> I'll check my BIOS settings twice! Did I get you right: on the other computer you didn't manage to get BT working?

Was the same as your issue as it didn't show up in lsusb but I couldn't test much with it because it is the only card my Lenovo can use due to whitelist

---

### Post by skaunov on 2014-10-29
Can't see anything relevant inBIOS. :*( It reports that connected devices are 1drive, 1keyboard, 1mouse, 2hubs. Very similar with lsusb.

---

### Post by jeremy31 on 2014-10-29
> **skaunov said:**
> Can't see anything relevant inBIOS. :*( It reports that connected devices are 1drive, 1keyboard, 1mouse, 2hubs. Very similar with lsusb.

Anything in BIOS regarding XHCI, EHCI, or UHCI?  I have a feeling that the xhci modules for linux are a bit imperfect at the time and the bluetooth from my Atheros shows as an xhci in lsusb -t

---

### Post by skaunov on 2014-10-30
> **jeremy31 said:**
> Anything in BIOS regarding XHCI, EHCI, or UHCI?  I have a feeling that the xhci modules for linux are a bit imperfect at the time and the bluetooth from my Atheros shows as an xhci in lsusb -t
Yes, XHCI, and EHCI; didn't understand its relevant, really thought it's only for USB mass storage speed. But its settings confuse me. I enabled XHCI(was Smart auto) and turned on Hands-off. I don't really understand should I hand it off, or, on contrary, disable it.

Does this setting indicate who operating the interface--- hardware or OS? And what is my case?

---

### Post by jeremy31 on 2014-10-30
> **skaunov said:**
> Yes, XHCI, and EHCI; didn't understand its relevant, really thought it's only for USB mass storage speed. But its settings confuse me. I enabled XHCI(was Smart auto) and turned on Hands-off. I don't really understand should I hand it off, or, on contrary, disable it.

Does this setting indicate who operating the interface--- hardware or OS? And what is my case?

I would try each of them to see if one setting will allow the bluetooth to be seen in lsusb

---

