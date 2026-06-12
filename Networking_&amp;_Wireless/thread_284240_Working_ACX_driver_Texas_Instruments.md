---
title: "Working ACX driver? Texas Instruments"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by GTR on 2006-10-25
I am trying to get my ABS wireless 54G PCI card to work with 6.06 and was wondering if anyone has a success with this Texas Instruments chipset. I have all the settings configured in Admin->Network for my wireless WEP network. Here's some code:
lshw
*-network
                description: Wireless interface
                product: ACX 111 54Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@02:00.0
                logical name: wlan0
                version: 00
                serial: 00:12:0e:20:a1:40
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=acx_pci multicast=yes wirele ss=IEEE 802.11b+/g+
                resources: iomemory:d8020000-d8021fff iomemory:d8000000-d801ffff  irq:11

lspci -v
0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Abocom Systems Inc: Unknown device ab90
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d8020000 (32-bit, non-prefetchable) [size=8K]
        Memory at d8000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"GT500"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:XXXX-0893-12   Security mode:open
          Power Management:off
          Link Quality=31/100  Signal level=4/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.

I was reading in WifiDocs that the ACX driver that comes with Ubuntu has bugs in it: [https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111)

Has anyone made or found a working driver for the Texas Instruments network controller? Should I try and use ndiswrapper and use the WinXP driver on the ABS cd even though a WinXP driver might crash the sytem? I wanted to check the board before trying to build the drivers per the link above since I am new to Linux.

---

