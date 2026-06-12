---
title: "Broadcom / eth2 not working."
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by vincentb on 2006-08-29
All,

I have the following wireless card in my PC.

[I]0000:05:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Linksys: Unknown device 0013
        Flags: bus master, fast devsel, latency 32, IRQ 74
        Memory at d1008000 (32-bit, non-prefetchable) [size=8K][/I]

and have installed ndiswrapper successfuly (I think)

[I]root@Ubuntu-vincent:/etc/network# ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
[/I]

I also guess the card is working, but was is strange is that it is linled to eth2 (while I would have expected wlan0). When is 'scan' with iwlist wia eth2, I get results (cell2 is my AP while cell 1 is my neighbour's one ...)

[I]eth2      Scan completed :
          Cell 01 - Address: 00:12:BF:15:53:63
                    ESSID:"dalmans"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0C:41:DE:0C:E7
                    ESSID:"vincentap"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-42 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

[/I]
so far so good ... But I do not succeed in routing all the traffic trhough eth2 (the wireless card). Can you have a look at this and tell me what is wrong with this sequence of commands? And why I can not route my traffic to eth2?

[I]root@Ubuntu-vincent:/etc/network# route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
root@Ubuntu-vincent:/etc/network# ifconfig eth0 down

root@Ubuntu-vincent:/etc/network# ifconfig eth2 up

root@Ubuntu-vincent:/etc/network# ifconfig
eth1      Lien encap:Ethernet  HWaddr 00:15:F2:AC:F5:0C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:74

eth2      Lien encap:Ethernet  HWaddr 00:0C:41:65:00:F5
          adr inet6: fe80::20c:41ff:fe65:f5/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2 erreurs:0 :0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:102 (102.0 b) Octets transmis:468 (468.0 b)
          Interruption:74 Mémoire:d1008000-d100a000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:958 erreurs:0 :0 overruns:0 frame:0
          TX packets:958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:471753 (460.6 KiB) Octets transmis:471753 (460.6 KiB)

root@Ubuntu-vincent:/etc/network# ifconfig eth2 192.168.1.2

root@Ubuntu-vincent:/etc/network# ifconfig
eth1      Lien encap:Ethernet  HWaddr 00:15:F2:AC:F5:0C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:74

eth2      Lien encap:Ethernet  HWaddr 00:0C:41:65:00:F5
          inet adr:192.168.1.2  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20c:41ff:fe65:f5/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2 erreurs:0 :0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:102 (102.0 b) Octets transmis:468 (468.0 b)
          Interruption:74 Mémoire:d1008000-d100a000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:958 erreurs:0 :0 overruns:0 frame:0
          TX packets:958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:471753 (460.6 KiB) Octets transmis:471753 (460.6 KiB)

root@Ubuntu-vincent:/etc/network# route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2

root@Ubuntu-vincent:/etc/network# route add default gw 192.168.1.1 dev eth2
[/I]
But nothing works when I *ifconfig eth0 down* and I have no access to internet via my gateway (192.168.1.1) I am pretty sure there is something wrong in the routing parameters but can not figure out the problem.

I am however well connected to my AP:

[I]root@Ubuntu-vincent:/home/vincent# iwconfig eth2
eth2      IEEE 802.11g  ESSID:"vincentap"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:DE:0C:E7
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:[SIZE="2"]XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX[/SIZE]   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-43 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/I]


Please ... help!
Thanks in advance,

Vincent

---

### Post by towsonu2003 on 2006-08-29
try taking down eth1 as well (ifconfig eth1 down) and than setup your ap to use dhcp and no security measure (wap wep etc) using its interface. than it is much easier:

ifconfig eth0 down
ifconfig eth1 down
ifconfgi eth2 up
iwlist eth2 scan
iwconfig eth2 essid whatever
dhclient eth2

once you get an ip, you should be good to go. 

also, if you still want static ip, do
ifconfig eth2 address x.x.x.x

and not 
ifconfig eth2 x.x.x.x

good luck :)

---

### Post by vincentb on 2006-08-29
Unfortunately, it not working.

But when I log on my AP, it confirms that the wireless card is well connected:

Wed Aug 30 00:13:40 2006 	Wireless PC connected 00:0C:41:65:00:F5

Which is well the MAC address of my eth2 card on my network.

Something strange also is that when I "ifconfig eth0 down", the 'ping 192.168.1.100' (ping eth0) is still responding.

How would this be possible ... 'cause when I 'ifconfig' my PC, the 'eth0' card is not listed anymore.

Thanks in advance,

Vincent

---

### Post by bensexson on 2006-08-29
post the output of sudo iwconfig eth2

---

### Post by vincentb on 2006-08-30
All,

thanks for your help. I think the problem came from the firewall. I have disabled it via Firestarter and everything was ok after that. I however still do not understand all the details for this problem ... I'll check and investigate more in depth.

I can connect to my AP, WEP is activated. Next step is to use WEPA ...

Anyway, thanks for your help: explaining problems to others is the first step to the solution.

Best regards,

Vincent

---

### Post by towsonu2003 on 2006-08-31
> **vincentb said:**
> 
thanks for your help. I think the problem came from the firewall. I have disabled it via Firestarter and everything was ok after that. I however still do not understand all the details for this problem ... I'll check and investigate more in depth.

ah firestarter :) my bad: I thought about it but assumed you don't have it installed... 
everytime you change the interface you are using (eth1 to eth2 to eth0 etc), you have to launch firestarter and let it know that the interface has changed (preferences -> network settings -> change the interface under "internet connected network device" to the one you're using)

---

