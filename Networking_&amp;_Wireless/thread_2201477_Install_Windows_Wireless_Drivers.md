---
title: "Install Windows Wireless Drivers"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by borgward on 2014-01-24
I just installed on Compaq Evo N610c laptop. 

System Settings > Administration > Windows Wireless Drivers

The Wireless Network Drivers  window is up

Currently Installed Windows Drivers: is blank.

Where do I download the driver from? (I assume from Compaq, Tom's Hardware, etc) Where should the download go? (I assume Downloads)

---

### Post by chili555 on 2014-01-24
Are you certain it requires Windows drivers? Aren't there Linux drivers for your device? Maybe you just need firmware. What is your device? Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```

---

### Post by borgward on 2014-01-24
lspci -nn | grep 0280

~ $ lspci -nn | grep 0280
~ $

~ $ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV200 [Mobility Radeon 7500]
02:04.0 Communication controller: LSI Corporation LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:06.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
02:0e.0 USB controller: NEC Corporation USB (rev 41)
02:0e.1 USB controller: NEC Corporation USB (rev 41)
02:0e.2 USB controller: NEC Corporation USB 2.0 (rev 02)

---

### Post by chili555 on 2014-01-24
I see no wireless device. May we also see:```
lsusb
```Is this, by chance, a virtual machine?

---

### Post by borgward on 2014-01-24
~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Not virtual.

I just inserted my known good Netgear PCMCIALinux compatible MA401 card.

lspci does not see it either,eventhough it's light is blinking.

Duh -sorry I just looked up the Compaq Evo N610c specs. Did not see any mention of internal wireless card. I guess theywill have to find a PCMCIA card or USB wireless dongle.

---

### Post by chili555 on 2014-01-24
Wait! I'm corn-fused! Are we trying to get the known-good Netgear going here? And did you *just now* insert it? Is this different with it now inserted?```
lspci -nn
```

Or, are you trying to coax a built-in wireless device to life? If so, I suspect it may be defective, because it doesn't show up anywhere..

---

### Post by borgward on 2014-01-24
my inquirey was about onboard wireless. After getting no response from lspci -nn, and then not seeing it under the response from lspci, I thought I would insert my own PCMCIA card to see if it would show up. It did not under either lspci -nn or lspci. 

I am sorry, but just looked up the Compaq N610c specs. No mention of onboard wireless. I am not really trying to get the PCMCIA card running as it is mine, and the people who own the laptop will have to fined one or a USB wireless dongle.

---

### Post by chili555 on 2014-01-24
Ahhhh! Got it! 

There is about a thread a week here on the forum about known working USB devices and I recommend you research and buy carefully. Here is but one example: [http://ubuntuforums.org/showthread.php?t=2166676](http://ubuntuforums.org/showthread.php?t=2166676)

---

### Post by borgward on 2014-01-24
Yeah I have a Linux comatible USB dongle as well, but will pass the link to the Compaqs owner.

---

