---
title: "Installing IPsec Strongswan on Ubuntu VM"
date: 2017-07-25
forum: Networking &amp; Wireless
---

### Post by drcorchit on 2017-07-25
I'm trying to install Strongswan on an ubuntu machine to establish a VPN connection with an Amazon VPC subnet. Almost everything is fine but there's one issue I need to resolve: the Amazon configuration uses two tunnels as a failover, but the Ubuntu strongswan only shows one tunnel as being up when I check ipsec status. When I install strongswan on CentOS, it shows both tunnels as being up at the same time. However, on Ubuntu it seems to only set up one tunnel at a time. Also, if I modify the secrets file and comment out the line for tunnel 1's PSK, it automatically switches over to tunnel 2. Then, it uses tunnel2 until I comment out tunnel 2 and switch back to tunnel 1 in the secrets file. So, I know that both tunnels are configured correctly and I want to know why they both go up at the same time on CentOS, but only one goes up at a time on Ubuntu. Is this intended behavior?

Ipsec Version: Linux strongSwan U5.1.2/K3.13.0-24-generic

Ipsec Status:
Security Associations (2 up, 0 connecting):
VPC-CUST-GW2[2]: ESTABLISHED 9 minutes ago, xxx.xxx.197.155[xxx.xxx.197.155]...xx.x.34.229[xx.x.34.229]
VPC-CUST-GW1[1]: ESTABLISHED 9 minutes ago, xxx.xxx.197.155[xxx.xxx.197.155]...yy.yyy.109.192[yy.yyy.109.192]
VPC-CUST-GW1{1}:  INSTALLED, TUNNEL, ESP in UDP SPIs: ca9fc5c0_i 45cc8e55_o
VPC-CUST-GW1{1}:   192.168.0.0/24 === 10.0.0.0/16 

As you can see, VPC-CUST-GW2 says "established" but it doesn't show anything else below it.

---

