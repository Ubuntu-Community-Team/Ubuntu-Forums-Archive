---
title: "IPv4 Manual Configuration Not Working"
date: 2019-01-03
forum: Networking &amp; Wireless
---

### Post by Daniel_Clarke on 2019-01-03
I am trying to install Ubuntu 18.04 LTS, when going through the installation it appears I can configure the network manually, when I attempt I run into the following issue while configuring the IPv4 settings

It wants the CIDR format for the Subnet, our Subnet is 255.255.255.0 so our CIDR should be 255.255.255.0/24 which it will accept. However it says our static ip address we are trying to assign which is 192.168.200.100 "is not contained in the 255.255.255.0/24". Which is confusing because all of our other machines and servers are on a 192.168.200.xxx configuration and working fine including an old 16.04 LTS server.

Can anyone help me troubleshoot this issue?

Thanks in aadvance

-daniel

---

### Post by chili555 on 2019-01-03
For the CIDR format netmask, will the installation accept, simply, /24?

---

