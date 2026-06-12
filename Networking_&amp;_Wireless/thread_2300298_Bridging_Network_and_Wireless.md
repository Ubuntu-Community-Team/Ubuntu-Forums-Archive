---
title: "Bridging Network and Wireless"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by 6-webmaster-a on 2015-10-24
Hello everyone,
I need a bridge setup with wireless access.

I'm using hostapd for the wireless hotspot.

Our network now:

```
Router & Modem  ------>  Server & Wireless & DNS
192.168.0.1/24    |      192.168.0.10/24
                  |
                  |
                  |
                  v
          Clients (DHCP from Router)
          192.168.0.100-150/24
          DNS: 192.168.0.10
```




**What we need:**

```
Router & Modem  ------>  Server & Wireless & DNS  ------>  Wireless Clients (DHCP from Router)
192.168.0.1/24    |      192.168.**1**.10/24                   192.168.**1**.100-150/24
                  |                                        DNS: 192.168.**1**.10
                  |
                  |
                  v
          Clients (DHCP from Router)
          192.168.**1**.100-150/24
          DNS: 192.168.**1**.10
```


So we need to change the subnet of the server and clients to **192.168.1.0**. I need a configuration for a bridge from **192.168.1.0 to ****192.168.0.0 **that the clients can still access the internet. Same counts for the wireless clients which are connected to the Server.

We are running Ubuntu 14.04.3 on the server. It has only one cable NIC and the wireless card (has AP support).

I think the server needs a bridged device with 2 ip's and a route from the one network to the other. But what about the wireless in this case?

Any ideas/help?

This is my network configuration so far:

```
auto lo
iface lo inet loopback


auto br0
iface br0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    bridge_ports eth0
    bridge_fd 5
    bridge_stp no

auto br0:0
iface br0:0 inet static
    address 192.168.0.10
    netmask 255.255.255.0
    gateway 192.168.0.1
```

Thank's very much to all of you!


edit: SOlved it. I revoked the br0:0 interface and added a second IP with "up ip addr add 192.168.2.10/24 dev br0" in /etc/network/interfaces. Then I just needed to setup the iptables rules and it works like a charm. Thanks anyways!

---

