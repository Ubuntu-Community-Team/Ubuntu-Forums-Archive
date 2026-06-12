---
title: "GRE Tunnel Using Dynamic IP Address"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by James_Saunders on 2016-04-21
Hi All, I have not been able to find an answer to this anywhere but I know it must be possible. Basically I wish to create a GRE tunnel and encrypt it using IPSEC. No issues! What I want to do though is create this tunnel using a hostname rather than it's IP address for the end point. Reason being is this is a dynamic address and not static. So should the hostname change I wish the tunnel to still be built between them.

The server (this end) has a static IP address, the Cisco router at the far end has a dynamic IP address and I am using DYNDNS to update DNS records and track the hostname. Therefore I want the tunnel built at the server end to point to that hostname as the IP address will change.

I am sure there is a simple script or something which can effectively do a DNS lookup on the hostname, take the resolved IP address from this data and place it in a variable under the Tunnel destination in /etc/network/interfaces file and the bounce the tunnel.

Example:

iface gre200 inet tunnel
        mode gre
        address 172.32.200.106
        netmask 255.255.255.252
        endpoint 172.32.200.100
        dstaddr 172.32.200.105 (make this a variable) or can a hostname simply be used?
        local 192.168.1.9
        ttl 255

Any ideas appreciated. Thanks very much.

---

