---
title: "Ubuntu boxes don't appear in Windows DNS server"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by ztirffritz on 2008-01-17
I manage a network of mostly Windows computers.  The DNS and DHCP servers are on a W2k3 Server.  I have several Ubuntu boxes in the network as clients only.  They are pulling IP addresses from DHCP and they successfully pull all of the needed info to connect to the network and the internet, but the DNS server never registers that they exist.  The result is that the Ubuntu clients can only be reached via IP address.  Their hostnames do not resolve through the Windows DNS server.  How to I get the Windows server to notice that the Ubuntu clients exist?  I could give them static IPs and create a DNS pointer manually, but that is not what I want.  I need to have the machines DHCP and automatically registering with the DNS server.  
So far I've modified the resolv.conf file as below (It is functionally the same, but I've 'anonymized' the info):

> domain acme.local
nameserver 192.168.1.1
nameserver 192.168.1.2
search acme.local


I've also tinkered a bit with DHClient.conf, but I haven't found any good information to explain how to configure it yet, so I haven't changed much and nothing has really helped yet anyway.

Does anyone know of a fool-proof explanation of how to make the Ubuntu Clients hostname resolve through the Windows DNS?

---

### Post by dynnamitt on 2008-03-11
I'm having the same issue.
It's just TO boring to manually register each new Linux inside the Windows DNS app.

The other day I did install one virtual appliance that magically seems to fix it:
[http://www.young-technologies.com/Software/Subversion-Virtual-Machine/](http://www.young-technologies.com/Software/Subversion-Virtual-Machine/)

but I don't understand what this vm has that my own "clean" ubuntu servers don't....

Please help - someone.

---

### Post by netztier on 2008-03-11
> **ztirffritz said:**
> 
I've also tinkered a bit with DHClient.conf, but I haven't found any good information to explain how to configure it yet, so I haven't changed much and nothing has really helped yet anyway.


That's the good approach.

But first, check how the Windows Client's IP addresses make it into DNS. There's basically two ways:
[LIST]
[*]Windows Client itself sends a DDNS update to the DNS server. The DNS must be configured to allow this (might be default on W2k3's DNS server). On most other DNS servers, this is disabled and they do not accept DDNS updates from "anyone".
[*]DHCP Server sends DDNS update to the DNS server. It uses the name that the DHCP client has submitted in it's DHCP request message. Here, the DNS must accept updates from the DHCP server, and clients must be configured to include their host name in the DHCP request
[/LIST]

For the first, I guess there should be some ddns scripts available that you can launch form /etc/network/interfaces as post-up scripts for the interface in question:

```
# The primary network interface
auto eth0
 iface eth0 inet dhcp
 post-up /path/to/your/ddns-script

```


For the latter, see the **send hostname "...";** option in /etc/dhcp3/dhclient.conf in Linux. Activating this option should include the hostname in the DHCP request. If configured accordingly, the DHCP server will see this and send a corresponding DDNS update to the DNS server.

regards

Marc

---

