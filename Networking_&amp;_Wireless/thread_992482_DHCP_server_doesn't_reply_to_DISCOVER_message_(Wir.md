---
title: "DHCP server doesn't reply to DISCOVER message (Wireless, WEP 8021x) (Ubuntu8.10)"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by guruqu on 2008-11-24
Hi all, so here is my problem i'm struggling with the whole day. I cannot get ip address from my DHCP server.

Wirless connection in our university is using { Dynamic WEP(8021x), PEAP, EAPMSCHAPv2} , i have configured correspondingly, and i think i have passed the authentication phase at this point because i can already see broadcast packets(DHCP,ARP..) come and go over the network (using WireShark). The strange thing is that I can never get reply for my DHCP-DISCOVER packet i sent. Funny thing is that i can also see DHCP packet sent by John Doe which succesffully finished DISCOVER-OFFER-REQUEST-ACK sequence. And I compared those two packets , they are basically the same. Pasted are the DHCP-DISCOVER packet sent by my computer (Ubuntu 8.10)

PS: Same computer using Windows XP doesn't have a problem getting IP address from DHCP server. 
```


User Datagram Protocol, Src Port: bootpc (68), Dst Port: bootps (
67)
Bootstrap Protocol
    Message type: Boot Request (1)
    Hardware type: Ethernet
    Hardware address length: 6
    Hops: 0
    Transaction ID: 0x39fd6161
    Seconds elapsed: 30
    Bootp flags: 0x0000 (Unicast)
    Client IP address: 0.0.0.0 (0.0.0.0)
    Your (client) IP address: 0.0.0.0 (0.0.0.0)
    Next server IP address: 0.0.0.0 (0.0.0.0)
    Relay agent IP address: 0.0.0.0 (0.0.0.0)
    Client MAC address: IntelCor_55:39:06 (00:1b:77:55:39:06)
    Server host name not given
    Boot file name not given
    Magic cookie: (OK)
    Option: (t=53,l=1) DHCP Message Type = DHCP Discover
    Option: (t=12,l=13) Host Name = "guruqu-laptop"
    Option: (t=55,l=11) Parameter Request List
    End Option
    Padding


```
Please help me :D. 
Thanks

PPS: I also got the same problem with my Nokai N78, iTouch which cannot connect to this particular network either, also stuck at DISCOVER phase.

---

