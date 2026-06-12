---
title: "wireless AP using netplan on 24.04 -- how to disable dnsmasq"
date: 2024-09-11
forum: Networking &amp; Wireless
---

### Post by dhlacik on 2024-09-11
Guys, I am trying to setup Wifi AP using netplan.
My configuration is as follows

```

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enP3p49s0:
      mtu: 9000
    enP4p65s0:
      mtu: 9000
  bridges:
    br0:
      addresses:
        - "172.16.17.31/26"
      nameservers:
        addresses:
          - 172.16.17.1
      mtu: 9000
      interfaces:
        - enP3p49s0
        - enP4p65s0
      routes:
        - to: "default"
          via: "172.16.17.1"
  wifis:
    wlP2p33s0:
      addresses:
        - "172.18.15.8/26"
      regulatory-domain: "CZ"
      access-points:
        "SOWA":
          band: "5GHz"
          channel: 149
          mode: "ap"

```

This works however NetworkManager activates dnsmasq to setup DHCP Server and DNS server to auto-assign IPs for devices connecting for this AP. **I need to disable this behaviour**

On Ubuntu 22.04 it was easy -- just make sure dnsmasq package is not installed, NetworkManager will complain about it but it will work anyway. On Ubuntu 24.04 behaviour is completely different and NetworkManager will just not set-up this wifi AP.

As i learned there is no just option in netplan to disable it, so i went to study networkmanager behaviour and found out that it is somehow related to ipv4.method set to "shared" by default. I tried to set it manually via nmcli to "manual" but it will not help.

Thanks for helping me

PS : this is **edge device** not a desktop

---

