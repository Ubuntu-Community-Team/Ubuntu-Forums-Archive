---
title: "Keep getting IPV6 address for unknown reason"
date: 2019-02-08
forum: Networking &amp; Wireless
---

### Post by ve3dcl on 2019-02-08
During the initial installation of two Ubuntu 18.04 servers, I configured them a static IPv6 address. We will say it's aaaa:bbbb:cccc:dddd::11:1/64
It also has a link local address of fe80:1111:2222:3333


Out of left field, the server gets this "other" global IPv6 address and the service is seeing the "other" IPV6 address before the static IPV6.  I can ping both the static and "other" IPV6 addresses.  As you can see below, I don't have DHCP enabled.

```
~$ cat /etc/netplan/50-cloud-init.yaml# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        ens160:
            addresses:
            - aaaa:bbbb:cccc:dddd::11:1/64
            - 192.168.1.111/24
            dhcp4: false
            dhcp6: false
            gateway4: 192.168.1.1
            gateway6: aaaa:bbbb:cccc:dddd::1
            nameservers:
                addresses:
                - 192.168.1.1
                search: []
    version: 2
```

I welcome any tips on how to prevent getting this "other" IPV6 address.  Thank you

---

### Post by dmnur on 2019-02-09
Those are probably Router Advertisements. Add this parameter to disable them:
```
accept-ra: false
```

---

### Post by ve3dcl on 2019-02-10
It worked!  Thank you!

---

