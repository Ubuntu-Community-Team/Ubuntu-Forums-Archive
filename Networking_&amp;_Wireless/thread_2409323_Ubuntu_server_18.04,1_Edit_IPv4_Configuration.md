---
title: "Ubuntu server 18.04,1 Edit IPv4 Configuration"
date: 2018-12-31
forum: Networking &amp; Wireless
---

### Post by reuben-hyman on 2018-12-31
I'm getting  '10.32.68.201' is not contained in 255.255.255.192/26
I should have a range of 10.32.68.193 - 10.32.68.254
I'm getting this error and I can't continue.
Any help?

---

### Post by Daniel_Clarke on 2019-01-03
Hi,

I am having the same issue, did you ever get this resolved?

Here is my setup

Subnet: 255.255.255.0/24
IP:        192.168.200.200 'is not contained in 255.255.255.0/24'
Gatway 192.168.200.2

This address should also be available in my range, what is going on here?

Thanks

---

### Post by chili555 on 2019-01-03
Where are you setting these variables? Ubuntu server 18.04 uses netplan. Please see: ```

cat /usr/share/doc/netplan.io/examples/static.yaml
```The netmask 255.255.255.0 is not explicitly listed:```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 10.10.10.2/24
      gateway4: 10.10.10.1
      nameservers:
          search: [mydomain,otherdomain]
          addresses: [10.10.10.1, 1.1.1.1]

```It is, instead, implied by /24.

---

