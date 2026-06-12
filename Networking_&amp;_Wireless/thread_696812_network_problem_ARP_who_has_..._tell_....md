---
title: "network problem: ARP who has ... tell ..."
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by eben on 2008-02-14
Hi. I'm new to the Ubuntu community and I'm trying to get my network running. I have this problem since I moved to a students residence.The problem appeares only when I'm home,    I have internet for about 1 minutes and than it breaks up. The problem appeared on every distro i tested (mandriva, zenwalk, ubuntu). I suppose something with my ip route / ip rule table is wrong. But I don't know, i still feel like a newbe somehow.

**ifconfig**

```
henrik@d34-4:~$ ifconfig 
eth0      Protokoll:Ethernet  Hardware Adresse 00:D0:59:A9:3C:33  
          inet Adresse:141.53.200.223  Bcast:141.53.200.255  Maske:255.255.255.0
          inet6 Adresse: fe80::2d0:59ff:fea9:3c33/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4093 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3620968 (3.4 MB)  TX bytes:646407 (631.2 KB)

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:12668 (12.3 KB)  TX bytes:12668 (12.3 KB)

```

**ip route**

```

henrik@d34-4:~$ ip route
141.53.200.0/24 dev eth0  proto kernel  scope link  src 141.53.200.223 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 141.53.200.1 dev eth0 

```

**ip rule**
```

henrik@d34-4:~$ ip rule
0:      from all lookup local 
32766:  from all lookup main 
32767:  from all lookup default 

```

**wireshark output**

```

No.     Time        Source                Destination           Protocol Info
      1 0.000000    Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 1 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
      2 0.123550    141.53.200.129        141.53.200.255        NBNS     Name query NB YOUR-CF5ED83388<20>

Frame 2 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: AsustekC_07:f6:2e (00:15:f2:07:f6:2e), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.129 (141.53.200.129), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
      3 0.182636    Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 3 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
      4 0.956330    Cisco_5e:f1:a4        CDP/VTP/DTP/PAgP/UDLD CDP      Device ID: c3548-thael-2.netwrk.med.uni-greifswald.  Port ID: FastEthernet0/36  

Frame 4 (430 bytes on wire, 430 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Cisco Discovery Protocol

No.     Time        Source                Destination           Protocol Info
      5 1.581051    141.53.200.71         239.255.67.250        UDP      Source port: 1436  Destination port: 16680

Frame 5 (250 bytes on wire, 250 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:43:fa (01:00:5e:7f:43:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.67.250 (239.255.67.250)
User Datagram Protocol, Src Port: 1436 (1436), Dst Port: 16680 (16680)
Data (208 bytes)

0000  64 34 3a 62 6f 64 79 64 34 3a 68 61 73 68 32 30   d4:bodyd4:hash20
0010  3a 8d e0 74 09 d1 da 53 2f c0 27 e8 80 e4 38 46   :..t...S/.'...8F
0020  a4 ad 19 00 76 33 3a 72 69 64 69 32 36 39 65 34   ....v3:ridi269e4
0030  3a 73 65 65 64 69 30 65 34 3a 74 79 70 65 69 32   :seedi0e4:typei2
0040  65 65 34 3a 6f 72 69 67 64 32 3a 64 70 69 31 37   ee4:origd2:dpi17
0050  34 35 32 65 33 3a 64 70 32 69 31 37 34 35 32 65   452e3:dp2i17452e
0060  33 3a 65 69 70 31 33 3a 31 34 31 2e 35 33 2e 32   3:eip13:141.53.2
0070  30 30 2e 37 31 32 3a 69 64 34 30 3a 39 43 44 34   00.712:id40:9CD4
0080  30 36 41 39 32 37 30 41 35 34 37 32 42 32 45 31   06A9270A5472B2E1
0090  36 38 36 38 30 34 41 43 30 42 44 46 45 34 42 39   686804AC0BDFE4B9
00a0  39 38 42 43 33 3a 69 69 70 37 3a 30 2e 30 2e 30   98BC3:iip7:0.0.0
00b0  2e 30 32 3a 74 70 69 31 37 34 35 32 65 65 34 3a   .02:tpi17452ee4:
00c0  74 79 70 65 69 33 65 33 3a 76 65 72 69 31 65 65   typei3e3:veri1ee

No.     Time        Source                Destination           Protocol Info
      6 1.670321    CompalEl_a9:a0:8b     Broadcast             ARP      Who has 169.254.204.141?  Tell 0.0.0.0

Frame 6 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
      7 1.996332    Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 7 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
      8 2.699854    CompalEl_a9:a0:8b     Broadcast             ARP      Who has 169.254.204.141?  Tell 0.0.0.0

Frame 8 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
      9 3.214759    fe80::9deb:d381:c752:cc8d ff02::2               ICMPv6   Router solicitation

Frame 9 (70 bytes on wire, 70 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:02 (33:33:00:00:00:02)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
     10 3.729438    CompalEl_a9:a0:8b     Broadcast             ARP      Who has 169.254.204.141?  Tell 0.0.0.0

Frame 10 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     11 3.999251    Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 11 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     12 4.120758    141.53.200.71         239.255.67.250        UDP      Source port: 1436  Destination port: 16680

Frame 12 (250 bytes on wire, 250 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:43:fa (01:00:5e:7f:43:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.67.250 (239.255.67.250)
User Datagram Protocol, Src Port: 1436 (1436), Dst Port: 16680 (16680)
Data (208 bytes)

0000  64 34 3a 62 6f 64 79 64 34 3a 68 61 73 68 32 30   d4:bodyd4:hash20
0010  3a 12 a3 0f 7c d7 cb 0c 4e 78 40 1d 60 0e 78 c5   :...|...Nx@.`.x.
0020  48 d6 f3 a4 8c 33 3a 72 69 64 69 32 37 30 65 34   H....3:ridi270e4
0030  3a 73 65 65 64 69 30 65 34 3a 74 79 70 65 69 32   :seedi0e4:typei2
0040  65 65 34 3a 6f 72 69 67 64 32 3a 64 70 69 31 37   ee4:origd2:dpi17
0050  34 35 32 65 33 3a 64 70 32 69 31 37 34 35 32 65   452e3:dp2i17452e
0060  33 3a 65 69 70 31 33 3a 31 34 31 2e 35 33 2e 32   3:eip13:141.53.2
0070  30 30 2e 37 31 32 3a 69 64 34 30 3a 39 43 44 34   00.712:id40:9CD4
0080  30 36 41 39 32 37 30 41 35 34 37 32 42 32 45 31   06A9270A5472B2E1
0090  36 38 36 38 30 34 41 43 30 42 44 46 45 34 42 39   686804AC0BDFE4B9
00a0  39 38 42 43 33 3a 69 69 70 37 3a 30 2e 30 2e 30   98BC3:iip7:0.0.0
00b0  2e 30 32 3a 74 70 69 31 37 34 35 32 65 65 34 3a   .02:tpi17452ee4:
00c0  74 79 70 65 69 33 65 33 3a 76 65 72 69 31 65 65   typei3e3:veri1ee

No.     Time        Source                Destination           Protocol Info
     13 4.888381    141.53.200.42         141.53.200.255        NBNS     Name query NB 6125198D9574472<20>

Frame 13 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: UniwillC_48:70:b3 (00:03:0d:48:70:b3), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.42 (141.53.200.42), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     14 5.371779    85.75.122.103         141.53.200.101        TCP      34281 > 1255 [PSH, ACK] Seq=0 Ack=0 Win=65349 Len=90

Frame 14 (144 bytes on wire, 144 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Clevo_18:1b:32 (00:90:f5:18:1b:32)
Internet Protocol, Src: 85.75.122.103 (85.75.122.103), Dst: 141.53.200.101 (141.53.200.101)
Transmission Control Protocol, Src Port: 34281 (34281), Dst Port: 1255 (1255), Seq: 0, Ack: 0, Len: 90
Data (90 bytes)

0000  5c 0c 2f e3 d8 e6 38 39 a1 4d 77 0c 0c 37 79 90   \./...89.Mw..7y.
0010  94 07 3e c6 bd 69 c3 7c a4 e2 8c 63 21 df c6 4f   ..>..i.|...c!..O
0020  93 70 82 40 89 eb de 07 17 48 cc 78 12 a7 34 d3   .p.@.....H.x..4.
0030  42 72 b9 3c 50 b8 d1 c9 17 80 7d b2 e9 3a 3e 6d   Br.<P.....}..:>m
0040  ad 57 83 ec b5 85 5d 2f a5 c0 a8 8d e5 41 e9 85   .W....]/.....A..
0050  1f 5e 58 ca 2c ef fc e9 51 ce                     .^X.,...Q.

No.     Time        Source                Destination           Protocol Info
     15 5.433947    CompaqHp_88:bc:6c     Broadcast             ARP      Who has 141.53.200.42?  Tell 141.53.200.216

Frame 15 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompaqHp_88:bc:6c (00:0b:cd:88:bc:6c), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     16 5.544658    Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 16 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
     17 5.638119    141.53.200.42         141.53.200.255        NBNS     Name query NB 6125198D9574472<20>

Frame 17 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: UniwillC_48:70:b3 (00:03:0d:48:70:b3), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.42 (141.53.200.42), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     18 5.694766    Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 18 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
     19 5.996821    Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 19 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     20 6.240715    141.53.200.239        141.53.200.255        BROWSER  Domain/Workgroup Announcement ARBEITSGRUPPE, NT Workstation, Domain Enum

Frame 20 (258 bytes on wire, 258 bytes captured)
Ethernet II, Src: 3com_03:13:24 (00:01:02:03:13:24), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.239 (141.53.200.239), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
     21 6.312352    Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 21 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     22 7.492057    QuantaCo_25:1c:f9     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.82

Frame 22 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: QuantaCo_25:1c:f9 (00:c0:9f:25:1c:f9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     23 8.000298    Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 23 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     24 8.519935    141.53.200.109        239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 24 (143 bytes on wire, 143 bytes captured)
Ethernet II, Src: AppleCom_33:ab:c8 (00:0d:93:33:ab:c8), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.109 (141.53.200.109), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     25 9.549051    Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 25 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     26 9.997273    Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 26 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     27 10.372518   141.53.200.66         224.0.0.251           MDNS     Standard query PTR _appletv-pair._tcp.local, "QM" question PTR _appletv._tcp.local, "QM" question

Frame 27 (99 bytes on wire, 99 bytes captured)
Ethernet II, Src: CompalEl_0a:96:b8 (00:1b:38:0a:96:b8), Dst: 01:00:5e:00:00:fb (01:00:5e:00:00:fb)
Internet Protocol, Src: 141.53.200.66 (141.53.200.66), Dst: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     28 10.749509   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 28 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     29 10.795185   Enterasy_17:df:22     01:80:c2:00:00:20     GMRP     GMRP

Frame 29 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP Multicast Registration Protocol

No.     Time        Source                Destination           Protocol Info
     30 10.809799   141.53.200.38         141.53.200.255        BROWSER  Local Master Announcement MILICA, Workstation, Server, Print Queue Server, NT Workstation, Potential Browser, Master Browser

Frame 30 (243 bytes on wire, 243 bytes captured)
Ethernet II, Src: AsustekC_fa:50:d4 (00:1b:fc:fa:50:d4), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.38 (141.53.200.38), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
     31 11.286424   Micro-St_eb:25:61     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.51

Frame 31 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Micro-St_eb:25:61 (00:10:dc:eb:25:61), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     32 11.777162   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 32 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     33 11.997390   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 33 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     34 14.001155   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 34 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     35 15.998767   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 35 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     36 16.599593   CameoCom_3c:09:7e     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.105

Frame 36 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CameoCom_3c:09:7e (00:40:f4:3c:09:7e), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     37 16.845224   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 37 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
     38 16.944559   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 38 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
     39 17.998652   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 39 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     40 18.031047   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 40 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     41 18.983688   141.53.200.71         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 41 (143 bytes on wire, 143 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
     42 19.011659   00:1d:09:37:f4:92     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.81

Frame 42 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: 00:1d:09:37:f4:92 (00:1d:09:37:f4:92), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     43 19.213603   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 43 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     44 19.998535   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 44 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     45 20.272385   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 45 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     46 21.544931   Enterasy_17:df:22     01:80:c2:00:00:20     GMRP     GMRP

Frame 46 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP Multicast Registration Protocol

No.     Time        Source                Destination           Protocol Info
     47 21.998765   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 47 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     48 22.625639   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 48 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
     49 22.627707   169.254.204.141       224.0.0.22            IGMP     V3 Membership Report

Frame 49 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 169.254.204.141 (169.254.204.141), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     50 22.661358   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49152  Destination port: hostmon

Frame 50 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49152 (49152), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e8 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     51 22.661877   169.254.204.141       224.0.0.252           UDP      Source port: 49153  Destination port: hostmon

Frame 51 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 169.254.204.141 (169.254.204.141), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49153 (49153), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e8 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     52 22.688781   169.254.204.141       224.0.0.22            IGMP     V3 Membership Report

Frame 52 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 169.254.204.141 (169.254.204.141), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     53 22.688828   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 53 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
     54 22.762401   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49152  Destination port: hostmon

Frame 54 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49152 (49152), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e8 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     55 22.762410   169.254.204.141       224.0.0.252           UDP      Source port: 49153  Destination port: hostmon

Frame 55 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 169.254.204.141 (169.254.204.141), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49153 (49153), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e8 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     56 22.966931   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49154  Destination port: hostmon

Frame 56 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49154 (49154), Dst Port: hostmon (5355)
Data (26 bytes)

0000  25 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   %............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     57 22.967172   169.254.204.141       224.0.0.252           UDP      Source port: 49155  Destination port: hostmon

Frame 57 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 169.254.204.141 (169.254.204.141), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49155 (49155), Dst Port: hostmon (5355)
Data (26 bytes)

0000  25 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   %............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     58 23.066953   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49154  Destination port: hostmon

Frame 58 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49154 (49154), Dst Port: hostmon (5355)
Data (26 bytes)

0000  25 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   %............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     59 23.066976   169.254.204.141       224.0.0.252           UDP      Source port: 49155  Destination port: hostmon

Frame 59 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 169.254.204.141 (169.254.204.141), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49155 (49155), Dst Port: hostmon (5355)
Data (26 bytes)

0000  25 f1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   %............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     60 24.003007   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 60 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     61 25.042448   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 61 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     62 25.807723   0.0.0.0               255.255.255.255       DHCP     DHCP Request  - Transaction ID 0xf2851417

Frame 62 (348 bytes on wire, 348 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 0.0.0.0 (0.0.0.0), Dst: 255.255.255.255 (255.255.255.255)
User Datagram Protocol, Src Port: bootpc (68), Dst Port: bootps (67)
Bootstrap Protocol

No.     Time        Source                Destination           Protocol Info
     63 25.822889   141.53.200.1          255.255.255.255       DHCP     DHCP ACK      - Transaction ID 0xf2851417

Frame 63 (369 bytes on wire, 369 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.1 (141.53.200.1), Dst: 255.255.255.255 (255.255.255.255)
User Datagram Protocol, Src Port: bootps (67), Dst Port: bootpc (68)
Bootstrap Protocol

No.     Time        Source                Destination           Protocol Info
     64 26.000223   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 64 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     65 26.139129   141.53.200.138        141.53.200.255        BROWSER  Domain/Workgroup Announcement MSHEIMNETZ, NT Workstation, Domain Enum

Frame 65 (258 bytes on wire, 258 bytes captured)
Ethernet II, Src: Inventec_62:88:9b (00:a0:d1:62:88:9b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.138 (141.53.200.138), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
     66 26.210792   CompalEl_a9:a0:8b     Broadcast             ARP      Who has 141.53.200.23?  Tell 0.0.0.0

Frame 66 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     67 26.321547   CompalEl_a9:a0:8b     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.23

Frame 67 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     68 26.494499   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 68 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     69 26.841488   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 69 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     70 26.855168   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 70 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
     71 27.015228   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 71 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     72 27.016018   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49156  Destination port: hostmon

Frame 72 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49156 (49156), Dst Port: hostmon (5355)
Data (26 bytes)

0000  75 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   u............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     73 27.016315   141.53.200.23         224.0.0.252           UDP      Source port: 49157  Destination port: hostmon

Frame 73 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49157 (49157), Dst Port: hostmon (5355)
Data (26 bytes)

0000  75 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   u............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     74 27.017733   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 74 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
     75 27.115746   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49156  Destination port: hostmon

Frame 75 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49156 (49156), Dst Port: hostmon (5355)
Data (26 bytes)

0000  75 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   u............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     76 27.116731   141.53.200.23         224.0.0.252           UDP      Source port: 49157  Destination port: hostmon

Frame 76 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49157 (49157), Dst Port: hostmon (5355)
Data (26 bytes)

0000  75 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   u............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     77 27.240375   CompalEl_a9:a0:8b     Broadcast             ARP      Who has 141.53.200.23?  Tell 0.0.0.0

Frame 77 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     78 27.240391   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 78 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     79 27.240607   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 79 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
     80 27.330104   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49158  Destination port: hostmon

Frame 80 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49158 (49158), Dst Port: hostmon (5355)
Data (26 bytes)

0000  17 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     81 27.330371   141.53.200.23         224.0.0.252           UDP      Source port: 49159  Destination port: hostmon

Frame 81 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49159 (49159), Dst Port: hostmon (5355)
Data (26 bytes)

0000  17 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     82 27.427807   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49158  Destination port: hostmon

Frame 82 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49158 (49158), Dst Port: hostmon (5355)
Data (26 bytes)

0000  17 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     83 27.427824   141.53.200.23         224.0.0.252           UDP      Source port: 49159  Destination port: hostmon

Frame 83 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49159 (49159), Dst Port: hostmon (5355)
Data (26 bytes)

0000  17 f0 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
     84 27.617654   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 84 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     85 27.999158   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 85 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     86 28.088183   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<00>

Frame 86 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     87 28.269946   CompalEl_a9:a0:8b     Broadcast             ARP      Who has 141.53.200.23?  Tell 0.0.0.0

Frame 87 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     88 28.714107   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 88 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     89 28.795509   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 89 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
     90 28.845124   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 90 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
     91 28.847338   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<00>

Frame 91 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     92 29.611757   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<00>

Frame 92 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     93 30.001346   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 93 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
     94 30.307128   141.53.200.197        141.53.200.255        BROWSER  Host Announcement YANGYANG, Workstation, Server, NT Workstation, Potential Browser, Backup Browser

Frame 94 (243 bytes on wire, 243 bytes captured)
Ethernet II, Src: Toshiba_02:e5:2c (00:0e:7b:02:e5:2c), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.197 (141.53.200.197), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
     95 30.376076   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<00>

Frame 95 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     96 31.061162   00:1d:60:f1:65:2e     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.57

Frame 96 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: 00:1d:60:f1:65:2e (00:1d:60:f1:65:2e), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     97 31.141328   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<00>

Frame 97 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     98 31.904862   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<00>

Frame 98 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
     99 32.005931   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 99 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    100 32.669265   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<00>

Frame 100 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    101 33.245836   Enterasy_17:df:22     01:80:c2:00:00:20     GMRP     GMRP

Frame 101 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP Multicast Registration Protocol

No.     Time        Source                Destination           Protocol Info
    102 33.433593   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<00>

Frame 102 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    103 34.004975   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 103 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    104 34.176254   85.75.122.103         141.53.200.101        TCP      [TCP Retransmission] 34281 > 1255 [PSH, ACK] Seq=0 Ack=0 Win=65349 Len=90

Frame 104 (144 bytes on wire, 144 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Clevo_18:1b:32 (00:90:f5:18:1b:32)
Internet Protocol, Src: 85.75.122.103 (85.75.122.103), Dst: 141.53.200.101 (141.53.200.101)
Transmission Control Protocol, Src Port: 34281 (34281), Dst Port: 1255 (1255), Seq: 0, Ack: 0, Len: 90
Data (90 bytes)

0000  5c 0c 2f e3 d8 e6 38 39 a1 4d 77 0c 0c 37 79 90   \./...89.Mw..7y.
0010  94 07 3e c6 bd 69 c3 7c a4 e2 8c 63 21 df c6 4f   ..>..i.|...c!..O
0020  93 70 82 40 89 eb de 07 17 48 cc 78 12 a7 34 d3   .p.@.....H.x..4.
0030  42 72 b9 3c 50 b8 d1 c9 17 80 7d b2 e9 3a 3e 6d   Br.<P.....}..:>m
0040  ad 57 83 ec b5 85 5d 2f a5 c0 a8 8d e5 41 e9 85   .W....]/.....A..
0050  1f 5e 58 ca 2c ef fc e9 51 ce                     .^X.,...Q.

No.     Time        Source                Destination           Protocol Info
    105 34.214555   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<20>

Frame 105 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    106 34.977994   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<20>

Frame 106 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    107 35.157637   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 107 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    108 35.742391   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<20>

Frame 108 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    109 36.007013   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 109 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    110 36.172306   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 110 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    111 36.506707   141.53.200.23         141.53.200.255        NBNS     Registration NB KATJA-PC<20>

Frame 111 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    112 37.297246   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1e>

Frame 112 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    113 37.505485   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 113 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    114 38.006150   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 114 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    115 38.051047   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1e>

Frame 115 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    116 38.299170   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 116 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    117 38.311041   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 117 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    118 38.381703   141.53.200.23         239.255.255.250       UDP      Source port: 49160  Destination port: 3702

Frame 118 (1033 bytes on wire, 1033 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49160 (49160), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 33 62 37   eID>urn:uuid:3b7
0210  33 33 30 62 32 2d 34 30 35 38 2d 34 39 65 33 2d   330b2-4058-49e3-
0220  61 32 61 65 2d 34 66 62 38 63 35 66 31 64 31 30   a2ae-4fb8c5f1d10
0230  36 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   6</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 31 22 3e 3c   sageNumber="1"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    119 38.382957   fe80::9deb:d381:c752:cc8d ff02::c               UDP      Source port: 49161  Destination port: 3702

Frame 119 (1053 bytes on wire, 1053 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49161 (49161), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 33 62 37   eID>urn:uuid:3b7
0210  33 33 30 62 32 2d 34 30 35 38 2d 34 39 65 33 2d   330b2-4058-49e3-
0220  61 32 61 65 2d 34 66 62 38 63 35 66 31 64 31 30   a2ae-4fb8c5f1d10
0230  36 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   6</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 31 22 3e 3c   sageNumber="1"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    120 38.385994   CompalEl_d8:90:70     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.110

Frame 120 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_d8:90:70 (00:02:3f:d8:90:70), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    121 38.508540   141.53.200.23         239.255.255.250       UDP      Source port: 49160  Destination port: 3702

Frame 121 (1033 bytes on wire, 1033 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49160 (49160), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 33 62 37   eID>urn:uuid:3b7
0210  33 33 30 62 32 2d 34 30 35 38 2d 34 39 65 33 2d   330b2-4058-49e3-
0220  61 32 61 65 2d 34 66 62 38 63 35 66 31 64 31 30   a2ae-4fb8c5f1d10
0230  36 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   6</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 31 22 3e 3c   sageNumber="1"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    122 38.565763   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 122 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    123 38.565836   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 123 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    124 38.697315   fe80::9deb:d381:c752:cc8d ff02::c               UDP      Source port: 49161  Destination port: 3702

Frame 124 (1053 bytes on wire, 1053 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49161 (49161), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 33 62 37   eID>urn:uuid:3b7
0210  33 33 30 62 32 2d 34 30 35 38 2d 34 39 65 33 2d   330b2-4058-49e3-
0220  61 32 61 65 2d 34 66 62 38 63 35 66 31 64 31 30   a2ae-4fb8c5f1d10
0230  36 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   6</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 31 22 3e 3c   sageNumber="1"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    125 38.794679   CompalEl_a9:a0:8b     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.23

Frame 125 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    126 38.815403   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1e>

Frame 126 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    127 38.850955   141.53.200.173        141.53.200.255        BROWSER  Local Master Announcement MARTINLABTOP, Workstation, Server, NT Workstation, Potential Browser, Master Browser

Frame 127 (256 bytes on wire, 256 bytes captured)
Ethernet II, Src: CompalEl_b5:f7:bd (00:02:3f:b5:f7:bd), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.173 (141.53.200.173), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    128 39.579843   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1e>

Frame 128 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    129 39.583256   CompalEl_a9:a0:8b     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.23

Frame 129 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    130 39.741160   141.53.200.71         239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 130 (324 bytes on wire, 324 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    131 39.754653   141.53.200.71         239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 131 (376 bytes on wire, 376 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    132 39.756384   141.53.200.71         239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 132 (390 bytes on wire, 390 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    133 39.764900   141.53.200.71         239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 133 (388 bytes on wire, 388 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    134 39.767312   141.53.200.71         239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 134 (333 bytes on wire, 333 bytes captured)
Ethernet II, Src: MitacInt_74:47:66 (00:40:d0:74:47:66), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.71 (141.53.200.71), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    135 39.832043   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49165  Destination port: hostmon

Frame 135 (86 bytes on wire, 86 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49165 (49165), Dst Port: hostmon (5355)
Data (24 bytes)

0000  eb f6 00 00 00 01 00 00 00 00 00 00 06 69 73 61   .............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    136 39.832369   141.53.200.23         224.0.0.252           UDP      Source port: 49166  Destination port: hostmon

Frame 136 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49166 (49166), Dst Port: hostmon (5355)
Data (24 bytes)

0000  eb f6 00 00 00 01 00 00 00 00 00 00 06 69 73 61   .............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    137 39.938992   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49165  Destination port: hostmon

Frame 137 (86 bytes on wire, 86 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49165 (49165), Dst Port: hostmon (5355)
Data (24 bytes)

0000  eb f6 00 00 00 01 00 00 00 00 00 00 06 69 73 61   .............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    138 39.939068   141.53.200.23         224.0.0.252           UDP      Source port: 49166  Destination port: hostmon

Frame 138 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49166 (49166), Dst Port: hostmon (5355)
Data (24 bytes)

0000  eb f6 00 00 00 01 00 00 00 00 00 00 06 69 73 61   .............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    139 40.007815   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 139 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    140 40.142391   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 140 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    141 40.346124   141.53.200.23         141.53.200.255        BROWSER  Request Announcement KATJA-PC

Frame 141 (221 bytes on wire, 221 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    142 40.572545   141.53.200.23         141.53.200.255        BROWSER  Host Announcement KATJA-PC, Workstation, Server, NT Workstation, Potential Browser

Frame 142 (243 bytes on wire, 243 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    143 40.905773   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 143 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    144 41.255046   CompalEl_0a:96:b8     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.66

Frame 144 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_0a:96:b8 (00:1b:38:0a:96:b8), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    145 41.670129   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 145 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    146 41.869370   141.53.200.23         141.53.200.255        BROWSER  Request Announcement KATJA-PC

Frame 146 (221 bytes on wire, 221 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    147 42.005818   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 147 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    148 42.179769   141.53.200.89         141.53.200.255        NBNS     Name query NB YOUR-CF5ED83388<20>

Frame 148 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Sony_2f:8d:fe (00:13:a9:2f:8d:fe), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.89 (141.53.200.89), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    149 42.179857   Inventec_62:88:9b     Broadcast             ARP      Who has 141.53.200.89?  Tell 141.53.200.138

Frame 149 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Inventec_62:88:9b (00:a0:d1:62:88:9b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    150 42.200938   141.53.200.197        141.53.200.255        NBNS     Name query NB VALERIA<20>

Frame 150 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_02:e5:2c (00:0e:7b:02:e5:2c), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.197 (141.53.200.197), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    151 42.201036   QuantaCo_f8:96:dc     Broadcast             ARP      Who has 141.53.200.197?  Tell 141.53.200.88

Frame 151 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: QuantaCo_f8:96:dc (00:c0:9f:f8:96:dc), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    152 42.611372   141.53.200.23         255.255.255.255       DHCP     DHCP Inform   - Transaction ID 0xb6d3ac62

Frame 152 (342 bytes on wire, 342 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 255.255.255.255 (255.255.255.255)
User Datagram Protocol, Src Port: bootpc (68), Dst Port: bootps (67)
Bootstrap Protocol

No.     Time        Source                Destination           Protocol Info
    153 42.832526   141.53.200.23         141.53.200.255        NBNS     Name query NB WPAD.DE.<00>

Frame 153 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    154 42.834589   141.53.200.23         141.53.200.255        NBNS     Name query NB WPAD.DE.<00>

Frame 154 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    155 42.915765   141.53.200.89         141.53.200.255        NBNS     Name query NB YOUR-CF5ED83388<20>

Frame 155 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Sony_2f:8d:fe (00:13:a9:2f:8d:fe), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.89 (141.53.200.89), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    156 43.196184   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 156 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    157 43.196215   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 157 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    158 43.198741   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 158 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    159 43.198851   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 159 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    160 43.266294   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 160 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    161 43.266832   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 161 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    162 43.267527   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 162 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    163 43.267854   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 163 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    164 43.270511   141.53.200.23         239.255.255.250       UDP      Source port: 49160  Destination port: 3702

Frame 164 (1033 bytes on wire, 1033 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49160 (49160), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 65 35 61   eID>urn:uuid:e5a
0210  63 63 63 64 32 2d 65 32 34 35 2d 34 33 32 30 2d   cccd2-e245-4320-
0220  38 31 30 35 2d 35 61 66 39 39 37 65 64 30 39 38   8105-5af997ed098
0230  61 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   a</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 32 22 3e 3c   sageNumber="2"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    165 43.272074   fe80::9deb:d381:c752:cc8d ff02::c               UDP      Source port: 49161  Destination port: 3702

Frame 165 (1053 bytes on wire, 1053 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49161 (49161), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 65 35 61   eID>urn:uuid:e5a
0210  63 63 63 64 32 2d 65 32 34 35 2d 34 33 32 30 2d   cccd2-e245-4320-
0220  38 31 30 35 2d 35 61 66 39 39 37 65 64 30 39 38   8105-5af997ed098
0230  61 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   a</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 32 22 3e 3c   sageNumber="2"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    166 43.284047   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 166 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    167 43.284347   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 167 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    168 43.285407   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49168  Destination port: hostmon

Frame 168 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49168 (49168), Dst Port: hostmon (5355)
Data (26 bytes)

0000  d1 f8 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    169 43.285866   141.53.200.23         224.0.0.252           UDP      Source port: 49169  Destination port: hostmon

Frame 169 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49169 (49169), Dst Port: hostmon (5355)
Data (26 bytes)

0000  d1 f8 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    170 43.371339   141.53.200.23         141.53.200.255        BROWSER  Request Announcement KATJA-PC

Frame 170 (221 bytes on wire, 221 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    171 43.388036   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49168  Destination port: hostmon

Frame 171 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49168 (49168), Dst Port: hostmon (5355)
Data (26 bytes)

0000  d1 f8 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    172 43.388062   141.53.200.23         224.0.0.252           UDP      Source port: 49169  Destination port: hostmon

Frame 172 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49169 (49169), Dst Port: hostmon (5355)
Data (26 bytes)

0000  d1 f8 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    173 43.412640   141.53.200.23         239.255.255.250       UDP      Source port: 49160  Destination port: 3702

Frame 173 (1033 bytes on wire, 1033 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49160 (49160), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 65 35 61   eID>urn:uuid:e5a
0210  63 63 63 64 32 2d 65 32 34 35 2d 34 33 32 30 2d   cccd2-e245-4320-
0220  38 31 30 35 2d 35 61 66 39 39 37 65 64 30 39 38   8105-5af997ed098
0230  61 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   a</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 32 22 3e 3c   sageNumber="2"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    174 43.463689   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 174 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    175 43.522922   fe80::9deb:d381:c752:cc8d ff02::c               UDP      Source port: 49161  Destination port: 3702

Frame 175 (1053 bytes on wire, 1053 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49161 (49161), Dst Port: 3702 (3702)
Data (991 bytes)

0000  3c 3f 78 6d 6c 20 76 65 72 73 69 6f 6e 3d 22 31   <?xml version="1
0010  2e 30 22 20 65 6e 63 6f 64 69 6e 67 3d 22 75 74   .0" encoding="ut
0020  66 2d 38 22 20 3f 3e 0a 3c 73 6f 61 70 3a 45 6e   f-8" ?>.<soap:En
0030  76 65 6c 6f 70 65 20 78 6d 6c 6e 73 3a 73 6f 61   velope xmlns:soa
0040  70 3d 22 68 74 74 70 3a 2f 2f 77 77 77 2e 77 33   p="http://www.w3
0050  2e 6f 72 67 2f 32 30 30 33 2f 30 35 2f 73 6f 61   .org/2003/05/soa
0060  70 2d 65 6e 76 65 6c 6f 70 65 22 20 78 6d 6c 6e   p-envelope" xmln
0070  73 3a 77 73 61 3d 22 68 74 74 70 3a 2f 2f 73 63   s:wsa="http://sc
0080  68 65 6d 61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72   hemas.xmlsoap.or
0090  67 2f 77 73 2f 32 30 30 34 2f 30 38 2f 61 64 64   g/ws/2004/08/add
00a0  72 65 73 73 69 6e 67 22 20 78 6d 6c 6e 73 3a 77   ressing" xmlns:w
00b0  73 64 3d 22 68 74 74 70 3a 2f 2f 73 63 68 65 6d   sd="http://schem
00c0  61 73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77   as.xmlsoap.org/w
00d0  73 2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76   s/2005/04/discov
00e0  65 72 79 22 20 78 6d 6c 6e 73 3a 77 73 64 70 3d   ery" xmlns:wsdp=
00f0  22 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61 73 2e   "http://schemas.
0100  78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73 2f 32   xmlsoap.org/ws/2
0110  30 30 36 2f 30 32 2f 64 65 76 70 72 6f 66 22 20   006/02/devprof" 
0120  78 6d 6c 6e 73 3a 70 75 62 3d 22 68 74 74 70 3a   xmlns:pub="http:
0130  2f 2f 73 63 68 65 6d 61 73 2e 6d 69 63 72 6f 73   //schemas.micros
0140  6f 66 74 2e 63 6f 6d 2f 77 69 6e 64 6f 77 73 2f   oft.com/windows/
0150  70 75 62 2f 32 30 30 35 2f 30 37 22 3e 3c 73 6f   pub/2005/07"><so
0160  61 70 3a 48 65 61 64 65 72 3e 3c 77 73 61 3a 54   ap:Header><wsa:T
0170  6f 3e 75 72 6e 3a 73 63 68 65 6d 61 73 2d 78 6d   o>urn:schemas-xm
0180  6c 73 6f 61 70 2d 6f 72 67 3a 77 73 3a 32 30 30   lsoap-org:ws:200
0190  35 3a 30 34 3a 64 69 73 63 6f 76 65 72 79 3c 2f   5:04:discovery</
01a0  77 73 61 3a 54 6f 3e 3c 77 73 61 3a 41 63 74 69   wsa:To><wsa:Acti
01b0  6f 6e 3e 68 74 74 70 3a 2f 2f 73 63 68 65 6d 61   on>http://schema
01c0  73 2e 78 6d 6c 73 6f 61 70 2e 6f 72 67 2f 77 73   s.xmlsoap.org/ws
01d0  2f 32 30 30 35 2f 30 34 2f 64 69 73 63 6f 76 65   /2005/04/discove
01e0  72 79 2f 48 65 6c 6c 6f 3c 2f 77 73 61 3a 41 63   ry/Hello</wsa:Ac
01f0  74 69 6f 6e 3e 3c 77 73 61 3a 4d 65 73 73 61 67   tion><wsa:Messag
0200  65 49 44 3e 75 72 6e 3a 75 75 69 64 3a 65 35 61   eID>urn:uuid:e5a
0210  63 63 63 64 32 2d 65 32 34 35 2d 34 33 32 30 2d   cccd2-e245-4320-
0220  38 31 30 35 2d 35 61 66 39 39 37 65 64 30 39 38   8105-5af997ed098
0230  61 3c 2f 77 73 61 3a 4d 65 73 73 61 67 65 49 44   a</wsa:MessageID
0240  3e 3c 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63   ><wsd:AppSequenc
0250  65 20 49 6e 73 74 61 6e 63 65 49 64 3d 22 39 30   e InstanceId="90
0260  22 20 53 65 71 75 65 6e 63 65 49 64 3d 22 75 72   " SequenceId="ur
0270  6e 3a 75 75 69 64 3a 34 35 34 61 31 39 65 36 2d   n:uuid:454a19e6-
0280  31 35 37 31 2d 34 34 66 38 2d 61 33 32 36 2d 39   1571-44f8-a326-9
0290  38 35 36 39 37 38 62 64 63 64 64 22 20 4d 65 73   856978bdcdd" Mes
02a0  73 61 67 65 4e 75 6d 62 65 72 3d 22 32 22 3e 3c   sageNumber="2"><
02b0  2f 77 73 64 3a 41 70 70 53 65 71 75 65 6e 63 65   /wsd:AppSequence
02c0  3e 3c 2f 73 6f 61 70 3a 48 65 61 64 65 72 3e 3c   ></soap:Header><
02d0  73 6f 61 70 3a 42 6f 64 79 3e 3c 77 73 64 3a 48   soap:Body><wsd:H
02e0  65 6c 6c 6f 3e 3c 77 73 61 3a 45 6e 64 70 6f 69   ello><wsa:Endpoi
02f0  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 61   ntReference><wsa
0300  3a 41 64 64 72 65 73 73 3e 75 72 6e 3a 75 75 69   :Address>urn:uui
0310  64 3a 39 32 32 36 63 39 36 63 2d 39 33 64 64 2d   d:9226c96c-93dd-
0320  34 33 34 38 2d 38 35 64 65 2d 35 65 31 33 63 61   4348-85de-5e13ca
0330  65 66 32 65 62 36 3c 2f 77 73 61 3a 41 64 64 72   ef2eb6</wsa:Addr
0340  65 73 73 3e 3c 2f 77 73 61 3a 45 6e 64 70 6f 69   ess></wsa:Endpoi
0350  6e 74 52 65 66 65 72 65 6e 63 65 3e 3c 77 73 64   ntReference><wsd
0360  3a 54 79 70 65 73 3e 77 73 64 70 3a 44 65 76 69   :Types>wsdp:Devi
0370  63 65 20 70 75 62 3a 43 6f 6d 70 75 74 65 72 3c   ce pub:Computer<
0380  2f 77 73 64 3a 54 79 70 65 73 3e 3c 77 73 64 3a   /wsd:Types><wsd:
0390  4d 65 74 61 64 61 74 61 56 65 72 73 69 6f 6e 3e   MetadataVersion>
03a0  32 3c 2f 77 73 64 3a 4d 65 74 61 64 61 74 61 56   2</wsd:MetadataV
03b0  65 72 73 69 6f 6e 3e 3c 2f 77 73 64 3a 48 65 6c   ersion></wsd:Hel
03c0  6c 6f 3e 3c 2f 73 6f 61 70 3a 42 6f 64 79 3e 3c   lo></soap:Body><
03d0  2f 73 6f 61 70 3a 45 6e 76 65 6c 6f 70 65 3e      /soap:Envelope>

No.     Time        Source                Destination           Protocol Info
    176 43.588849   141.53.200.23         141.53.200.255        NBNS     Name query NB WPAD.DE.<00>

Frame 176 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    177 43.588941   141.53.200.23         141.53.200.255        NBNS     Name query NB WPAD.DE.<00>

Frame 177 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    178 43.594368   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49171  Destination port: hostmon

Frame 178 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49171 (49171), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e1 fb 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    179 43.594849   141.53.200.23         224.0.0.252           UDP      Source port: 49172  Destination port: hostmon

Frame 179 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49172 (49172), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e1 fb 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    180 43.696468   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 180 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
    181 43.713658   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 181 (62 bytes on wire, 62 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    182 43.713894   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 182 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    183 43.715608   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49171  Destination port: hostmon

Frame 183 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49171 (49171), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e1 fb 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    184 43.715683   141.53.200.23         224.0.0.252           UDP      Source port: 49172  Destination port: hostmon

Frame 184 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49172 (49172), Dst Port: hostmon (5355)
Data (26 bytes)

0000  e1 fb 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    185 43.747095   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 185 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
    186 44.006032   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 186 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    187 44.338907   141.53.200.23         141.53.200.255        NBNS     Name query NB WPAD.DE.<00>

Frame 187 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    188 44.338931   141.53.200.23         141.53.200.255        NBNS     Name query NB WPAD.DE.<00>

Frame 188 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    189 44.654161   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 189 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    190 44.871153   141.53.200.23         141.53.200.255        BROWSER  Request Announcement KATJA-PC

Frame 190 (221 bytes on wire, 221 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    191 45.735592   217.17.45.147         141.53.200.101        TCP      https > 1050 [FIN, ACK] Seq=0 Ack=0 Win=5840 Len=0

Frame 191 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Clevo_18:1b:32 (00:90:f5:18:1b:32)
Internet Protocol, Src: 217.17.45.147 (217.17.45.147), Dst: 141.53.200.101 (141.53.200.101)
Transmission Control Protocol, Src Port: https (443), Dst Port: 1050 (1050), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    192 45.792453   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 192 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    193 46.008419   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 193 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    194 46.372539   141.53.200.23         141.53.200.255        BROWSER  Browser Election Request

Frame 194 (233 bytes on wire, 233 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    195 46.523511   141.53.200.109        239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 195 (326 bytes on wire, 326 bytes captured)
Ethernet II, Src: AppleCom_33:ab:c8 (00:0d:93:33:ab:c8), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.109 (141.53.200.109), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    196 46.526579   141.53.200.109        239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 196 (378 bytes on wire, 378 bytes captured)
Ethernet II, Src: AppleCom_33:ab:c8 (00:0d:93:33:ab:c8), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.109 (141.53.200.109), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    197 46.530707   141.53.200.109        239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 197 (392 bytes on wire, 392 bytes captured)
Ethernet II, Src: AppleCom_33:ab:c8 (00:0d:93:33:ab:c8), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.109 (141.53.200.109), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    198 46.535917   141.53.200.109        239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 198 (390 bytes on wire, 390 bytes captured)
Ethernet II, Src: AppleCom_33:ab:c8 (00:0d:93:33:ab:c8), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.109 (141.53.200.109), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    199 46.538569   141.53.200.109        239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 199 (335 bytes on wire, 335 bytes captured)
Ethernet II, Src: AppleCom_33:ab:c8 (00:0d:93:33:ab:c8), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.109 (141.53.200.109), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 8008 (8008), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    200 46.941356   217.17.45.147         141.53.200.101        TCP      https > 1050 [FIN, ACK] Seq=0 Ack=0 Win=5840 Len=0

Frame 200 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Clevo_18:1b:32 (00:90:f5:18:1b:32)
Internet Protocol, Src: 217.17.45.147 (217.17.45.147), Dst: 141.53.200.101 (141.53.200.101)
Transmission Control Protocol, Src Port: https (443), Dst Port: 1050 (1050), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    201 47.097755   Enterasy_17:df:22     01:80:c2:00:00:20     GMRP     GMRP

Frame 201 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP Multicast Registration Protocol

No.     Time        Source                Destination           Protocol Info
    202 47.251475   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 202 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    203 47.251505   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 203 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    204 47.261388   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 204 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    205 47.261441   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 205 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    206 47.286270   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 206 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    207 47.286514   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 207 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    208 47.287308   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49176  Destination port: hostmon

Frame 208 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49176 (49176), Dst Port: hostmon (5355)
Data (26 bytes)

0000  00 ff 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    209 47.287720   141.53.200.23         224.0.0.252           UDP      Source port: 49177  Destination port: hostmon

Frame 209 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49177 (49177), Dst Port: hostmon (5355)
Data (26 bytes)

0000  00 ff 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    210 47.386634   141.53.200.23         141.53.200.255        BROWSER  Browser Election Request

Frame 210 (233 bytes on wire, 233 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    211 47.386864   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49176  Destination port: hostmon

Frame 211 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49176 (49176), Dst Port: hostmon (5355)
Data (26 bytes)

0000  00 ff 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    212 47.386937   141.53.200.23         224.0.0.252           UDP      Source port: 49177  Destination port: hostmon

Frame 212 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49177 (49177), Dst Port: hostmon (5355)
Data (26 bytes)

0000  00 ff 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 01 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    213 47.590058   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49178  Destination port: hostmon

Frame 213 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49178 (49178), Dst Port: hostmon (5355)
Data (26 bytes)

0000  87 e1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    214 47.590614   141.53.200.23         224.0.0.252           UDP      Source port: 49179  Destination port: hostmon

Frame 214 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49179 (49179), Dst Port: hostmon (5355)
Data (26 bytes)

0000  87 e1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    215 47.698721   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49178  Destination port: hostmon

Frame 215 (88 bytes on wire, 88 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49178 (49178), Dst Port: hostmon (5355)
Data (26 bytes)

0000  87 e1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    216 47.699151   141.53.200.23         224.0.0.252           UDP      Source port: 49179  Destination port: hostmon

Frame 216 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49179 (49179), Dst Port: hostmon (5355)
Data (26 bytes)

0000  87 e1 00 00 00 01 00 00 00 00 00 00 08 6b 61 74   .............kat
0010  6a 61 2d 50 43 00 00 1c 00 01                     ja-PC.....

No.     Time        Source                Destination           Protocol Info
    217 47.776196   141.53.200.23         224.0.0.22            IGMP     V3 Membership Report

Frame 217 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:16 (01:00:5e:00:00:16)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.22 (224.0.0.22)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
    218 47.776249   fe80::9deb:d381:c752:cc8d ff02::16              ICMPv6   Multicast Listener Report Message v2

Frame 218 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:16 (33:33:00:00:00:16)
Internet Protocol Version 6
Internet Control Message Protocol v6

No.     Time        Source                Destination           Protocol Info
    219 47.824020   141.53.200.35         141.53.200.255        BROWSER  Browser Election Request

Frame 219 (232 bytes on wire, 232 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    220 48.007828   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 220 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    221 48.400541   141.53.200.23         141.53.200.255        BROWSER  Browser Election Request

Frame 221 (233 bytes on wire, 233 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    222 48.460531   UniwillC_20:2e:11     Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.181

Frame 222 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: UniwillC_20:2e:11 (00:03:0d:20:2e:11), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    223 48.638965   141.53.200.35         141.53.200.255        BROWSER  Browser Election Request

Frame 223 (232 bytes on wire, 232 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    224 49.416011   141.53.200.23         141.53.200.255        BROWSER  Browser Election Request

Frame 224 (233 bytes on wire, 233 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    225 49.419189   217.17.45.147         141.53.200.101        TCP      https > 1050 [FIN, ACK] Seq=0 Ack=0 Win=5840 Len=0

Frame 225 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Clevo_18:1b:32 (00:90:f5:18:1b:32)
Internet Protocol, Src: 217.17.45.147 (217.17.45.147), Dst: 141.53.200.101 (141.53.200.101)
Transmission Control Protocol, Src Port: https (443), Dst Port: 1050 (1050), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    226 49.602852   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49181  Destination port: hostmon

Frame 226 (86 bytes on wire, 86 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49181 (49181), Dst Port: hostmon (5355)
Data (24 bytes)

0000  60 e2 00 00 00 01 00 00 00 00 00 00 06 69 73 61   `............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    227 49.603279   141.53.200.23         224.0.0.252           UDP      Source port: 49182  Destination port: hostmon

Frame 227 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49182 (49182), Dst Port: hostmon (5355)
Data (24 bytes)

0000  60 e2 00 00 00 01 00 00 00 00 00 00 06 69 73 61   `............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    228 49.710725   fe80::9deb:d381:c752:cc8d ff02::1:3             UDP      Source port: 49181  Destination port: hostmon

Frame 228 (86 bytes on wire, 86 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49181 (49181), Dst Port: hostmon (5355)
Data (24 bytes)

0000  60 e2 00 00 00 01 00 00 00 00 00 00 06 69 73 61   `............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    229 49.710750   141.53.200.23         224.0.0.252           UDP      Source port: 49182  Destination port: hostmon

Frame 229 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 49182 (49182), Dst Port: hostmon (5355)
Data (24 bytes)

0000  60 e2 00 00 00 01 00 00 00 00 00 00 06 69 73 61   `............isa
0010  74 61 70 00 00 01 00 01                           tap.....

No.     Time        Source                Destination           Protocol Info
    230 49.784079   141.53.200.35         141.53.200.255        BROWSER  Browser Election Request

Frame 230 (232 bytes on wire, 232 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    231 49.914816   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 231 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    232 50.013351   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 232 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    233 50.428661   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 233 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    234 50.663412   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 234 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    235 50.784252   141.53.200.35         141.53.200.255        BROWSER  Browser Election Request

Frame 235 (232 bytes on wire, 232 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    236 51.178398   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 236 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    237 51.413433   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 237 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    238 51.784243   141.53.200.35         141.53.200.255        BROWSER  Browser Election Request

Frame 238 (232 bytes on wire, 232 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    239 51.890589   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 239 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    240 51.928480   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 240 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    241 52.006914   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 241 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    242 52.186941   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 242 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    243 52.678422   141.53.200.23         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 243 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    244 52.784325   141.53.200.35         141.53.200.255        BROWSER  Browser Election Request

Frame 244 (232 bytes on wire, 232 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    245 52.936407   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 245 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    246 53.091466   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 246 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    247 53.428750   141.53.200.23         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 247 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    248 53.686431   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 248 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    249 53.785475   141.53.200.35         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 249 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    250 54.008387   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 250 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    251 54.177085   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 251 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    252 54.178474   141.53.200.23         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 252 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    253 54.534254   141.53.200.35         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 253 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    254 54.647366   85.75.122.103         141.53.200.101        TCP      34281 > 1255 [FIN, ACK] Seq=90 Ack=0 Win=65349 Len=0

Frame 254 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Cisco_88:00:00 (00:b0:4a:88:00:00), Dst: Clevo_18:1b:32 (00:90:f5:18:1b:32)
Internet Protocol, Src: 85.75.122.103 (85.75.122.103), Dst: 141.53.200.101 (141.53.200.101)
Transmission Control Protocol, Src Port: 34281 (34281), Dst Port: 1255 (1255), Seq: 90, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    255 54.928583   141.53.200.23         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 255 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    256 55.284310   141.53.200.35         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 256 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    257 55.305386   141.53.200.28         141.53.200.255        BROWSER  Get Backup List Request

Frame 257 (216 bytes on wire, 216 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    258 55.309176   141.53.200.28         141.53.200.255        NBNS     Name query NB WORKGROUP<1b>

Frame 258 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    259 55.415486   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 259 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    260 55.678515   141.53.200.23         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 260 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    261 56.012661   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 261 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    262 56.034314   141.53.200.35         141.53.200.255        NBNS     Registration NB WORKGROUP<1d>

Frame 262 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    263 56.064977   141.53.200.28         141.53.200.255        NBNS     Name query NB WORKGROUP<1b>

Frame 263 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    264 56.165503   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 264 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    265 56.429111   141.53.200.23         141.53.200.255        BROWSER  Request Announcement KATJA-PC

Frame 265 (221 bytes on wire, 221 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    266 56.429304   141.53.200.23         141.53.200.255        BROWSER  Request Announcement KATJA-PC

Frame 266 (221 bytes on wire, 221 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    267 56.430090   141.53.200.23         141.53.200.255        BROWSER  Domain/Workgroup Announcement WORKGROUP, NT Workstation, Domain Enum

Frame 267 (251 bytes on wire, 251 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    268 56.784676   141.53.200.35         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 268 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    269 56.810873   141.53.200.28         141.53.200.255        NBNS     Name query NB WORKGROUP<1b>

Frame 269 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    270 56.915598   141.53.200.23         141.53.200.255        NBNS     Name query NB ISATAP<00>

Frame 270 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    271 56.932044   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 271 (175 bytes on wire, 175 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    272 56.956273   Siemens_07:33:31      Broadcast             ARP      Who has 141.53.200.23?  Tell 141.53.200.41

Frame 272 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Siemens_07:33:31 (00:01:e3:07:33:31), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    273 57.246612   fe80::9deb:d381:c752:cc8d ff02::c               SSDP     M-SEARCH * HTTP/1.1

Frame 273 (192 bytes on wire, 192 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49186 (49186), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    274 57.247154   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 274 (178 bytes on wire, 178 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    275 57.260164   fe80::9deb:d381:c752:cc8d ff02::c               SSDP     M-SEARCH * HTTP/1.1

Frame 275 (179 bytes on wire, 179 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49186 (49186), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    276 57.260386   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 276 (165 bytes on wire, 165 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    277 57.534493   141.53.200.35         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 277 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    278 57.647452   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 278 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
    279 57.698213   Enterasy_17:df:22     01:80:c2:00:00:21     GVRP     GVRP

Frame 279 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP VLAN Registration Protocol

No.     Time        Source                Destination           Protocol Info
    280 57.835398   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 280 (175 bytes on wire, 175 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    281 58.007577   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 281 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    282 58.284565   141.53.200.35         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 282 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    283 59.034561   141.53.200.35         141.53.200.255        NBNS     Registration NB <01><02>__MSBROWSE__<02><01>

Frame 283 (110 bytes on wire, 110 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    284 59.787371   141.53.200.35         141.53.200.255        BROWSER  Domain/Workgroup Announcement WORKGROUP, NT Workstation, Domain Enum

Frame 284 (250 bytes on wire, 250 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    285 59.932328   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 285 (175 bytes on wire, 175 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    286 60.007812   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 286 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    287 60.248474   fe80::9deb:d381:c752:cc8d ff02::c               SSDP     M-SEARCH * HTTP/1.1

Frame 287 (192 bytes on wire, 192 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49186 (49186), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    288 60.248743   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 288 (178 bytes on wire, 178 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    289 60.260468   fe80::9deb:d381:c752:cc8d ff02::c               SSDP     M-SEARCH * HTTP/1.1

Frame 289 (179 bytes on wire, 179 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49186 (49186), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    290 60.260741   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 290 (165 bytes on wire, 165 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    291 60.287621   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 291 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    292 60.341885   141.53.200.28         141.53.200.255        BROWSER  Get Backup List Request

Frame 292 (216 bytes on wire, 216 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
    293 60.344133   141.53.200.35         141.53.200.255        NBNS     Name query NB ROJ<00>

Frame 293 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    294 60.344332   141.53.200.28         141.53.200.255        NBNS     Name query NB WORKGROUP<1b>

Frame 294 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    295 60.834892   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 295 (175 bytes on wire, 175 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    296 61.008909   Cisco_5e:f1:a4        CDP/VTP/DTP/PAgP/UDLD CDP      Device ID: c3548-thael-2.netwrk.med.uni-greifswald.  Port ID: FastEthernet0/36  

Frame 296 (430 bytes on wire, 430 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Cisco Discovery Protocol

No.     Time        Source                Destination           Protocol Info
    297 61.093687   141.53.200.35         141.53.200.255        NBNS     Name query NB ROJ<00>

Frame 297 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    298 61.115866   141.53.200.28         141.53.200.255        NBNS     Name query NB WORKGROUP<1b>

Frame 298 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    299 61.426656   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 299 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    300 61.447528   Enterasy_17:df:22     01:80:c2:00:00:20     GMRP     GMRP

Frame 300 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
GARP Multicast Registration Protocol

No.     Time        Source                Destination           Protocol Info
    301 61.843850   141.53.200.35         141.53.200.255        NBNS     Name query NB ROJ<00>

Frame 301 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    302 61.846429   141.53.200.28         141.53.200.255        NBNS     Name query NB WORKGROUP<1b>

Frame 302 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: Toshiba_e9:e1:d9 (00:00:39:e9:e1:d9), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.28 (141.53.200.28), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    303 62.009889   Cisco_5e:f1:a4        Spanning-tree-(for-bridges)_00 STP      Conf. Root = 32768/00:06:d7:5e:a7:c0  Cost = 4  Port = 0x8034

Frame 303 (60 bytes on wire, 60 bytes captured)
IEEE 802.3 Ethernet 
Logical-Link Control
Spanning Tree Protocol

No.     Time        Source                Destination           Protocol Info
    304 62.096870   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 304 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    305 62.551923   Wistron_4e:3f:36      Broadcast             ARP      Who has 141.53.200.1?  Tell 141.53.200.77

Frame 305 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Wistron_4e:3f:36 (00:16:d3:4e:3f:36), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    306 62.604246   141.53.200.35         224.0.0.252           UDP      Source port: 51180  Destination port: hostmon

Frame 306 (63 bytes on wire, 63 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 51180 (51180), Dst Port: hostmon (5355)
Data (21 bytes)

0000  94 06 00 00 00 01 00 00 00 00 00 00 03 52 4f 4a   .............ROJ
0010  00 00 01 00 01                                    .....

No.     Time        Source                Destination           Protocol Info
    307 62.703989   141.53.200.35         224.0.0.252           UDP      Source port: 51180  Destination port: hostmon

Frame 307 (63 bytes on wire, 63 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: 01:00:5e:00:00:fc (01:00:5e:00:00:fc)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 224.0.0.252 (224.0.0.252)
User Datagram Protocol, Src Port: 51180 (51180), Dst Port: hostmon (5355)
Data (21 bytes)

0000  94 06 00 00 00 01 00 00 00 00 00 00 03 52 4f 4a   .............ROJ
0010  00 00 01 00 01                                    .....

No.     Time        Source                Destination           Protocol Info
    308 62.904866   141.53.200.35         141.53.200.255        NBNS     Name query NB ROJ<00>

Frame 308 (92 bytes on wire, 92 bytes captured)
Ethernet II, Src: UniwillC_6d:ef:df (00:03:0d:6d:ef:df), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 141.53.200.35 (141.53.200.35), Dst: 141.53.200.255 (141.53.200.255)
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
NetBIOS Name Service

No.     Time        Source                Destination           Protocol Info
    309 62.938540   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 309 (175 bytes on wire, 175 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    310 63.250361   fe80::9deb:d381:c752:cc8d ff02::c               SSDP     M-SEARCH * HTTP/1.1

Frame 310 (192 bytes on wire, 192 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: IPv6-Neighbor-Discovery_00:00:00:0c (33:33:00:00:00:0c)
Internet Protocol Version 6
User Datagram Protocol, Src Port: 49186 (49186), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    311 63.250769   141.53.200.23         239.255.255.250       SSDP     M-SEARCH * HTTP/1.1

Frame 311 (178 bytes on wire, 178 bytes captured)
Ethernet II, Src: CompalEl_a9:a0:8b (00:1b:38:a9:a0:8b), Dst: 01:00:5e:7f:ff:fa (01:00:5e:7f:ff:fa)
Internet Protocol, Src: 141.53.200.23 (141.53.200.23), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 49189 (49189), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

dmesg:

00000 00000000 00000000 00000000
[    5.443321] CPU: L1 I cache: 16K, L1 D cache: 16K
[    5.443326] CPU: L2 cache: 512K
[    5.443331] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[    5.443348] Compat vDSO mapped to ffffe000.
[    5.443367] Checking 'hlt' instruction... OK.
[    5.459104] SMP alternatives: switching to UP code
[    5.459314] Freeing SMP alternatives: 11k freed
[    5.459717] Early unpacking initramfs... done
[    6.003797] ACPI: Core revision 20070126
[    6.004047] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    6.011112] ACPI: setting ELCR to 0200 (from 0800)
[    6.031781] CPU0: Intel(R) Pentium(R) III Mobile CPU      1133MHz stepping 01
[    6.031792] SMP motherboard not detected.
[    6.031797] Local APIC not detected. Using dummy APIC emulation.
[    6.031875] Brought up 1 CPUs
[    6.032114] Booting paravirtualized kernel on bare hardware
[    6.032205] Time: 17:27:53  Date: 01/14/108
[    6.032258] NET: Registered protocol family 16
[    6.032451] EISA bus registered
[    6.032469] ACPI: bus type pci registered
[    6.032775] PCI: PCI BIOS revision 2.10 entry at 0xfd8fe, last bus=8
[    6.032780] PCI: Using configuration type 1
[    6.032783] Setting up standard PCI resources
[    6.037603] ACPI: EC: Found ECDT
[    6.048641] ACPI: Interpreter enabled
[    6.048649] ACPI: (supports S0 S3 S4 S5)
[    6.048678] ACPI: Using PIC for interrupt routing
[    6.060060] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    6.060159] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    6.060170] PCI: Probing PCI hardware (bus 00)
[    6.060507] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    6.060514] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    6.060910] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    6.060969] PCI: Transparent bridge - 0000:00:1e.0
[    6.061124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    6.061220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    6.061258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    6.066431] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    6.066754] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    6.067136] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    6.067456] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    6.067777] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    6.068070] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    6.068364] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    6.068657] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    6.069120] ACPI: Power Resource [PUBS] (on)
[    6.069140] Linux Plug and Play Support v0.97 (c) Adam Belay
[    6.069160] pnp: PnP ACPI init
[    6.069178] ACPI: bus type pnp registered
[    6.074699] pnp: PnP ACPI: found 13 devices
[    6.074703] ACPI: ACPI bus type pnp unregistered
[    6.074710] PnPBIOS: Disabled by ACPI PNP
[    6.074810] PCI: Using ACPI for IRQ routing
[    6.074834] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    6.082494] NET: Registered protocol family 8
[    6.082499] NET: Registered protocol family 20
[    6.082629] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    6.082636] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    6.082641] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    6.082647] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    6.082817] Time: tsc clocksource has been installed.
[    6.113205] PCI: Bridge: 0000:00:01.0
[    6.113209]   IO window: disabled.
[    6.113215]   MEM window: c0100000-c01fffff
[    6.113220]   PREFETCH window: e0000000-ebffffff
[    6.113231] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    6.113236]   IO window: 00002000-000020ff
[    6.113241]   IO window: 00002400-000024ff
[    6.113247]   PREFETCH window: f0000000-f3ffffff
[    6.113253]   MEM window: c4000000-c7ffffff
[    6.113259] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[    6.113262]   IO window: 00002800-000028ff
[    6.113268]   IO window: 00002c00-00002cff
[    6.113274]   PREFETCH window: f4000000-f7ffffff
[    6.113280]   MEM window: c8000000-cbffffff
[    6.113285] PCI: Bridge: 0000:00:1e.0
[    6.113289]   IO window: 2000-6fff
[    6.113296]   MEM window: c0200000-cfffffff
[    6.113302]   PREFETCH window: f0000000-f7ffffff
[    6.113320] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    6.113945] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    6.113951] PCI: setting IRQ 11 as level-triggered
[    6.113956] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    6.114511] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    6.114516] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    6.114545] NET: Registered protocol family 2
[    6.150864] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    6.150950] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[    6.151154] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    6.151302] TCP: Hash tables configured (established 8192 bind 8192)
[    6.151308] TCP reno registered
[    6.163038] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[    6.633912]  it is
[    7.197129] Freeing initrd memory: 7036k freed
[    7.197420] Simple Boot Flag at 0x35 set to 0x1
[    7.197843] audit: initializing netlink socket (disabled)
[    7.197871] audit(1203010074.708:1): initialized
[    7.201910] VFS: Disk quotas dquot_6.5.1
[    7.202028] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.202225] io scheduler noop registered
[    7.202230] io scheduler anticipatory registered
[    7.202234] io scheduler deadline registered
[    7.202270] io scheduler cfq registered (default)
[    7.202344] Boot video device is 0000:01:00.0
[    7.202692] isapnp: Scanning for PnP cards...
[    7.555602] isapnp: No Plug & Play device found
[    7.607657] Real Time Clock Driver v1.12ac
[    7.607836] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    7.609632] pnp: Device 00:0a activated.
[    7.609895] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    7.611337] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    7.611698] input: Macintosh mouse button emulation as /class/input/input0
[    7.611852] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    7.619711] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.619723] serio: i8042 AUX port at 0x60,0x64 irq 12
[    7.620025] mice: PS/2 mouse device common for all mice
[    7.620214] EISA: Probing bus 0 at eisa.0
[    7.620226] Cannot allocate resource for EISA slot 1
[    7.620232] Cannot allocate resource for EISA slot 2
[    7.620237] Cannot allocate resource for EISA slot 3
[    7.620241] Cannot allocate resource for EISA slot 4
[    7.620245] Cannot allocate resource for EISA slot 5
[    7.620249] Cannot allocate resource for EISA slot 6
[    7.620259] EISA: Detected 0 cards.
[    7.620439] TCP cubic registered
[    7.620475] NET: Registered protocol family 1
[    7.620529] Using IPI No-Shortcut mode
[    7.620837]   Magic number: 12:754:491
[    7.621485] Freeing unused kernel memory: 364k freed
[    7.654407] input: AT Translated Set 2 keyboard as /class/input/input1
[    8.938725] AppArmor: AppArmor initialized<5>audit(1203010076.208:2):  type=1505 info="AppArmor initialized" pid=1189
[    8.954542] fuse init (API version 7.8)
[    8.962882] Failure registering capabilities with primary security module.
[    8.986667] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    8.989754] ACPI: Thermal Zone [THM0] (56 C)
[    9.803693] usbcore: registered new interface driver usbfs
[    9.803738] usbcore: registered new interface driver hub
[    9.803778] usbcore: registered new device driver usb
[    9.806227] USB Universal Host Controller Interface driver v3.0
[    9.806354] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    9.806373] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    9.806379] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    9.806628] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    9.806660] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    9.806878] usb usb1: configuration #1 chosen from 1 choice
[    9.806926] hub 1-0:1.0: USB hub found
[    9.806937] hub 1-0:1.0: 2 ports detected
[    9.911507] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    9.911518] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.911537] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    9.911544] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    9.911599] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    9.911633] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    9.911845] usb usb2: configuration #1 chosen from 1 choice
[    9.911898] hub 2-0:1.0: USB hub found
[    9.911911] hub 2-0:1.0: 2 ports detected
[    9.965298] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[    9.965305] e100: Copyright(c) 1999-2006 Intel Corporation
[   10.014494] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.014504] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.014524] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.014530] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.014575] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   10.014608] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[   10.014798] usb usb3: configuration #1 chosen from 1 choice
[   10.014848] hub 3-0:1.0: USB hub found
[   10.014862] hub 3-0:1.0: 2 ports detected
[   10.061373] SCSI subsystem initialized
[   10.078061] libata version 2.21 loaded.
[   10.119428] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   10.119438] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   10.143130] e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:D0:59:A9:3C:33
[   10.206258] ata_piix 0000:00:1f.1: version 2.11
[   10.206286] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   10.206302] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.206364] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.206619] scsi0 : ata_piix
[   10.206711] scsi1 : ata_piix
[   10.207473] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[   10.207480] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[   10.253447] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   10.271155] Floppy drive(s): fd0 is 1.44M
[   10.351043] FDC 0 is a National Semiconductor PC87306
[   10.369731] ata1.00: ATA-6: TOSHIBA MK4025GAS, KA100A, max UDMA/100
[   10.369740] ata1.00: 78140160 sectors, multi 16: LBA 
[   10.377758] ata1.00: configured for UDMA/100
[   10.420740] usb 2-2: configuration #1 chosen from 1 choice
[   10.474905] usbcore: registered new interface driver hiddev
[    5.116000] Marking TSC unstable due to: possible TSC halt in C2.
[    5.116000] input: PS/2+USB Mouse as /class/input/input2
[    5.116000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-2
[    5.116000] usbcore: registered new interface driver usbhid
[    5.116000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.120000] Time: acpi_pm clocksource has been installed.
[    5.236000] Clocksource tsc unstable (delta = -98298077 ns)
[    5.496000] ata2.00: ATAPI: HITACHI DVD-ROM GD-S200, 0034, max UDMA/33
[    5.684000] ata2.00: configured for UDMA/33
[    5.684000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4025GA KA10 PQ: 0 ANSI: 5
[    5.688000] scsi 1:0:0:0: CD-ROM            HITACHI  DVD-ROM GD-S200  0034 PQ: 0 ANSI: 5
[    5.720000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.720000] sd 0:0:0:0: [sda] Write Protect is off
[    5.720000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.720000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.720000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.720000] sd 0:0:0:0: [sda] Write Protect is off
[    5.720000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.720000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.720000]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    5.828000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.840000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.840000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.872000] sr0: scsi3-mmc drive: 10x/24x cd/rw xa/form2 cdda tray
[    5.872000] Uniform CD-ROM driver Revision: 3.20
[    5.872000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.204000] Attempting manual resume
[    6.204000] swsusp: Resume From Partition 8:5
[    6.204000] PM: Checking swsusp image.
[    6.204000] PM: Resume from disk failed.
[    6.264000] kjournald starting.  Commit interval 5 seconds
[    6.264000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.260000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.264000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.496000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.532000] agpgart: Detected an Intel 830M Chipset.
[   14.548000] agpgart: AGP aperture is 256M @ 0xd0000000
[   14.976000] iTCO_vendor_support: vendor-support=0
[   14.980000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.980000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[   14.980000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.016000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:023b]
[   15.016000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   15.016000] Yenta: Routing CardBus interrupts to PCI
[   15.016000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21022, devctl 0x64
[   15.248000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   15.248000] Socket status: 30000006
[   15.248000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[   15.248000] cs: IO port probe 0x2000-0x6fff: clean.
[   15.248000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   15.248000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   15.248000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:023b]
[   15.248000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   15.248000] Yenta: Routing CardBus interrupts to PCI
[   15.248000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21022, devctl 0x64
[   15.260000] Intel 82802 RNG detected
[   15.480000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   15.480000] Socket status: 30000006
[   15.480000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[   15.480000] cs: IO port probe 0x2000-0x6fff: clean.
[   15.480000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   15.480000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   16.720000] input: PC Speaker as /class/input/input3
[   16.912000] parport_pc 00:0b: reported by Plug and Play ACPI
[   16.912000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   17.068000] irda_init()
[   17.068000] NET: Registered protocol family 23
[   17.316000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.332000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   17.344000] pnp: Device 00:0c activated.
[   17.344000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   17.344000] nsc-ircc, chip->init
[   17.344000] nsc-ircc, Found chip at base=0x02e
[   17.344000] nsc-ircc, driver loaded (Dag Brattli)
[   17.344000] IrDA: Registered device irda0
[   17.344000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   17.480000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   17.480000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.480000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   17.528000] cs: IO port probe 0x100-0x3af: clean.
[   17.528000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.528000] cs: IO port probe 0x820-0x8ff: clean.
[   17.528000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.528000] cs: IO port probe 0xa00-0xaff: clean.
[   17.536000] cs: IO port probe 0x100-0x3af: clean.
[   17.540000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.540000] cs: IO port probe 0x820-0x8ff: clean.
[   17.540000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.540000] cs: IO port probe 0xa00-0xaff: clean.
[   18.256000] intel8x0_measure_ac97_clock: measured 55686 usecs
[   18.256000] intel8x0: clocking to 48000
[   18.892000] loop: module loaded
[   18.936000] lp0: using parport0 (interrupt-driven).
[   19.040000] Adding 1020116k swap on /dev/sda5.  Priority:-1 extents:1 across:1020116k
[   19.400000] EXT3 FS on sda1, internal journal
[   21.328000] kjournald starting.  Commit interval 5 seconds
[   21.332000] EXT3 FS on sda6, internal journal
[   21.332000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.372000] kjournald starting.  Commit interval 5 seconds
[   21.372000] EXT3 FS on sda7, internal journal
[   21.372000] EXT3-fs: mounted filesystem with ordered data mode.
[   22.756000] ACPI: ACPI Dock Station Driver 
[   22.792000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.896000] input: Power Button (FF) as /class/input/input5
[   22.900000] ACPI: Power Button (FF) [PWRF]
[   22.960000] input: Lid Switch as /class/input/input6
[   22.960000] ACPI: Lid Switch [LID]
[   22.988000] input: Sleep Button (CM) as /class/input/input7
[   22.988000] ACPI: Sleep Button (CM) [SLPB]
[   23.096000] ACPI: Battery Slot [BAT0] (battery present)
[   23.240000] ACPI: AC Adapter [AC] (on-line)
[   23.272000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   23.272000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   23.272000] ACPI: Error installing bay notify handler
[   23.272000] ACPI: Bay [\_SB_.PCI0.IDE0.SCND.MSTR] Added
[   25.372000] ppdev: user-space parallel port driver
[   25.520000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[   25.708000] audit(1203010098.893:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4556 profile="/usr/sbin/cupsd"
[   25.784000] IBM machine detected. Enabling interrupts during APM calls.
[   25.784000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   25.784000] apm: overridden by ACPI.
[   25.968000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   25.968000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   25.972000] thinkpad_acpi: another device driver is already handling bay events
[   25.972000] thinkpad_acpi: disabling subdriver bay
[   26.180000] Failure registering capabilities with primary security module.
[   29.672000] [drm] Initialized drm 1.1.0 20060810
[   29.728000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   29.732000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   29.732000] mtrr: base(0xe4000000) is not aligned on a size(0x5000000) boundary
[   29.732000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   29.736000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   29.748000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   31.112000] NET: Registered protocol family 17
[   36.812000] NET: Registered protocol family 10
[   36.812000] lo: Disabled Privacy Extensions
[   47.396000] eth0: no IPv6 routers present
[  348.368000] device eth0 entered promiscuous mode
[  348.368000] audit(1203010421.395:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  348.408000] device lo entered promiscuous mode
[  348.408000] audit(1203010421.395:5): dev=lo prom=256 old_prom=0 auid=4294967295
[  350.904000] device eth0 left promiscuous mode
[  350.904000] audit(1203010423.895:6): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  350.940000] device lo left promiscuous mode
[  350.940000] audit(1203010423.895:7): dev=lo prom=0 old_prom=256 auid=4294967295
[  351.400000] device eth0 entered promiscuous mode
[  351.400000] audit(1203010424.395:8): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  400.612000] device eth0 left promiscuous mode
[  400.612000] audit(1203010473.398:9): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  402.404000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  542.988000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  542.992000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  542.992000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  553.784000] eth0: no IPv6 routers present
[  564.024000] device eth0 entered promiscuous mode
[  564.024000] audit(1203010636.907:10): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  564.044000] device lo entered promiscuous mode
[  564.044000] audit(1203010636.907:11): dev=lo prom=256 old_prom=0 auid=4294967295
[  565.256000] device eth0 left promiscuous mode
[  565.256000] audit(1203010638.407:12): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  565.280000] device lo left promiscuous mode
[  565.280000] audit(1203010638.407:13): dev=lo prom=0 old_prom=256 auid=4294967295
[  567.468000] device eth0 entered promiscuous mode
[  567.468000] audit(1203010640.407:14): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  578.464000] device eth0 left promiscuous mode
[  578.464000] audit(1203010651.408:15): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  599.204000] device eth0 entered promiscuous mode
[  599.204000] audit(1203010672.409:16): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  599.224000] device lo entered promiscuous mode
[  599.224000] audit(1203010672.409:17): dev=lo prom=256 old_prom=0 auid=4294967295
[  600.244000] device eth0 left promiscuous mode
[  600.244000] audit(1203010673.409:18): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  600.268000] device lo left promiscuous mode
[  600.268000] audit(1203010673.409:19): dev=lo prom=0 old_prom=256 auid=4294967295
[  601.788000] device eth0 entered promiscuous mode
[  601.788000] audit(1203010674.909:20): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  665.092000] device eth0 left promiscuous mode
[  665.092000] audit(1203010737.913:21): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  665.140000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  665.144000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  665.144000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  679.716000] eth0: no IPv6 routers present
[ 1407.076000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1421.076000] e100: eth0: e100_watchdog: link down
[ 1423.076000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1423.076000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1440.916000] eth0: no IPv6 routers present
[ 1728.820000] e100: eth0: e100_watchdog: link down
[ 1730.932000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1731.044000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1742.340000] eth0: no IPv6 routers present
[ 1772.632000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1774.560000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1774.564000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1774.564000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1791.360000] eth0: no IPv6 routers present
[ 1983.284000] e100: eth0: e100_watchdog: link down
[ 1987.508000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1987.620000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1998.340000] eth0: no IPv6 routers present
[ 2026.044000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2026.048000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2026.048000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2027.752000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2027.756000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2027.756000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2043.956000] eth0: no IPv6 routers present
[ 2170.876000] e100: eth0: e100_watchdog: link down
[ 2172.988000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2173.100000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2183.840000] eth0: no IPv6 routers present
[ 2259.608000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2392.300000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2392.304000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2392.304000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2410.584000] eth0: no IPv6 routers present
[ 2527.092000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2527.096000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2527.096000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2528.432000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2528.436000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2528.436000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2546.808000] eth0: no IPv6 routers present
[ 2667.868000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2669.452000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2683.600000] eth0: no IPv6 routers present
[ 2709.744000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2709.748000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2709.748000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2711.264000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2711.268000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2711.268000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2729.228000] eth0: no IPv6 routers present
[ 2803.652000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2803.656000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2803.656000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2804.848000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2804.852000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2804.852000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2821.204000] eth0: no IPv6 routers present
[ 2872.708000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2872.712000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2872.712000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2874.252000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2874.256000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2874.256000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2889.116000] eth0: no IPv6 routers present
[ 2939.312000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2939.316000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2939.316000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2940.616000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2940.620000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 2940.620000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2955.920000] eth0: no IPv6 routers present



```

I suppose my problem goes back to this strange "ARP      Who has 141.53.200.1?  Tell 141.53.200.7" ...
This might go back to a missing link between ip route and ip rule. But I don't know how to fix that. 
The connection works fine at every other station I tested..

If you know anything I'd really appreciate your help.

---

### Post by aBitLater on 2008-02-14
hallo und guten tag eben,

I'm a total newb, but I have to ask, is your subnet mask correct for both locations?

I look at it (as a newb) and see that you have a subnet mask of all 1's (3rd octet) and that is illegal.  Will a mask of 255.255.0.0 work with your 141.53.x.x network?

Maybe you can post your /etc/network/interfaces file for others to see

---

### Post by eben on 2008-02-14
thanks for answering ... :-)

my /etc/network/interfaces :

[CODE]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


/etc/network/interfaces (END) 
[CODE]

I didn't make any changes in the config files since I installed ubuntu ... 

how do I change the netmask?

thanks

---

### Post by tcpip4lyfe on 2008-02-14
You should be configured though DHCP by your school.

To make sure it is edit /etc/network/interfaces

You should have a line that looks like this:

```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Then do this:

```
/etc/init.d/networking restart/
```

Paste this output.

---

### Post by aBitLater on 2008-02-14
eben, 

again, i'm very much a newb with networking, so someone else may answer with a correction or addition.  Hopefully this gets you started on the right path.

Maybe you need to allow roaming for that connections, since you use it at 2 places
Try System / Administration / Network / Your-connection / Properties / enable roaming

I have the following lines for my wireless card in my interfaces (please note I do not have roaming enabled, so this may not be right for you)

```
auto eth1
iface eth1 inet dhcp
address 192.168.1.2
gateway 192.168.1.1
netmask 255.255.255.0
```

notice this is eth1 not eth0.  for me, eth0 is my 'wired' connection.  for wireless, I use eth1.  some people use wlan0 for wireless (vielleicht das ist besser, ich weiss's nicht) 

The "auto eth1" makes it available at startup.  You can leave that out and start it yourself (which may be a good idea for you when at home).  use ifup eth1 from console to start it, and ifdown eth1 to stop it.

so maybe one configuration for your connection can go in interfaces as eth0 for your connection at school, then make another section for eth1 that is for the same network card when at home.  If you're using wireless, you might use wlan0 and wlan1 as interface names.  either way, you can set the mask to be different for each place.

I have no problems with hard-coding the address even though i have it configured as "iface eth1 inet dhcp", because my router is configured to give that IP to my network card, and only my machine's network card (my wife's machine never will get it).  You can replace "dhcp" with "static" if your IP never changes and is not assigned by a dhcp server.  

I don't know enough about this to tell you exactly how to configure your /etc/network/interfaces, but you can try different things - try adding only the 'netmask' and see how it works.  Also, I think  you have to 'ifdown eth1" before making changes and "ifup eth1" after making changes (again, eth1 is only an example, use ethX for whatever your set it up as, eth0, eth2, etc).
gateway is your router if you have one.  

hope that helps.  Agian, I'm a newb with networking.... :)

---

### Post by eben on 2008-02-14
ok, thanks ...

```

henrik@d34-4:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:a9:3c:33
Sending on   LPF/eth0/00:d0:59:a9:3c:33
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 141.53.200.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 141.53.200.1
bound to 141.53.200.223 -- renewal in 139734 seconds.
                                                                         [ OK ]
henrik@d34-4:~$ 

```

but it didn't seem to work ...

wireshark still says:

```

"9","36.816334","AmbitMic_a9:3c:33","Broadcast","ARP","Who has 141.53.200.1?  Tell 141.53.200.223"

```

thanks anyway

---

### Post by aBitLater on 2008-02-14
weird, the ARP packet says TELL 141.53.200.223, so you only renewed your old IP address. 

do this

```
ifdown eth0
```

add this to /etc/network/interfaces and save:
```

auto eth0
iface eth0 inet dhcp
gateway 141.253.200.1
netmask 255.255.0.0
```

then do this:

```
ifup eth0
```

if it works, this will at least confirm the bad netmask.

The TCPIP4LYFE guy probably knows what he is talking about... considering his name :)

---

### Post by eben on 2008-02-14
thanks ...

```

henrik@d34-4:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 7183
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:a9:3c:33
Sending on   LPF/eth0/00:d0:59:a9:3c:33
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 141.53.9.12 port 67
henrik@d34-4:~$ sudo mousepad /etc/network/interfaces 
henrik@d34-4:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:a9:3c:33
Sending on   LPF/eth0/00:d0:59:a9:3c:33
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 141.53.200.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 141.53.200.1
bound to 141.53.200.223 -- renewal in 159947 seconds.
henrik@d34-4:~$ 

```

doesn't seem to work. i had fast internet for a few seconds. than it broke up. wireshark shows the ARP message.

i saw  eth0: no IPv6 routers present in dmesg ... might that be my problem?

part of dmesg
```

[   29.364000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   29.368000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   29.368000] mtrr: base(0xe4000000) is not aligned on a size(0x5000000) boundary
[   29.368000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   29.368000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   29.368000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   30.024000] eth0: no IPv6 routers present
[  505.528000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  505.532000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  505.532000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  515.856000] eth0: no IPv6 routers present
[  652.432000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  652.436000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  652.436000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  662.692000] eth0: no IPv6 routers present
[  731.100000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  741.896000] eth0: no IPv6 routers present
[  850.708000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  850.712000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  850.712000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  861.220000] eth0: no IPv6 routers present
[  977.340000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  977.344000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[  977.344000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  987.856000] eth0: no IPv6 routers present
[ 1034.724000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1034.728000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1034.728000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1044.732000] eth0: no IPv6 routers present
[ 1088.844000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1088.848000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1088.848000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1099.652000] eth0: no IPv6 routers present
[ 1188.832000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1188.836000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[ 1188.836000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1199.428000] eth0: no IPv6 routers present
[ 1326.540000] device eth0 entered promiscuous mode
[ 1326.540000] audit(1203032546.605:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[ 1326.576000] device lo entered promiscuous mode
[ 1326.576000] audit(1203032546.605:5): dev=lo prom=256 old_prom=0 auid=4294967295
[ 1328.280000] device eth0 left promiscuous mode
[ 1328.280000] audit(1203032548.605:6): dev=eth0 prom=0 old_prom=256 auid=4294967295
[ 1328.308000] device lo left promiscuous mode
[ 1328.308000] audit(1203032548.605:7): dev=lo prom=0 old_prom=256 auid=4294967295
[ 1328.844000] device eth0 entered promiscuous mode
[ 1328.844000] audit(1203032549.105:8): dev=eth0 prom=256 old_prom=0 auid=4294967295
[ 1333.960000] device lo entered promiscuous mode
[ 1333.960000] audit(1203032554.105:9): dev=lo prom=256 old_prom=0 auid=4294967295
[ 1337.084000] device lo left promiscuous mode
[ 1337.084000] audit(1203032557.105:10): dev=lo prom=0 old_prom=256 auid=4294967295
[ 1371.380000] device eth0 left promiscuous mode
[ 1371.380000] audit(1203032591.607:11): dev=eth0 prom=0 old_prom=256 auid=4294967295

```

thanks for your help !!

---

### Post by aBitLater on 2008-02-14
show us 

ifconfig -a

and 
sudo cat /etc/network/interfaces

---

### Post by aBitLater on 2008-02-14
look here in this forum User CP (control panel) for your private message.  I sent contact info for your network to you via private message.  

I didn't feel comfortable posting the phone numbers and email addresses in a publicly viewable forum.

Perhaps the Network admins can help you.

---

### Post by eben on 2008-02-14
```

henrik@d34-4:~$ ifconfig -a
eth0      Protokoll:Ethernet  Hardware Adresse 00:D0:59:A9:3C:33  
          inet Adresse:141.53.200.223  Bcast:141.53.200.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:507 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:846021 (826.1 KB)  TX bytes:47173 (46.0 KB)

irda0     Protokoll:IrLAP  Hardware Adresse 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:2766 (2.7 KB)  TX bytes:2766 (2.7 KB)

henrik@d34-4:~$ 

```

```

henrik@d34-4:~$ sudo cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# auto eth0
# iface eth0 inet dhcp
# address 192.168.1.2
# gateway 192.168.1.1
# netmask 255.255.255.0
auto eth0
iface eth0 inet dhcp
gateway 141.253.200.1
netmask 255.255.0.0

# The loopback network interface
auto lo
iface lo inet loopback


henrik@d34-4:~$ 


```

IPv6 wasn't the problem. i turned it off and i still have the problems ..

---

### Post by aBitLater on 2008-02-14
I still think (til an expert says otherwise) that the mask is wrong at 255.255.255.0

I don't know why it seems to be configured properly in /etc/network/interfaces (as 255.255.0.0) but is not actually the mask you get.

it is beyond me. sorry I couldn't be of help to you.

If you find the answer, please post it so we know.

just for fun, try removing the gateway line from your interfaces file

ifdown eth0 
remove gateway line
ifup eth0

if that doesn't change anything, reboot :)

---

### Post by eben on 2008-02-14
didn't solve the problem at all ...

i found this thread [http://groups.google.com/group/linux.debian.isp/browse_thread/thread/fbd737d9a129262f]("http://groups.google.com/group/linux.debian.isp/browse_thread/thread/fbd737d9a129262f")

he seems to have a similar problem

but I don't understand his solution to the problem at all. maybe anyone can help?

thanks

---

### Post by tcpip4lyfe on 2008-02-15
The netmask can pretty much be anything they want it to be.  Depends on how they segment the network.  A netmask of 255.255.255.0 means that you can have up to 253 hosts per network. What is that irda interface? Try downing that for troubleshooting purposes.   As far as the ip setting go anything you get from dhcp should be right so it probably a problem with a setting your box.  Have you added or removed any static routes? Route should only have 2 lines in it.  

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *                  255.255.0.0     U     0      0        0    eth0
default         10.0.0.1        0.0.0.0             UG    100    0        0 eth0 
```


Swap network cables and try that.  When that doesn't work (do it anyway just in case :) ) boot to a live CD and see if you have internet on that. If you do, try and find out what is different and write it down so you can change it.  If it doesn't, I suspect the NIC or NIC drivers.  Try swapping that out.  Let us know what you find out.

edit: I dont understand the google solution either. Dont feel bad.

---

### Post by aBitLater on 2008-02-15
> **tcpip4lyfe said:**
> The netmask can pretty much be anything they want it to be.  Depends on how they segment the network.  A netmask of 255.255.255.0 means that you can have up to 253 hosts per network.

I did a net lookup of his gateway and got a report back for his network that shows the networks as 

141.53.0.0

so that's what makes me think he needs a mask of 255.255.0.0.  But apparently he's not getting that as his ifconfig -a shows.

---

