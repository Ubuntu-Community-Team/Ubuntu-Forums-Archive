---
title: "Dnsmasq and NetworkManager"
date: 2016-04-29
forum: Networking &amp; Wireless
---

### Post by Imaginary on 2016-04-29
I've got a Xubuntu 14.04.04 LTS workstation with two (wired) Ethernet connections.

[LIST]
[*]eth0[LIST]
[*]PCIe on the motherboard
[*]Local LAN connection and out to the world at large
[*]I get assigned an IP on 172.16.*.* from the local DHCP server.
[*]NetworkManager is used to tell this interface to accept DHCP.
[*]I get assigned a local DNS server to perform host lookups against (which forwards non-local stuff out to the world)
[/LIST]

[*]eth1[LIST]
[*]USB-Ethernet dongle
[*]Local isolated subnet to communicate with equipment within 5 feet.
[*]Often just a point-to-point link without a hub, so the connection goes up and down
[*]NetworkManager is used to set this interface to a static IP of 192.168.0.1
[*]I want to serve DHCP to this equipment in 192.168.0.*
[*]I want to resolve this equipment by hostname
[/LIST]

[/LIST]

So it seems like what I want is to have my system running dnsmasq and serving DHCP on eth1 (and NOT on eth0), and have any attempts to resolve by hostname first check my locally assigned leases and, failing this, fall back to querying the LAN DNS server.  But I've tried all manner of thing, and just can't get the combination of NetworkManager and dnsmasq (which I (think I) allow NetworkManager to manage) to do this.  I go in with Wireshark and see the devices sending out DHCP Discovers, but my side just doesn't response.

Any thoughts would be greatly appreciated.  The two things I can think of that make this easier are:
[LIST=1]
[*]This is a stationary machine with no wifi, so telling NetworkManager to just go away is a viable option.
[*]The devices on eth1 all act as servers only.  They need to accept inbound connections, but they don't need to be able to see the rest of the world.
[/LIST]

**/etc/NetworkManager/NetworkManager.conf**
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=00:50:B6:15:6E:9A,54:04:A6:64:B5:A6,

[ifupdown]
managed=false

[logging]
level=INFO

```

**/etc/NetworkManager/dnsmasq.d/teststand.conf**
```

no-dhcp-interface=eth0
no-negcache
dhcp-range=192.168.0.200,192.168.0.220
log-dhcp
domain=local

```

**/proc/1497/cmdline**
```
/usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq-r/var/run/dnsmasq/resolv.conf -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
```

---

