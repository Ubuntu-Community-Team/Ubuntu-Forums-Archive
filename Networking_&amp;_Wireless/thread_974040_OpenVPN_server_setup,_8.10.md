---
title: "OpenVPN server setup, 8.10"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by NitroBooster on 2008-11-07
I got the latest repo OpenVPN up on Intrepid, the client connects, but there is no internet on the client side. (with or without firestarter)

What should I be checking?

This server is on a static IP

I suspect this has to do with DNS. DNS requests from 10.8.0.0 are being blocked by host OS. How do I fix that?

I can ping the VPN server from the client:
> 
C:\Documents and Settings\admin>ping 10.8.0.1

Pinging 10.8.0.1 with 32 bytes of data:

Reply from 10.8.0.1: bytes=32 time=19ms TTL=64
Reply from 10.8.0.1: bytes=32 time=17ms TTL=64
Reply from 10.8.0.1: bytes=32 time=17ms TTL=64
Reply from 10.8.0.1: bytes=32 time=19ms TTL=64

Ping statistics for 10.8.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 19ms, Average = 18ms

C:\Documents and Settings\admin>


---

