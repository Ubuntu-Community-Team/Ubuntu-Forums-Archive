---
title: "wireless help  BCM4318"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by voam on 2007-06-06
After convincing my father to swith his laptop to Ubuntu, I have having trouble with this wireless connection. When I setup the system I got wireless to work on my own wireless network, but when I took the computer over to his place I could not get it to connect so I don't think it is a driver issue. I installed the  The wired connection is fine from laptop to router to internet, but the wireless one is not. Can someone help me please?
 
 Here are some of the specs:
 Notebook: Acer Aspire 3000
Router: 2wire2700Hg-B

lspci:
```



00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

iwlist scan eth1
```

eth1      Scan completed :
          
          Cell 04 - Address: 00:14:95:CC:D0:81
                    ESSID:"2WIRE913"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-38 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 96ms ago
          
```

iwconfig
```

eth1      IEEE 802.11b/g  ESSID:"2WIRE913"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:95:CC:D0:81   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off

          Link Quality=66/100  Signal level=-42 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:32:C1:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:16:CE:36:C3:6B  
          inet6 addr: fe80::216:ceff:fe36:c36b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:317 errors:0 dropped:2 overruns:0 frame:0
          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14016 (13.6 KiB)  TX bytes:27660 (27.0 KiB)
          Interrupt:4 Base address:0x4000 

eth1:avah Link encap:Ethernet  HWaddr 00:16:CE:36:C3:6B  
          inet addr:169.254.7.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:4 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1330 (1.2 KiB)  TX bytes:1330 (1.2 Ki

```

Perhaps this will shed some light on the problem:
After running:
sudo /etc/init.d/networking restart

and then ifconfig the eth1 interface disappears:

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:32:C1:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1854 (1.8 KiB)  TX bytes:1854 (1.8 KiB)


```

Here is the output from the restart:
```

tom@tom-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 6053
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:ce:36:c3:6b
Sending on   LPF/eth1/00:16:ce:36:c3:6b
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFFLAGS: No such device
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
SIOCSIFFLAGS: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/eth1/00:16:ce:36:c3:6b
Sending on   LPF/eth1/00:16:ce:36:c3:6b
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
                                                                         [ OK ]
```

Can someone make heads or tails of this? I am really stumped....

Thanks in advance!

---

### Post by voam on 2007-06-06
Interestingly, when I use "roaming mode" it can see the network, and sees its strength, but I do not get assigned an IP address. By the way, I have disabled WEP on the router to simplify things. 

What are the steps to fix this?

---

### Post by tetujin on 2008-01-11
voam,

i'm having nearly the same behavior you describe on my own laptop.  while i'm operating on a dell inspiron 2650, i have the same linksys card as you -- the BMC4318.  for me, networking is fine for a certain amount of time -- i haven't pinned down yet when it dies, but it seems to be good for a few hours at least (and i'm connected via WEP).  then it dies and eth1 just... disappears.  it does come back when i reboot, though.

i know this is an old thread, but did you ever find a solution?  i'd like to stabilize the wifi on this machine without needing to reboot every x hours. :)

---

### Post by voam on 2008-01-12
To be honest I don't remember what the resolution was. I was setting up the laptop for someone else and I don't have easy access to it anymore.

Have you looked at the wifi docs?

[http://help.ubuntu.com/community/WifiDocs]("http://help.ubuntu.com/community/WifiDocs")

Sorry I can't be of more help.

---

