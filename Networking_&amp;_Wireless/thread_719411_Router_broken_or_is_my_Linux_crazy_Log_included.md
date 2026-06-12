---
title: "Router broken or is my Linux crazy? Log included"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by kung fu buntu on 2008-03-09
I bought a router but it stops working after a couple of hours, sometimes a couple of minutes. The store told me they tested and it works fine -_-'
 The problem is that I only started using the router 4 months after I had bougth it so I can't have my money back  (without a strong argument)  :(
 
 Today when I wake up I noticed I had no network again, so I remembered to pop up wireshark and try to see what's wrong. The scenario is the following, I had no network, can't access the router web interface, can't even ping it. If I reboot the router things start working again.
 It's an SMCWBR14-G2.
 
 Thank you for any insights on this issue.
 The log starts with an web request and then I try to ping it.



```
No.     Time        Source                Destination           Protocol Info
      1 0.000000    192.168.2.100         192.168.2.1           TCP      51160 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=148678558 TSER=0 WS=7

Frame 1 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Transmission Control Protocol, Src Port: 51160 (51160), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
      2 2.328399    192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 2 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
      3 3.000556    192.168.2.100         192.168.2.1           TCP      51160 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=148679308 TSER=0 WS=7

Frame 3 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Transmission Control Protocol, Src Port: 51160 (51160), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
      4 5.000640    AsustekC_ba:f5:a8     SmcNetwo_74:f6:02     ARP      Who has 192.168.2.1?  Tell 192.168.2.100

Frame 4 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
      5 5.000897    SmcNetwo_74:f6:02     AsustekC_ba:f5:a8     ARP      192.168.2.1 is at __:__:__:74:f6:02

Frame 5 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
      6 9.000843    192.168.2.100         192.168.2.1           TCP      51160 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=148680808 TSER=0 WS=7

Frame 6 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Transmission Control Protocol, Src Port: 51160 (51160), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
      7 9.529458    192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 7 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
      8 11.404960   192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 8 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
      9 21.001360   192.168.2.100         192.168.2.1           TCP      51160 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=148683808 TSER=0 WS=7

Frame 9 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Transmission Control Protocol, Src Port: 51160 (51160), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     10 45.002512   192.168.2.100         192.168.2.1           TCP      51160 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=148689808 TSER=0 WS=7

Frame 10 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Transmission Control Protocol, Src Port: 51160 (51160), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     11 50.002740   AsustekC_ba:f5:a8     SmcNetwo_74:f6:02     ARP      Who has 192.168.2.1?  Tell 192.168.2.100

Frame 11 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     12 50.002997   SmcNetwo_74:f6:02     AsustekC_ba:f5:a8     ARP      192.168.2.1 is at __:__:__:74:f6:02

Frame 12 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     13 93.004816   192.168.2.100         192.168.2.1           TCP      51160 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=148701808 TSER=0 WS=7

Frame 13 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Transmission Control Protocol, Src Port: 51160 (51160), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     14 98.007970   AsustekC_ba:f5:a8     SmcNetwo_74:f6:02     ARP      Who has 192.168.2.1?  Tell 192.168.2.100

Frame 14 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     15 98.008228   SmcNetwo_74:f6:02     AsustekC_ba:f5:a8     ARP      192.168.2.1 is at __:__:__:74:f6:02

Frame 15 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     16 119.786527  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 16 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     17 120.889078  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 17 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     18 124.107148  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 18 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     19 244.925816  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 19 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     20 246.982463  192.168.2.100         192.168.2.1           DHCP     DHCP Request  - Transaction ID 0xd5fd845e

Frame 20 (342 bytes on wire, 342 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
User Datagram Protocol, Src Port: bootpc (68), Dst Port: bootps (67)
Bootstrap Protocol

No.     Time        Source                Destination           Protocol Info
     21 249.166798  192.168.2.1           255.255.255.255       DHCP     DHCP ACK      - Transaction ID 0xd5fd845e

Frame 21 (342 bytes on wire, 342 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 255.255.255.255 (255.255.255.255)
User Datagram Protocol, Src Port: bootps (67), Dst Port: bootpc (68)
Bootstrap Protocol

No.     Time        Source                Destination           Protocol Info
     22 251.982611  AsustekC_ba:f5:a8     SmcNetwo_74:f6:02     ARP      Who has 192.168.2.1?  Tell 192.168.2.100

Frame 22 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     23 251.982861  SmcNetwo_74:f6:02     AsustekC_ba:f5:a8     ARP      192.168.2.1 is at __:__:__:74:f6:02

Frame 23 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     24 252.927016  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 24 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     25 254.366737  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 25 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     26 370.065156  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 26 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     27 370.705189  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 27 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     28 372.416887  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 28 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     29 495.204493  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 29 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     30 498.626946  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 30 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     31 503.525725  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 31 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     32 504.635362  192.168.2.100         192.168.2.255         BROWSER  Local Master Announcement STARDUST, Workstation, Server, Print Queue Server, Xenix Server, NT Workstation, NT Server, Master Browser, Unknown server type:23

Frame 32 (258 bytes on wire, 258 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.255 (192.168.2.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
     33 504.635383  192.168.2.100         192.168.2.255         BROWSER  Domain/Workgroup Announcement STARDUST, NT Workstation, Domain Enum

Frame 33 (251 bytes on wire, 251 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.255 (192.168.2.255)
User Datagram Protocol, Src Port: netbios-dgm (138), Dst Port: netbios-dgm (138)
NetBIOS Datagram Service
SMB (Server Message Block Protocol)
SMB MailSlot Protocol
Microsoft Windows Browser Protocol

No.     Time        Source                Destination           Protocol Info
     34 620.343827  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 34 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     35 623.224237  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 35 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     36 624.062963  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 36 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     37 745.483259  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 37 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     38 747.060858  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 38 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     39 754.444471  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 39 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     40 770.853989  AsustekC_ba:f5:a8     Broadcast             ARP      Who has 192.168.2.1?  Tell 192.168.2.100

Frame 40 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     41 770.854239  SmcNetwo_74:f6:02     AsustekC_ba:f5:a8     ARP      192.168.2.1 is at __:__:__:74:f6:02

Frame 41 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     42 770.854248  192.168.2.100         192.168.2.1           DNS      Standard query AAAA stardust

Frame 42 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
User Datagram Protocol, Src Port: 34035 (34035), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     43 775.850250  192.168.2.100         192.168.2.1           DNS      Standard query AAAA stardust

Frame 43 (68 bytes on wire, 68 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
User Datagram Protocol, Src Port: 34035 (34035), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     44 870.622422  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 44 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     45 872.962894  192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 45 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     46 877.023368  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 46 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     47 995.761817  192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 47 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     48 996.881936  192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 48 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     49 1000.196960 192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 49 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     50 1120.901269 192.168.2.1           224.0.0.1             IGMP     V2 Membership Query

Frame 50 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:01 (__:__:__:00:00:01)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.1 (224.0.0.1)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     51 1121.062768 192.168.2.100         224.0.0.251           IGMP     V2 Membership Report

Frame 51 (46 bytes on wire, 46 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: UscInfor_00:00:fb (__:__:__:00:00:fb)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 224.0.0.251 (224.0.0.251)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     52 1126.501968 192.168.2.1           224.0.0.9             IGMP     V2 Membership Report

Frame 52 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: UscInfor_00:00:09 (__:__:__:00:00:09)
Internet Protocol, Src: 192.168.2.1 (192.168.2.1), Dst: 224.0.0.9 (224.0.0.9)
Internet Group Management Protocol

No.     Time        Source                Destination           Protocol Info
     53 1143.931841 AsustekC_ba:f5:a8     Broadcast             ARP      Who has 192.168.2.1?  Tell 192.168.2.100

Frame 53 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     54 1143.932095 SmcNetwo_74:f6:02     AsustekC_ba:f5:a8     ARP      192.168.2.1 is at __:__:__:74:f6:02

Frame 54 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: SmcNetwo_74:f6:02 (__:__:__:74:f6:02), Dst: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     55 1143.932100 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 55 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     56 1144.927903 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 56 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     57 1145.927962 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 57 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     58 1146.928001 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 58 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     59 1147.928058 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 59 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     60 1148.928105 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 60 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     61 1149.928155 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 61 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     62 1150.928204 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 62 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     63 1151.928251 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 63 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     64 1152.928302 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 64 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     65 1153.928346 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 65 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     66 1154.928394 192.168.2.100         192.168.2.1           ICMP     Echo (ping) request

Frame 66 (98 bytes on wire, 98 bytes captured)
Ethernet II, Src: AsustekC_ba:f5:a8 (__:__:__:ba:f5:a8), Dst: SmcNetwo_74:f6:02 (__:__:__:74:f6:02)
Internet Protocol, Src: 192.168.2.100 (192.168.2.100), Dst: 192.168.2.1 (192.168.2.1)
Internet Control Message Protocol

```

---

### Post by chewearn on 2008-03-10
Are you running heavy traffic across it, like multiple bittorrents?

---

