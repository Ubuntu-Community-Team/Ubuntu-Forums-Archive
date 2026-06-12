---
title: "strange timestamp"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by saipkjai on 2008-02-22
Hi

  Right now, I'm trying to capture some ICMP packet to do some experimenting. When I try to 
```

timestamp -d localhost

```

and use wireshark to capture such ICMP packet, something really strange happened. 

This is the ICMP type 13 packet

Internet Control Message Protocol
    Type: 13 (Timestamp request)
    Code: 0 
    Checksum: 0xe30f [correct]
    Identifier: 0x0ff0
    Sequence number: 0 (0x0000)
    Originate timestamp: 0 time after midnight UTC
    Receive timestamp: 0 time after midnight UTC
    Transmit timestamp: 0 time after midnight UTC


so far so good. But when I take a look at the reply message. The following happen

Internet Control Message Protocol
    Type: 14 (Timestamp reply)
    Code: 0 
    Checksum: 0x18a4 [correct]
    Identifier: 0x0ff0
    Sequence number: 0 (0x0000)
    Originate timestamp: 0 time after midnight UTC
    Receive timestamp: 5 hours, 8 minutes, 59.419 seconds after midnight UTC
    Transmit timestamp: 5 hours, 8 minutes, 59.419 seconds after midnight UTC

Notice that the receive timestamp is 5 hours?!?!?!?!? I can assume everything that the packet was send and receive within 1 second. Why this strange thing happen? Anyone have any idea?

---

