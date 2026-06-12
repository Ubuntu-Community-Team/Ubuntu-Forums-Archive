---
title: "Ubuntu Mate blocks Internet"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by Anahaym on 2016-02-15
Hi,
i installed Ubuntu mate on raspberrypi 2. One month all worked prefect.
Now i have a problem with Internet access. I have a network: two FritzBox Routers, one FritzBox 7490 has NAT and DHCP, second FritzBox 7390 works in Client-IP mode (DHCP and Firewall are off). Both routers have last firmware.
[IMG]http://fs.exonix.ru/network/wifi1.png[/IMG]
Ubuntu get an IP address 192.168.29.55, and can ping **only** the second router 192.168.29.28
**Other** devices, which connected to second router like a Laptop with IP 192.168.29.56, can ping all and has Internet.
i discussed this problem on FritzBox forums - no solutions. But if it will problem of router, then all connected devices haven't Internet.

My computer has IP 192.168.29.100 and connected to first router. I can ping Ubuntu once in twenty attempts.
Could you please help me? 

Thank you!

---

### Post by lensman3 on 2016-02-15
Sounds like you might have two devices with the same IPv4 address.  One device gets most of the traffic and the other R-pi occasionally get a packet because it is the (much) slower machine.

Fishing here.  Nice graphics.

---

### Post by Anahaym on 2016-02-16
> **lensman3 said:**
> Sounds like you might have two devices with the same IPv4 address.  One device gets most of the traffic and the other R-pi occasionally get a packet because it is the (much) slower machine.

Fishing here.  Nice graphics.

Hi **lensman3**, thank you for your answer.
i thought so, but if i shutdown R-Pi, i still can't ping any IP 192.168.29.55, and can't see a MAC address corresponding to this IP
when i turn on R-Pi i see his MAC addess.

---

### Post by Anahaym on 2016-02-23
so, in my case (Fritz blocks MAC of USB WiFi Card) i just changed USB-WiFi Card. Now all works.

---

