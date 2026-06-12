---
title: "Operation not supported with ethtool to display or change RSS hashing"
date: 2016-03-06
forum: Networking &amp; Wireless
---

### Post by jerome24 on 2016-03-06
Hi,

I'm writing a UDP server (in Go) and running some load testing, I found out that only one CPU core was used by the server (out of 16). The server runs on 14.04. After doing some research, I found [https://blog.cloudflare.com/how-to-receive-a-million-packets/](https://blog.cloudflare.com/how-to-receive-a-million-packets/) that indicates this is because of the hashing algorithm that is used to pin each RX queue to a specific CPU core. The hash is probably a tuple (src ip, dst ip).

I wanted to confirm that so I ran: ```
ethtool -n eth0 rx-flow-hash udp4
``` but getting the following error:

> Cannot get RX network flow hashing options: Operation not supported

Trying to force including the ports in the hash with ```
ethtool -N eth0 rx-flow-hash udp4 sdfn
``` does not work either:


> Cannot change RX network flow hashing options: Operation not supported



Is there a different way to have access and change this information in ubuntu? Pretty much all the commands indicated on [http://syuu.dokukino.com/2013/05/linux-kernel-features-for-high-speed.html](http://syuu.dokukino.com/2013/05/linux-kernel-features-for-high-speed.html) end-up with the same error as above.

This is pretty bad, all traffic in our VPC is coming from the 10.116.0.0/24 range (or smth like that) and it seems all the traffic is hitting the same CPU core on the server, I need to be able to spread the load across more CPU cores.

Thanks
Jerome

---

