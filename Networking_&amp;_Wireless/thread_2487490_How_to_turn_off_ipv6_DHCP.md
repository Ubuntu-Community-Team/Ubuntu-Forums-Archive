---
title: "How to turn off ipv6 DHCP?"
date: 2023-06-06
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2023-06-06
I'm setting up ipv4/ipv6 router on Ubuntu server 22.04. Figured out virtually everything. But still can't solve one issue. In my setup, I don't need systemd-networkd to request DHCP for ipv6, it's done by isc-dhcp-client. But there is still ipv6 dhcp request from systemd-networkd, even though dhcp is set to "false" in Netplan.

Here's Netplan file content:


network:
  ethernets:
    eno1:
      dhcp4: true
      dhcp6: false
      ipv6-privacy: true
      accept-ra: true
    enp4s0:
      addresses: [192.168.10.6/24,192.168.10.1/24]
        #gateway4: 192.168.10.1
      nameservers:
        addresses: [192.168.10.1,192.168.10.2]
        search: [****-****.****]
      dhcp4: no
        #routes:
        #- to: default
        #via: 192.168.10.1
  version: 2

eno1 is the WAN interface. BTW, dhcp6 is not set for the LAN interface enp4s0, but it's still getting an address from radvd (which is what I need).

Anyway, how to prevent systemd-networkd from requestion ipv6 dhcp?

---

### Post by #&amp;thj^% on 2023-06-06
Editing /etc/netplan/01-netcfg.yaml, configure:
```

network:
  ...
  ethernets:
    eth0:
      ...
      dhcp6: no
      accept-ra: no
```

You will need to use your interface name instead of eth0. After you save the file execute:"netplan apply or reboot"

If you already have received an IPv6 IP from autoconfiguration and you want to remove it without rebooting, you can execute:
```

ip -6 addr del 1111:2222:1:0:aaaa:bbbb:cccc:dddd/64 dev eth0
``` 

Of course you need to replace the IP and device in this command.
EDIT: Also have a careful read for: [https://installati.one/install-radvd-ubuntu-20-04/](https://installati.one/install-radvd-ubuntu-20-04/)
That might be what you need.

---

### Post by Alex_Filonov on 2023-06-06
Well, I thought I need accept-ra: true, because it's a router. OK, will try it and post results.

---

### Post by Alex_Filonov on 2023-06-11
OK, after I figured out proper way to set up dhclient, I have no problem with the second ipv6 address. I will post my router configuration in a separate thread.

---

