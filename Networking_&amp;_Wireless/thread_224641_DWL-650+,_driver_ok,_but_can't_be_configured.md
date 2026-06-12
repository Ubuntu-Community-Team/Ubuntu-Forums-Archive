---
title: "DWL-650+, driver ok, but can't be configured"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by baosheng on 2006-07-28
Hi guys, I encountered a strange problem.

I have just bought a D-link DWL-650+ wireless NIC. (hard ware version: B4, firmware version 1.9.3.101).
I inserted it into the PCMCIA slot and booted my computer. Then, in "System->Administration->Networking", I can see one item named "wireless lan"
At that time, the PWR LED is on and the link LED is off(there is no wireless station in my room).

I left it in the PCMCIA slot and rebooted the computer. 
This time, the PWR LED is off and the link LED is on.

But I can't see WLAN interface in the "System->Administration->Networking" menu this time.

So I tried the command "lspci" and got the following:
forrest@orioleQ:/forrest/LinuxSofts/Server$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751F Fast Ethernet PCI Express (rev 21)
0000:04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:05:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

The last two lines indicates the card has been driven. 
So I got confused why it doesn't work now.
I just reboot the computer.

Can anyone help me?
Thanks.

---

