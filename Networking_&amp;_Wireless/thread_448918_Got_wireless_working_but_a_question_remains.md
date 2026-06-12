---
title: "Got wireless working but a question remains"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by attelas on 2007-05-19
After hours of trying to find out why my Intel 2200BG  couldn't connect to my AP which is secured with WPA-PSK/AES I finally managed to get it working. The problem was that Network Manager kept nagging about my password.
Changing the DHCP Server software running on the firewall seemed to be the solution!

It seems that the 'handshaking-proces" between client and AP only succesfully ends when the client is offered an IP address!
But in my opinion, establishing secure connections and acquiring IP addresses trough DHCP are two separate processes.

Does anyone has a clou?

---

