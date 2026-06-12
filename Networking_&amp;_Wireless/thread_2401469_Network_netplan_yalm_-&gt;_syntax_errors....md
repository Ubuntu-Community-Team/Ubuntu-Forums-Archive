---
title: "Network netplan yalm -&gt; syntax errors..."
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by BobMaze on 2018-09-18
First at all, the netplan/yalm implementation on ubuntu is the biggest mistake! My personal opinion!
Complicated and unuseable!

But... there seems no other way to setup the network on ubuntu server, so...

```
--- 
ethernets: 
  addresses: 
    - 192.168.50.224/24
  dhcp4: false
  dhcp6: false
  gateway4: "192.168.50.250"
  nameservers: 
    addresses: 
      - "192.168.50.225"
      - "192.168.50.250"
    search: 
      - lan
match: 
  name: enp*s*
network: 
  renderer: networkd
  version: 2

```
YALM Lint checked this config and it is CORRECT!
But ubuntu server netplan gives this error!

```
Error in network definition //etc/netplan/01-netcfg.yaml line 1 column 0: unknown key ethernets
```

So, what is wrong with ubuntu netplan implementation?!!!

---

### Post by The Cog on 2018-09-18
Looking at [https://netplan.io/examples](https://netplan.io/examples), maybe ethernets should be a child/sub-key of network?

---

### Post by BobMaze on 2018-09-19
It doesn't matter in which order this is. YAML Lint has restructured this!
I can also write it in the following order, the error is the same!

```

match: 
  name: enp*s*
network: 
  renderer: networkd
  version: 2
ethernets: 
  addresses: 
    - 192.168.50.224/24
  dhcp4: false
  dhcp6: false
  gateway4: "192.168.50.250"
  nameservers: 
    addresses: 
      - "192.168.50.225"
      - "192.168.50.250"
    search: 
      - lan

```
Or this order...
```

network: 
  renderer: networkd
  version: 2
match: 
  name: enp*s*
ethernets: 
  addresses: 
    - 192.168.50.224/24
  dhcp4: false
  dhcp6: false
  gateway4: "192.168.50.250"
  nameservers: 
    addresses: 
      - "192.168.50.225"
      - "192.168.50.250"
    search: 
      - lan

```
So, what is wrong with ubuntu netplan?

YALM Lint says, this is correct!

Edit:
So, I think... ubuntu netplan can't handle 'match' and 'name' directives!
This gives no error!
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s17:
#    match:
#      name: enp*s*
        addresses:
          - 192.168.50.224/24
        dhcp4: false
        dhcp6: false
        gateway4: "192.168.50.250"
        nameservers:
          addresses:
            - "192.168.50.225"
            - "192.168.50.250"
          search:
            - lan

```
This gives again an error!
```
network:
  version: 2
  renderer: networkd
  ethernets:
#    enp0s17:
    match:
      name: enp*s*
        addresses:
          - 192.168.50.224/24
        dhcp4: false
        dhcp6: false
        gateway4: "192.168.50.250"
        nameservers:
          addresses:
            - "192.168.50.225"
            - "192.168.50.250"
          search:
            - lan
```
Ubuntu bionic netplan is bugged?

---

### Post by The Cog on 2018-09-20
I am guessing because I haven't ever configured netplan, but perhaps ethernets should contain a list and not just an object? In which case, perhaps there should be a hyphen before the match keyword to make it the first element of a list.

---

