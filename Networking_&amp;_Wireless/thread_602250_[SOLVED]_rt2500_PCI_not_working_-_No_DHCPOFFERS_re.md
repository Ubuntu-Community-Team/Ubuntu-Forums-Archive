---
title: "[SOLVED] rt2500 PCI not working - No DHCPOFFERS received"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by MrHyde on 2007-11-04
Hi,

I have installed a fresh install of Gutsy using the Alternate CD and base command line install.  I am now trying to get my wireless card to work and am not having much luck.  The card is one I salvaged from an old computer and works fine under Windows.  It is a no-name generic card, so I don't know who the manufacturer is.  

I followed the instructions as per the Ubuntu wiki, but am getting "No DHCPOFFERS received".  I can see lots of forum threads on the same error, but none seem to have a working solution.  I'll try and list everything I see on my system here.

[PHP]
vivek@supermachine:~$ lspci -v
<snip>
02:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Unknown device 18eb:5310
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at fddfa000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
<snip>
[/PHP]

This confirms that my card uses the RT2500 chipset from an unknown manufacturer.

[PHP]
vivek@supermachine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Mittal"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP]

This shows that the name is wlan0 and it is using the ESS = "Mittal"

[PHP]
vivek@supermachine:~$ sudo lshw -C network
[sudo] password for vivek:
  *-network:0
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: wmaster0
       version: 01
       serial: 00:50:18:2f:4c:ac
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:02:0f.0
       logical name: eth0
       version: 10
       serial: 00:1d:7d:93:32:48
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.103 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
[/PHP]

This shows that the driver being used for the wireless card is rt2500pci

[PHP]
vivek@supermachine:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Mittal
wireless-key 1111111111111111111111111111
wireless-channel 11
wireless-mode managed
[/PHP]

These are my settings in the /etc/network/interfaces file.

[PHP]
vivek@supermachine:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0D:88:B8:D8:4C
                    ESSID:"Mittal"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Signal level=-63 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000071afba02
[/PHP]

This shows that my router is being detected by the card.

[PHP]
vivek@supermachine:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:50:18:2f:4c:ac
Sending on   LPF/wlan0/00:50:18:2f:4c:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[/PHP]

This is what I get when I try to start the wlan0 network.  I have even tried it with WEP switched off.  I get the same result. 

I have even tried it with setting a static IP for the wlan0 end point, with no luck, which suggests it is not a DHCP issue, but something else. eth0 works fine with DHCP to the same router.

Also, I can't see any request in my router logs, which suggests that the card is not even able to communicate with the router, even though the scans show that the AP is there.

Can someone please tell me what else I can try.  

Thank you.
Vivek

---

### Post by MrHyde on 2007-11-04
This has been solved.  I have the card working now.  I followed the instructions in thread [http://ubuntuforums.org/showthread.php?t=602180](http://ubuntuforums.org/showthread.php?t=602180), but did not complete them as I got stuck on the copy module to another location but as the file extra/rt2500.ko did not exist. However, I don't know if it also did something else that could have affected this.

The other change I made was that I noticed that iwlist was showing me using Channel 1.  However, my router is set up on Channel 11, so my interfaces file said Channel 11.  As soon as I changed it to Channel 1, it started working.  I believe this change is the only thing that affected it, but due to the other module installations, I cannot be 100% sure.

---

