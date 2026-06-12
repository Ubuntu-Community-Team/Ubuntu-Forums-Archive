---
title: "Unsecured Wireless Connection"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by scamio on 2007-10-26
Hi guys

since a week I can not get connected with my wireless connection. Wicd says it is unsecured, but it was secured since a week ago. I surely did some stupid change, I am newabe!! Anyway I post you some output that may be useful in order to understand what's going  on:


```

>sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 172.16.35.149
netmask 255.255.224.0
gateway 172.16.63.254

auto ath0
iface ath0 inet dhcp

--------------------------------------------------------------

>ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:E3:B3:63:79
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3545 (3.4 KiB)  TX bytes:3342 (3.2 KiB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:DE:A3:FE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3316 (3.2 KiB)  TX bytes:3316 (3.2 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-B3-63-79-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7951 errors:0 dropped:0 overruns:0 frame:8915
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:643307 (628.2 KiB)  TX bytes:11222 (10.9 KiB)
          Interrupt:17

--------------------------------------------------------------------

>iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"802.11SSID"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:DD:18:D0
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/94  Signal level=-42 dBm  Noise level=-96 dBm
          Rx invalid nwid:1465  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

----------------------------------------------------------------------

>iwlist ath0 scan

ath0      Scan completed :
          Cell 01 - Address: 00:E0:98:DD:18:D0
                    ESSID:"802.11SSID"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200

------------------------------------------------------------------------------------

                   
>sudo iptables -L INPUT


Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.1.1          anywhere
ACCEPT     0    --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       0    --  anywhere             255.255.255.255
DROP       0    --  anywhere             172.16.63.255
DROP       0    --  224.0.0.0/8          anywhere
DROP       0    --  anywhere             224.0.0.0/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input'

-------------------------------------------------------------------------------------

sudo /etc/init.d/networking restart


 * Reconfiguring network interfaces...                        SIOCDELRT: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 3776
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:e3:b3:63:79
Sending on   LPF/ath0/00:16:e3:b3:63:79
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Operation not permitted
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:e3:b3:63:79
Sending on   LPF/ath0/00:16:e3:b3:63:79
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 81865 seconds.
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
                                                       [ OK ]

```

thank you very much for your help!!

---

### Post by scrooge_74 on 2007-10-26
What brand of card you have?

The system seems to have lots of cards detected

Get everything back to auto in the interfaces file like 

auto ath0
iface ath0 inet dhcp

And start a fresh

---

### Post by scamio on 2007-10-26
Hi
thanks for your answer. I have got an Ateron wireless card that is perfectly cofigurated if I start Kubuntu from CD which is the ath0. I then have a wired connection eth0.
This is my new interfaces file:

auto eth0
iface eth0 inet static
address 172.16.35.149
netmask 255.255.224.0
gateway 172.16.63.254

auto ath0
iface ath0 inet dhcp



any idea?:confused:

---

### Post by scrooge_74 on 2007-10-26
you have a conflict there

Hum weird? boot from the CD again and copy down what the /etc/network/interfaces says, maybe you can use that info to get it running when booting from the HD

---

### Post by kevdog on 2007-10-26
Are you sure you have a secure connection -- linux (not wicd or anything else) reports an unencrypted connection.  Its in your output:


> ```
ath0      Scan completed :
          Cell 01 - Address: 00:E0:98:DD:18:D0
                    ESSID:"802.11SSID"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    **[SIZE="4"]Encryption key:off[/SIZE]**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
```

---

### Post by scamio on 2007-10-27
Hi
thanks for the replies. I will try the CD booting and get back to you with an answer. I guess my connection is secure, I can get connected with Windows and I used to get connected with linux until a week ago. But I think you got the point. Maybe somehow Linux consider the connection not secure and does not allow me the connection. In this case, how can I tell Linux it can trust that connection?
thanks

---

### Post by scamio on 2007-10-27
Hi guys
no luck with the Kubuntu CD interface settings. I read several tread related to the same problem I have. s this some kind of unsolvable problem that force linux user to reinstall the OS? :confused:

---

