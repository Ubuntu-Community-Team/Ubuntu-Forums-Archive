---
title: "Wireless stopped working"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by Lucrezia on 2007-09-04
Hi,

I'm using ubuntu 7.04 updated.
I've been on holiday for a month and a friend of mine configured the network for me to be able to join the Wep wireless in my vacation home and the wireless in my university.

The wireless of the university was this:

[http://solisgate.uu.nl/solisgate-index-802.html](http://solisgate.uu.nl/solisgate-index-802.html)

And the how to for linux is:

[http://people.cs.uu.nl/koos/linux-8021x-solis-air.html](http://people.cs.uu.nl/koos/linux-8021x-solis-air.html)


Now that i'm back home i've an unprotected wireless (usually it has a mac adress list, but i removed it just for this). Before holyday everything was working fine, but now i can't connect to the wireless, i can just use the wire.

I've [this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034926718B08") gate.

I can connect to the gate, but it look like it's unplugged from internet. When i try to visit a site it says: "404 page not found". The same if i try both wireless or wired to the gate. 
But when i use a Ubuntu Live cd everything is working fine. Or when i connect straight to the gateway of my provider trough cable.

I don't have to format right? :D:D

In the next post my configs files :)

---

### Post by Lucrezia on 2007-09-04
iwconfig:

> 
calipso@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID:off/any
Mode:Managed Frequency=nan kHz Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:14 Missed beacon:0

vmnet1 no wireless extensions.

vmnet8 no wireless extensions.


Ifconfig:

> 
calipso@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:17:A4:CC:AE:39
inet addr:1.110.113.34 Bcast:1.110.113.255 Mask:255.255.255.0
inet6 addr: fe80::217:a4ff:fecc:ae39/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:17082 errors:2463 dropped:0 overruns:0 frame:2463
TX packets:16915 errors:0 dropped:0 overruns:0 carrier:0
collisions:3439 txqueuelen:1000
RX bytes:9885846 (9.4 MiB) TX bytes:6813397 (6.4 MiB)
Interrupt:16

eth1 Link encap:Ethernet HWaddr 00:192:38:49:6A
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:14 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0x6000 Memory:f4000000-f4000fff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:548 (548.0 b) TX bytes:548 (548.0 b)

vmnet1 Link encap:Ethernet HWaddr 00:50:56:C0:00:01
inet addr:172.16.101.1 Bcast:172.16.101.255 Mask:255.255.255.0
inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

vmnet8 Link encap:Ethernet HWaddr 00:50:56:C0:00:08
inet addr:192.168.1.1 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


> 
calipso@ubuntu:~$ sudo iwconfig eth1 essid linksys

calipso@ubuntu:~$ sudo iwconfig eth1 mode managed


calipso@ubuntu:~$ sudo iwconfig eth1 ap any

calipso@ubuntu:~$ sudo dhclient -s 192.168.1.1 eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:38:49:6a
Sending on LPF/eth1/00:19:d2:38:49:6a
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPDISCOVER on eth1 to 192.168.1.1 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 192.168.1.1 port 67
DHCPREQUEST on eth1 to 192.168.1.1 port 67


...


Killed

> 

calipso@ubuntu:~$ sudo !!
sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:38:49:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:f4000000-f4000fff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:a4:cc:ae:39
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half ip=1.110.113.34 latency=64 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:f4108000-f4109fff irq:16




> 
calipso@ubuntu:~$ sudo !!
sudo cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:17:a4:cc:ae:39 arp 1




> 
calipso@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



> 
calipso@ubuntu:~$ dmesg |grep wlan0
calipso@ubuntu:~$ 




wpa_supplicant.conf

> 
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=2
ap_scan=2

network={
        ssid="SOLIS-AIR"
        key_mgmt=IEEE8021X
        eap=TTLS
        phase2="auth=PAP"
        identity="ahAh"
	password="blabla"
}


---

### Post by tgalati4 on 2007-09-04
>sudo iwconfig eth0 "yournetwork's name" key open 34:46:24:AE:45

I think the problem is that you are set up for WPA security, not WEP (that is why you have a wpa_suplicant.conf file.)

Try renaming the wpa_suplicant.conf file to wpa_suplicant.conf.bak and then try the iwconfig line above.

---

### Post by Lucrezia on 2007-09-04
> 

calipso@ubuntu:~$ sudo iwconfig eth1 "linksys" key open 34:46:24:AE:45
Error : unrecognised wireless request "linksys"



i tried also with eth0

> 

calipso@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:42:15:68
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=99/100  Signal level=-24 dBm  Noise level=-24 dBm
                    Extra: Last beacon: 60ms ago

vmnet8    Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.




---

### Post by tgalati4 on 2007-09-06
I'm a bonehead:

That should be:


calipso@ubuntu:~$ sudo iwconfig eth1 essid "linksys" key open 34:46:24:AE:45

I forgot the essid option.  See: 

>man iwconfig

---

