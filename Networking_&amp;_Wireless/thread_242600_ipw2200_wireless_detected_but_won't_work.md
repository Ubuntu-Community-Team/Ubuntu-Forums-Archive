---
title: "ipw2200 wireless detected but won't work"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by ironyCurtain on 2006-08-23
Hi all.  I cannot for the life of me get my wireless to work on my Acer TravelMate 4650 laptop.  It is Intel Pro 2200 Wireless (Centrino), and it uses the ipw2200 driver.  My home wireless network uses 128-bit WEP encryption,  but I have been unable even to connect to a unsecured network in our apartment complex without encryption.  

It is detected on eth1, and it can see wireless networks in my area, but when I try to connect to my wireless network through Network Settings it says it is disconnected.  I installed wifi-radar, and I made more progress with it.  Like the wireless tool that came with Ubuntu it detects wireless access points, but it actually appears to send and receive packets with a connectivity level of ~90%.  However, after a minute or so it repeatedly connects and disconnects very quickly, switching between APs.

Taking a command line approach:

```

irony@acer:~$ lspci | grep -i '2200'
0000:05:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

irony@acer:~$ dmesg | grep -i '2200'
[17179591.592000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1[17179591.592000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.592000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179591.592000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[17179592.064000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

irony@acer:~$ sudo iwconfig eth1 essid "ChemLab Beacon" channel 11 mode managed key 123ABC...D45

irony@acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"ChemLab Beacon"
          Mode:Managed  Frequency=2.462 GHz  Access Point: FF:00:FF:00:FF:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

irony@acer:~$ sudo ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:12:f0:be:e2:02
Sending on   LPF/eth1/00:12:f0:be:e2:02
Sending on   Socket/fallback

irony@acer:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:12:f0:be:e2:02
Sending on   LPF/eth1/00:12:f0:be:e2:02
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

This is not working either.  Anyone have any ideas, or see something I'm doing blatantly wrong?  Any help would be much appreciated.

Edit:  By the way, this is with a completely fresh Dapper install.

---

### Post by ironyCurtain on 2006-08-24
Alright, so I solved it with a one-liner:

```

sudo iwconfig eth1 essid "ChemLab Beacon" key restricted <hex-key> mode managed

```

You need the restricted for WEP apparently, at least for this wireless chipset...?  Whatever, as long as it works.  :grin:

---

