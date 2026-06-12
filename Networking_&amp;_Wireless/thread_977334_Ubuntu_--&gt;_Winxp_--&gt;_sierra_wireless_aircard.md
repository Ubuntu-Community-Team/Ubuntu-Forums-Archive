---
title: "Ubuntu --&gt; Winxp --&gt; sierra wireless aircard"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by dirtycanuck on 2008-11-10
*edit* ran in circles for hours, posted, then solved 5 minutes later. In the network manager, under the DNS tab,Ubuntu tries to use the router as a DNS server. Delete this listing and add the IP of the gateway computer. Leaving both IPs does not work.

This is probably pretty elementary to most, but noted just in case somebody runs into the same issue ***

Haven't found this variant anywhere in the forum yet...

I've got a Sierra Wireless 595 aircard connected to a machine running winxp. This is in turn connected to a dLink router. I've been able to access the shared internet connection with another laptop running winxp, but not with Ubuntu 8.04.

- I can access shared folders on the winxp machine with Ubuntu
- Tried assigning a static IP to the ubuntu machine. 
- using the network manager, specified the following:
    ip address 192.168.0.101  (static ip assigned by router)
    subnet mask: 255.255.255.0
    gateway address: 192.168.0.1 (winxp machine)

This is the closets that I've ever had to full functionality for a wireless card in any linux distro, but adding internet would be great if anybody has any advice.

Thanks in advance
Mike

---

