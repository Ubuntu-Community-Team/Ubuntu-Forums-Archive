---
title: "Multiple NICs, setting default route permanently"
date: 2021-04-12
forum: Networking &amp; Wireless
---

### Post by brandon090 on 2021-04-12
Running fresh install of Ubuntu 20.04 minimal installation with GUI (even though it isnt being used with a monitor)
I have 2 network cards, enp1s0, and enp2s0.
When rebooting, 2 gateways are being set as default. The card I use internally on the lan (enp2s0) keeps getting overwritten as the 1st default gateway. If i manually delete the default gw on enp2s0, and set enp1s0 as the default gw, everything is OK.
When I reboot the gateways are overwritten and I have to manually set the routes again. Also it seems randomly the gateways get overwritten even without rebooting. I am assuming networkmanager is doing that?

How can I permanently set enp1s0 as the default route/gateway... I get conflicting information via google search....

---

### Post by TheFu on 2021-04-12
Does the computer move or will it be on the same network, always?
There's little need for network manager.  Just use the netplan YAML config file and setup whatever you like.  [https://netplan.io/](https://netplan.io/)  You'll want to change the renderer from NetworkManager to .... let me look: 
```
network:
  version: 2
  renderer: **networkd**
.....

```
plus add all the other stuff you need in there - static IP, network, gateway, nameservers. I suppose DHCP is supported. I don't use that.

Netplan YAML is highly indentation dependent, like all YAML files.  There are a number of example files in these forums too, if you need more examples than they show at the netplan.io site.

---

