---
title: "Wireless Connection Problem"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by markprice81 on 2006-07-26
I am having some problems connecting to my wireless router. I am a bit unsure of what I am doing and any help is appreciated. Here is the situation, I am running Dapper and have a Belkin F5D7000UK version 3000UK PCI card in my desktop. As far as I can tell I have set it up correctly with ndiswrapper. I am trying to connect to a linksys WRT54GS-UK wireless router. I am able to associate with the router but unable to recieve an IP address from it and unable to ping it.

The result of iwconfig is

lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"XXXX"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:B6:1B:AB:F6
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:XXXXXX  Security mode:open
          Link Quality=62/100  Signal level=-65 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

When I run ifconfig I get the following

eth0      Link encap:Ethernet  HWaddr 00:E0:18:A5:0C:9E
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fea5:c9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5037419 (4.8 MiB)  TX bytes:1397203 (1.3 MiB)
          Interrupt:9

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2609575 (2.4 MiB)  TX bytes:2609575 (2.4 MiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:A8:A7:5F
          inet6 addr: fe80::211:50ff:fea8:a75f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456 errors:1 dropped:1 overruns:0 carrier:0
          collisions:24 txqueuelen:1000
          RX bytes:11774 (11.4 KiB)  TX bytes:23744 (23.1 KiB)
          Interrupt:11

If I run dhclient I get the following output

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:11:50:a8:a7:5f
Sending on   LPF/ra0/00:11:50:a8:a7:5f
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Thanks in advance for the help.

Mark

---

### Post by philippe_carlo on 2006-07-26
If you enter the WEP key as 5 alphanumerical characters, then you have to set it with s: up front like this:

```
sudo iwconfig ra0 key s:xxxxx
```

That is a common problem. Also, you signal quality is on the low side, you may want to try moving closer to the router.

---

### Post by markprice81 on 2006-07-26
> **philippe_carlo said:**
> If you enter the WEP key as 5 alphanumerical characters, then you have to set it with s: up front like this:

```
sudo iwconfig ra0 key s:xxxxx
```

That is a common problem.

Sorry, I should have been clear, the key is not 5 alphanumeric characters. I just changed it rather than display the key over the internet.

> **philippe_carlo said:**
> 
Also, you signal quality is on the low side, you may want to try moving closer to the router.

They are currently about 2m apart. Does this mean I need to have my router sat next to my PC?

Mark

---

