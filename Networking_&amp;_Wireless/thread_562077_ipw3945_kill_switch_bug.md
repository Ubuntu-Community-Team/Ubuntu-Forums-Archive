---
title: "ipw3945 kill switch bug"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by alauro on 2007-09-28
I've searched through the forums and still haven't come to a solution. The problem is that nothing has allowed me to change the kill switch setting. I've reinstalled ipw3945 and I've set the key bindings for Fn+F2, but nothing works. Does anyone have any more ideas of what I should do. Currently, I'm in the process of downloading the gutsy beta release and am going to boot live and see what happens.

Any suggestions would be helpful. Even if it entails opening up the darn laptop and changing the settings on the card by hand, if that's even possible. 

I'm just so :confused: and :mad: because I have really enjoyed ubuntu, but I've never gotten wireless to work on a laptop. 

thank you for any help.

---

### Post by noob12 on 2007-09-28
You may need to load a hotkey driver.  Can you post the make and model of your laptop as well as the output of **lspci -nn**  ?

---

### Post by alauro on 2007-09-28
The laptop is an hp compaq 6710b

I've included the output from several commands:
lspci -nn, dmesg | grep ipw, lsmod | grep ipw, and a section from lshw

Thank you very much

lspci -nn:

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
18:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)

dmesg | grep ipw
[   19.208000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   19.208000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.208000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   21.056000] ipw3945: Radio Frequency Kill Switch is On:

lsmod | grep ipw
ipw3945               119840  1 
ieee80211              35656  1 ipw3945

lshw
 *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:18:00.0
                logical name: eth0
                version: 02
                serial: 00:1a:4b:68:c7:40
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.77 ip=192.168.180.79 latency=0 module=tg3 multicast=yes

Thank you.

---

### Post by noob12 on 2007-09-28
I checked the rfswitch support matrix and it isn't listed.  It probably is a direct hardware-based switch.

(1) Check your BIOS settings
(2) On that laptop, are you sure the wireless switch is FN+F2?  Documentation indicates there is a single button that toggles it.

---

### Post by alauro on 2007-10-01
noob12,

thank you for responding - it definitely is a hardware switch - but I can't figure out how to turn it on/off. I've tried the FN+F2 thing several times to no avail and I've tried loading the Acer Hotkey Module - but I get a Cannot allocate memory error. I haven't checked the BIOS settings yet. That's next.

Tony

---

### Post by noob12 on 2007-10-01
No the acerhk module doesn't apply to you as far as I know.  Yes.  Check the BIOS.  Also, while I can't find specific info for that model, my interpretation of what I can see on the web is that it is a single button, not FN+F2.  Were you using FN+F2 (successfully) with Windows?

---

### Post by alauro on 2007-10-01
The laptop was brandnew when I got it and only booted it once as Windows, just long enough to download Ubuntu, so I never tried the FN+F2 button. However, you are correct, there is a single button based on some documentation that showed that there is a wireless button. There's a small panel above the keyboard area that contains 5 buttons/controls: power, info, wireless, display, and volume. This is the button that's supposed to toggle wireless. It didn't work at all.

But I finally found some BIOS-like Configuration options - it's not the actuall BIOS controls, but it did work. On this laptop - I pressed F10 and that took me to a BIOS-like settings manager. After trying several things under the Boot Device Configuration options and still nothing worked, I then reset values to default, and hokus pokus, wireless worked! 

I have not tried using the button - I'm a little scared at the moment since wireless is working and I don't want to mess it up. I will try it in a couple of days when I'm feeling adventurous. :)

Thanks for your help.

Tony

---

### Post by TeeCker on 2008-06-26
Hello guys I'm new here, but it doesen't matter.
My really great THANKS belongs to **alauro**,
because he has very very helped me to solve my problem.

I'm using HP Compaq nx6310, and I was thinking, that I will never use my integrated Bluetooth stack or my WLAN chip (Intel PRO/Wireless 3945ABG), because however I'm using ipw3945 driver, could't turn my WLAN on.
Everytime was an error occured: ipw3945: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.

So I tried to reset my BIOS settings to default, and really was everything working - Bluetooth and WLAN.

This little annomaly can be caused by stupid Windows drivers.
Before I've installed Kubuntu onto my machine, I was using Windows and can remember, that before deleting it from HDD, I turned WLAN and Bluetooth off (by the software way - direct in Windows)...and after installing Kubuntu begans my problems with this SWITCH.

I mean Windows was able to setup the BIOS so another operation system e.g. Linux, with another drivers couldn't change this settings.

After reseting BIOS to default, everything works perfect and Hardware RF Kill switch can be used to control Wireless Connection.


THANKS ONE MORE TIME TO*** alauro***

---

