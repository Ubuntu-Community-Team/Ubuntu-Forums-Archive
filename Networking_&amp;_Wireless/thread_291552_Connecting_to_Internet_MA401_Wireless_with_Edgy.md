---
title: "Connecting to Internet: MA401 Wireless with Edgy"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by skate1 on 2006-11-02
Hi All,

New to Linux, and it has been years since I was a Unix user.  This looks like a great forum.

Just completed my first install of Ubuntu.  The PC is an IBM Thinkpad T20.  The install went well, and I am able to ping and use Firefox when using my 10/100 connection.  No configuration required - it automatically detects/DHCPs and establishes the connection.

Unplugging the 10/100 link, I am now trying to get the Wifi connection to work.  I have a ~5 year old Netgear MA401 802.11b PCMCIA card which I used with the laptop when it was Win2000. 

The card worked on Win2000 this morning, so I know the card is still good.  Also, my other 802.11 enabled PCs are working fine, so the network and AP are up and running.

I have tried using the 'System->Administration->Networking' tool.  Checking/unchecking the card enable.  Confirming the ESSID and setting DHCP enable.  None of this seems to help the connectivity.

_Here's what I've tried so far:_

**ping 192.168.0.2** (another machine on my local network)
connect: Network is unreachable

**iwconfig**
eth1      IEEE 802.11b  ESSID:"80211"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:AA:BB:CC:0D   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=-6 dBm  Noise level=-145 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**ifconfig**
eth1      Link encap:Ethernet  HWaddr 00:30:AB:05:F7:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 


**lshw**
*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:ab:05:f7:64
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

**sudo ifup eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:30:ab:05:f7:64
Sending on   LPF/eth1/00:30:ab:05:f7:64
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[I]I am stumped on what to try next.  Thoughts?
Thanks!
[/I]

---

### Post by skate1 on 2006-11-03
Follow-up.  I have found the exact same results with a Lucent/Agere Orinoco Gold card with Hermes I chipset.

The driver is loaded.  I get signal strength and association with the correct AP.  I just can't get it to DHCP correctly.

Is there anything special that needs to be done to get dhclient to operate correctly on a wifi card?

---

### Post by skate1 on 2006-11-07
Yet another follow-up.  I find that the Orinoco card works perfectly (automatically detected, IP address assigned via DHCP, and internet connectivity works) when using the Edgy Eft LiveCD vs the HDD-installed version.

Searching these forums, I see this is a common problem.  Unfortunately, I am yet to find a solution.

---

