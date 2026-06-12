---
title: "DHCP &amp; VLAN - config with 2 nic's"
date: 2017-03-26
forum: Networking &amp; Wireless
---

### Post by jimmyh1972 on 2017-03-26
Hello
I hava a Ubunut machine with 2 ethernet nics
enp0s3 is connected to a VPN
enp4s1 - I want to make it a DHCP server so that users that will connect to that interface will get an IP adrress and will be able to go "outside" to the www wan via the enp0s3 which is connected to the VPN
I thought about creating a VLAN from the enp4s1 nic but I dont know how to make it DHCP fro lan users and then make the VPN as its gateway
Thanks ahead - Jimmi

---

### Post by SeijiSensei on 2017-03-26
Install isc-dhcp-server then edit /etc/default/isc-dhcp-server like this:
```

INTERFACES="enp4s1"

```
to make the server listen only on that interface.

You'll need to edit /etc/dhcp/dhcpd.conf to your liking.  See this:  [https://help.ubuntu.com/community/isc-dhcp-server](https://help.ubuntu.com/community/isc-dhcp-server)

I don't know what you mean by VLANs.  Usually those are configured on a network switch.  I've never needed a VLAN in any simple networking arrangement.

---

