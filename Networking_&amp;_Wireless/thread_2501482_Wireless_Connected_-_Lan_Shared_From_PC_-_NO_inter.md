---
title: "Wireless Connected - Lan Shared From PC - NO internet"
date: 2024-10-09
forum: Networking &amp; Wireless
---

### Post by stevenlutz1970 on 2024-10-09
Hi!

Ubuntu server 24.04 - Intel wifi 6 wireless card installed and connected to wifi - last resort test was to share my PC internet connection across the 10G switch hoping it would "grab it" - it did, and was assigned an IP address from the network sharing on the W11 PC, but neither the Ethernet nor the wireless are actually connecting to the internet.

I have removed cloud-init through apt, and disabled networkd in favor of NetworkManager.

Here are the two commands I remembered to copy, the results of nmcli, and the results of an attempted apt-update.

Please let me know if you need any more reports or tests.

Thank you!

```
steven@boticelli:~$ nmcli
enp4s0: connected to netplan-enp4s0
        "Aquantia AQC107 NBase-T/IEEE 802.3bz"
        ethernet (atlantic), F0:2F:74:70:09:24, hw, mtu 1500
        ip4 default
        inet4 192.168.137.15/24
        route4 192.168.137.0/24 metric 100
        route4 default via 192.168.137.1 metric 100
        inet6 fe80::f22f:74ff:fe70:924/64
        route6 fe80::/64 metric 256

wlp3s0: connected to netplan-wlp3s0-Monarch Guest
        "Intel 6 AX200"
        wifi (iwlwifi), 44:AF:28:14:7B:16, hw, mtu 1500
        inet4 10.67.97.105/24
        route4 10.67.97.0/24 metric 600
        route4 default via 10.67.97.1 metric 600

lo: connected (externally) to lo
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536
        inet4 127.0.0.1/8
        inet6 ::1/128

p2p-dev-wlp3s0: disconnected
        "p2p-dev-wlp3s0"
        wifi-p2p, hw

eno1: unavailable
        "Intel 82579V"
        ethernet (e1000e), AC:22:0B:50:FB:30, hw, mtu 1500

DNS configuration:
        servers: 192.168.137.1
        domains: mshome.net
        interface: enp4s0

        servers: 8.8.8.8 1.1.1.1 8.8.4.4
        interface: wlp3s0

Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.

Consult nmcli(1) and nmcli-examples(7) manual pages for complete usage details.
steven@boticelli:~$ sudo apt update
[sudo] password for steven: 
Ign:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Ign:2 http://security.ubuntu.com/ubuntu noble-security InRelease
Ign:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease
Ign:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Ign:2 http://security.ubuntu.com/ubuntu noble-security InRelease
Ign:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Ign:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease
Ign:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Ign:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Ign:2 http://security.ubuntu.com/ubuntu noble-security InRelease
Ign:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease
Ign:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Err:2 http://security.ubuntu.com/ubuntu noble-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/noble/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/noble-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
steven@boticelli:~$ 
```

---

### Post by stevenlutz1970 on 2024-10-09
file created and networkd disabled

/etc/cloud/cloud.cfg.d/99-disable-network-config.cfg

network: {config: disabled}

I should also state that wireless works on a clean install, but as soon as I introduce static IP address assignment to the 10G card, everything breaks.  That is also when the p2p-dev-wlp3s0 makes it's appearance.

50-*yaml

# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp4s0:
      dhcp4: true
      dhcp6: false
  wifis:
    wlp3s0:
      access-points:
        "Monarch Guest":
          password:

and NetworkManger created yaml

network:
  version: 2
  wifis:
    wlp3s0:
      renderer: NetworkManager
      match: {}
      dhcp4: true
      access-points:
        "Monarch Guest":
          auth:
            key-management: "psk"
            password: ""
          networkmanager:
            uuid: "bf345061-d63b-3bd1-9080-ec5ee42667b1"
            name: "netplan-wlp3s0-Monarch Guest"
            passthrough:
              connection.timestamp: "1728496866"
              ipv6.method: "disabled"
              ipv6.ip6-privacy: "-1"
              proxy._: ""
      networkmanager:
        uuid: "bf345061-d63b-3bd1-9080-ec5ee42667b1"
        name:

---

### Post by stevenlutz1970 on 2024-10-09
I found the answer - see netplan config:

# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
      enp4s0:
        dhcp4: false
        dhcp6: false
        addresses:
          - 192.168.1.177/24
        dhcp4-overrides:
          use-routes: no
          use-dns: no
    version: 2
    wifis:
        wlp3s0:
            access-points:
                Monarch Guest:
                    password: ************!
            dhcp4: true
            routes:
              - to: default
                via: 10.67.97.1

---

