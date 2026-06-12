---
title: "Hostapd vlan"
date: 2019-04-30
forum: Networking &amp; Wireless
---

### Post by ulysse132 on 2019-04-30
Hello,

I try to create a wireless AP with only one SSID. I want this Wifi AP to link a wifi client to a vlan based on what provides a local RADIUS server. The router is on a different device

I build this AP on debian. I've crated all the vlan interfaces on ens18 (wired interfaced) with dhcp client (the ip are fixed on the router).

I can't achieve to link a user to an interface. I don't understand this options on */etc/hostapd/hostapd.conf* :
```
dynamic_vlan=1
vlan_file=/etc/hostapd.vlan
vlan_bridge
vlan_tagged_interface
```

When I try to lauch hostapd, I have this error messages :

```
Failed to create interface tr10: -95 (Operation not supported)
VLAN: Could not add VLAN tr10: Protocol not available
VLAN initialization failed.

```

tr10 is the name I put on /etc/hostapd.vlan

Thanks a lot for your help !

---

