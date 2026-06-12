---
title: "local only DNS function"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by andrew204 on 2015-02-24
Hi

I need to set up an isolated test network. I have a server which needs to communicate with the clients, but the clients will automatically go to "web.services.xyz.htv/webservices.php". I need that to be translated to "192.168.0.49:8082/iptvmanagement/php/webservices2k14/webservices.php". Its unfortunately not possible to change where they look, and I'm told it has to be done using a DNS server.

I want to run a ubuntu server vm to handle this with DNSMASQ to do the DHCP and DNS. As my expertise lie elsewhere, I'm not getting anywhere. All the examples I see for DNS seems to suggest that only short domains are capable of being translated to a local IP address - is that correct?

Would someone be so kind as to indicate what needs to be configured in DNSMASQ to get this one direction to happen? I'm not sure what's required for setting up a network like this.

Thanks a lot
Andrew

---

