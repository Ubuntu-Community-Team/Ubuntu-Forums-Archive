---
title: "BCM4318 nearly working, please help"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by kadil on 2006-07-29
Hi,

I followed the howto to get my bcm4318 working with the native driver and wpa supplicant. Last night I was able to get "sudo iwlist eth1" to identify my access point. No such luck this morning.

right now, iwconfig returns:
 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


but when I try "sudo ifup eth1": 

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:15:f2:a0:b6:10
Sending on   LPF/eth1/00:15:f2:a0:b6:10
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 and "dmesg" returns:
dmesg=>
...
[4295702.440000] bcm43xx driver
[4295702.441000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 177
[4295988.023000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4296015.484000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Any assistance would really be appreciated.

Thanks,
Kim

---

### Post by kadil on 2006-07-29
I suspect one of my problems is that I am using wpa_supplicant version 4.something, and I need version 5. So I downloaded version 5.someting, but it is not so easy to compile on a vanilla dapper install without internet access. I think I will just do the ndiswrapper thing until the whole bcm solution is supported better. If I am missing something basic, pleaselet me know.

Thanks,
Kim

---

