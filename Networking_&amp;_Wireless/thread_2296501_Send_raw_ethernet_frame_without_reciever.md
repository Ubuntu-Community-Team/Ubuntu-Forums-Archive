---
title: "Send raw ethernet frame without reciever"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by CkDGTAT on 2015-09-26
Hi,

I am looking for a way to send raw ethernet frame through a rj45 without any receptor at the end.

I cannot make this code work.

Thank you


```
#!/usr/bin/env python
from socket import socket, AF_PACKET, SOCK_RAW
s = socket(AF_PACKET, SOCK_RAW)
s.bind(("eth0", 0))

src_addr = "\x01\x02\x03\x04\x05\x06"
dst_addr = "\x01\x02\x03\x04\x05\x06"
payload = ("["*30)+"PAYLOAD"+("]"*30)
checksum = "\x1a\x2b\x3c\x4d"
ethertype = "\x08\x01"    

s.send(dst_addr+src_addr+ethertype+payload+checksum)
```

---

### Post by tgalati4 on 2015-09-26
Perhaps explain what you are trying to do--what is the goal of this activity?

Ethernet communication is a [7-layer]("http://www.google.com/imgres?imgurl=http://www.infocellar.com/networks/ethernet/files/frame.1.gif&imgrefurl=http://www.infocellar.com/networks/ethernet/frame.htm&h=436&w=570&tbnid=8Ma5CRpVN-5ldM:&docid=9hPXJjz3FYsJSM&ei=U6oGVqepMIunNqHQi5gH&tbm=isch&ved=0CCEQMygAMABqFQoTCOee9KPzlMgCFYuTDQodIegCcw") model with the physical connection between two devices the first layer.  Without this first layer, the other layers won't work.

The [ethernet frame]("https://en.wikipedia.org/wiki/Ethernet_frame") has a specific format, but it requires the underlying layers to function properly.  The [physical]("https://en.wikipedia.org/wiki/PHY_(chip)") layer has specific requirements.

When you import the socket functions into python, it presumes a standard OSI stack, which includes all of the layers.  You have to provide substitutes for layers that are missing to get the stack communication to work.

So I interpret your question as follows:

"I am trying to write a python script using the Layer-4 Socket library to transmit a Layer-3 Ethernet frame to an unknown/undefined Layer-1 device.  Why doesn't my script work?"

---

