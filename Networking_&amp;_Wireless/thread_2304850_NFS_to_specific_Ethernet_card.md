---
title: "NFS to specific Ethernet card"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by cranerja on 2015-11-30
Is there a way to export an NFS to a specific interface? I have a machine being used as a DHCP server and a file server that is connected directly to the internet with one connection and the to my home network with the other. I am worried that when I have it connected to the internet, it is vulnerable.

How would one secure this?

---

### Post by bab1 on 2015-12-01
> **cranerja said:**
> Is there a way to export an NFS to a specific interface?

Yes, but most likely not how you would think it would happen.
> 
 I have a machine being used as a DHCP server and a file server that is connected directly to the internet with one connection and the to my home network with the other. I am worried that when I have it connected to the internet, it is vulnerable.

How would one secure this?
The NFS service can be bound to the LAN side network (i.e. 192.168.1.0/24)  if you wanted.  

See [**here**]("https://help.ubuntu.com/community/NFSv4Howto") for more information.  Read the section under **_NFSv4 without Kerberos_** section: ***2. To export our directories to a local network 192.168.1.0/24 ***

You can also export to a specific address using just that clients IP address (i.e. 192.168.1.12).  You **can't **direct all the traffic *_out a specific NIC on the sever_*.    This just means you either export to clients IP addresses explicitly or to the subnet that the LAN NIC is configured for.

---

