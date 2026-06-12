---
title: "Netplan/NetworkManager not using dhclient at boot"
date: 2023-06-22
forum: Networking &amp; Wireless
---

### Post by triatic on 2023-06-22
I would like to use dhclient as my DHCP client, and as systemd-networkd does not support this, I would like to switch to Network Manager in Ubuntu 22.04.

My Netplan configuration is as follows:

```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp0s6:
      critical: true
      nameservers:
        addresses:
        - 169.254.169.254
        search:
        - vcn38927584.oraclevcn.com
      dhcp-identifier: "mac"
      dhcp4: true
      dhcp6: true
```

And I have instructed Network Manager to use dhclient:

```
:~$ cat /etc/NetworkManager/conf.d/dhcp-client.conf
[main]
dhcp=dhclient
```

The issue is that I am not getting an IPv6 address from dhclient after reboot until I manually apply the Netplan settings:

```
:~$ ping -6 google.com
ping: google.com: Temporary failure in name resolution

:~$ sudo netplan apply

:~$ ping -6 google.com
PING google.com(lhr25s32-in-x0e.1e100.net (2a00:1450:4009:81e::200e)) 56 data bytes
64 bytes from lhr25s32-in-x0e.1e100.net (2a00:1450:4009:81e::200e): icmp_seq=1 ttl=120 time=1.52 ms
64 bytes from lhr25s32-in-x0e.1e100.net (2a00:1450:4009:81e::200e): icmp_seq=2 ttl=120 time=1.37 ms
64 bytes from lhr25s32-in-x0e.1e100.net (2a00:1450:4009:81e::200e): icmp_seq=3 ttl=120 time=1.39 ms
```

Why isn't Netplan/NetworkManager using dhclient at boot?

---

