---
title: "Cant find static IP insert"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by hendo2515 on 2014-11-26
Hello,

A while ago I added a static IP to my PC and now I can't find what I have done so that I can remove it ans start using DHCP.

/etc/network/interfaces
```
auto lo
iface lo inet loopback
```

uncommented lines in /etc/dhcp/dhclient.conf

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name = gethostname();

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        dhcp6.name-servers, dhcp6.domain-search,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers,
        dhcp6.fqdn, dhcp6.sntp-servers;

```

This is the dhclient process

```
/sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-866e771a-7cf9-4405-ac29-9aef371a5d3e-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
```

This is the uncommented lines in /var/lib/NetworkManager/dhclient-eth0.conf

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, domain-search, host-name,
dhcp6.name-servers, dhcp6.domain-search,
netbios-name-servers, netbios-scope, interface-mtu,
rfc3442-classless-static-routes, ntp-servers,
dhcp6.fqdn, dhcp6.sntp-servers;

send host-name "mel-prgd001"; # added by NetworkManager

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
option ms-classless-static-routes code 249 = array of unsigned integer 8;
option wpad code 252 = string;

also request rfc3442-classless-static-routes;
also request ms-classless-static-routes;
also request static-routes;
also request wpad;
also request ntp-servers;
```

Any idea how I can fix this. Any help given would be much appreciated 

Ubuntu 14.04

---

### Post by hendo2515 on 2014-11-26
Please ignore this. The problem turned out to be on the iternal network

---

