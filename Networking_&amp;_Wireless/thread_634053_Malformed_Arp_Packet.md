---
title: "Malformed Arp Packet"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by luccom on 2007-12-07
I have Gusty installed on my laptop.

Whenever I plug in my network card on the network it always sends 5 malformed arp packet. 

0000   ff ff ff ff ff ff 00 16 41 a9 2c 24 08 06 00 00  ........A.,$....
0010   00 00 18 31 05 08 00 01 08 00 06 04 00 01 00 16  ...1............
0020   41 a9 2c 24 00 00 00 00 00 00 00 00 00 00 00 00  A.,$............
0030   00 00 00 00 00 00 00 00 00 00 00 00              ............

Can someone help me track the source of theses bad packet?

---

### Post by dervsh on 2008-01-10
Same thing here... or even worse...

I'm network administrator of 1000 hosts LAN.
Problem appeared first in my friend network too (~500 hosts LAN).

Most of my switches are managed 3Com 3xxx, 4xxx, Linksys SRW business series.
Those switches support STP protocol, which is turned on.

Problem concerns:
- Ubuntu 7.10 running as Live CD
- Ubuntu 7.10 installed, then aptitude update, aptitude safe-upgrade

Those Linuxes are sending a lot of broadcast malformed ARP packets. Mantioned ARP packets have no hardware type set and they contain a string "Move to 10mb on d3-packet" inside.

One Ubuntu box plugged to the network makes a total disaster, because of broadcast rate. Switches  sometimes hang connections.

My, partially working solution is to install arptables packet and execute commands below before interfaces are brought up...
/sbin/arptables -F
/sbin/arptables -A OUTPUT --h-type 1 -j ACCEPT
/sbin/arptables -P OUTPUT DROP
BUT... I still get those packets on gateway machine...

there is Wireshark dump:
No.     Time        Source                Destination           Protocol 
Info
       4 0.000016    08:00:46:db:27:c5     00:00:00:00:00:00     ARP 
   [Malformed Packet]

Frame 4 (60 bytes on wire, 60 bytes captured)
     Arrival Time: Nov 17, 2007 20:54:28.053279000
     Time delta from previous packet: 0.000005000 seconds
     Time since reference or first frame: 0.000016000 seconds
     Frame Number: 4
     Packet Length: 60 bytes
     Capture Length: 60 bytes
     Protocols in frame: eth:arp
Ethernet II, Src: 08:00:46:db:27:c5 (08:00:46:db:27:c5), Dst: 
00:00:00:00:00:00 (00:00:00:00:00:00)
     Destination: 00:00:00:00:00:00 (00:00:00:00:00:00)
         Address: 00:00:00:00:00:00 (00:00:00:00:00:00)
         .... ...0 .... .... .... .... = Multicast: This is a UNICAST frame
         .... ..0. .... .... .... .... = Locally Administrated Address: 
This is a FACTORY DEFAULT address
     Source: 08:00:46:db:27:c5 (08:00:46:db:27:c5)
         Address: 08:00:46:db:27:c5 (08:00:46:db:27:c5)
         .... ...0 .... .... .... .... = Multicast: This is a UNICAST frame
         .... ..0. .... .... .... .... = Locally Administrated Address: 
This is a FACTORY DEFAULT address
     Type: ARP (0x0806)
[Malformed Packet: ARP/RARP]

0000  00 00 00 00 00 00 08 00 46 db 27 c5 08 06 4d 6f   ........F.'...Mo
0010  76 65 20 74 6f 20 31 30 6d 62 20 6f 6e 20 44 33   ve to 10mb on D3
0020  2d 70 61 63 6b 65 74 00 6e 74 ab f9 d8 48 50 10   -packet.nt...HP.
0030  fa 4b 15 be 00 00 02 04 05 b4 01 01               .K..........

No.     Time        Source                Destination           Protocol 
Info
       5 0.000022    08:00:46:db:27:c5     00:00:00:00:00:00     ARP 
   [Malformed Packet]

Frame 5 (60 bytes on wire, 60 bytes captured)
     Arrival Time: Nov 17, 2007 20:54:28.053285000
     Time delta from previous packet: 0.000006000 seconds
     Time since reference or first frame: 0.000022000 seconds
     Frame Number: 5
     Packet Length: 60 bytes
     Capture Length: 60 bytes
     Protocols in frame: eth:arp
Ethernet II, Src: 08:00:46:db:27:c5 (08:00:46:db:27:c5), Dst: 
00:00:00:00:00:00 (00:00:00:00:00:00)
     Destination: 00:00:00:00:00:00 (00:00:00:00:00:00)
         Address: 00:00:00:00:00:00 (00:00:00:00:00:00)
         .... ...0 .... .... .... .... = Multicast: This is a UNICAST frame
         .... ..0. .... .... .... .... = Locally Administrated Address: 
This is a FACTORY DEFAULT address
     Source: 08:00:46:db:27:c5 (08:00:46:db:27:c5)
         Address: 08:00:46:db:27:c5 (08:00:46:db:27:c5)
         .... ...0 .... .... .... .... = Multicast: This is a UNICAST frame
         .... ..0. .... .... .... .... = Locally Administrated Address: 
This is a FACTORY DEFAULT address
     Type: ARP (0x0806)
[Malformed Packet: ARP/RARP]

0000  00 00 00 00 00 00 08 00 46 db 27 c5 08 06 4d 6f   ........F.'...Mo
0010  76 65 20 74 6f 20 31 30 6d 62 20 6f 6e 20 44 33   ve to 10mb on D3
0020  2d 70 61 63 6b 65 74 00 6e 74 ab f9 d8 48 50 10   -packet.nt...HP.
0030  fa 4b 15 be 00 00 02 04 05 b4 01 01               .K..........

No.     Time        Source                Destination           Protocol 
Info
       6 0.000027    08:00:46:db:27:c5     00:00:00:00:00:00     ARP 
   [Malformed Packet]

[...]

ANY help appreciated! (problem seems to exist since November and concerns only Linux Ubuntu boxes)

---

