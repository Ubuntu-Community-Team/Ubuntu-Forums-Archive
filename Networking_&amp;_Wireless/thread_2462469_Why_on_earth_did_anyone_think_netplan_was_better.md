---
title: "Why on earth did anyone think netplan was better?"
date: 2021-05-21
forum: Networking &amp; Wireless
---

### Post by sturmey2 on 2021-05-21
So I'm fighting with a new server that is up to date (just ran the commands in the past hour) and I'm trying to add a static persistent route to force all UDP traffic to a single interface.

in the past the command was simple:
sudo ip route -p add 239.0.0.0/8 dev eth1

But now, the -p doesn't work. Everything that google brings us says "just use -p to make it persistent" and there are Thousands of web sites and forum posts echoing the same thing, but now with the new improved NETPLAN none of that works, and I've spend 2 hours trying to find the commands on how to get this pig to oink. 

Yeah I've read [https://netplan.io/faq/](https://netplan.io/faq/) and I can't disagree more with what's written there. It has NOT made it easier, it's made it much more difficult. I think I've found what's needed, but everytime I try to apply it I get more errors. Why was this deployed with so little good documentation?

```
yaml file:
  GNU nano 4.8                          00-installer-config.yaml
# This is the network config written by 'subiquity'
network:
  ethernets:
    eno1:
      dhcp4: true
    eno2:
      dhcp4: true
    enp193s0f0:
      addresses:
      - 10.199.200.100/24
      gateway4: 10.199.200.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 1.1.1.1
        search: []
    enp193s0f1:
      dhcp4: true
    enp193s0f2:
      dhcp4: true
    enp193s0f3:
      addresses:
      - 10.199.199.100/24
      nameservers:
        addresses: []
        search: []
      routes:
      -to: 239.0.0.0/8
      via: dev enp193s0f3
  version: 2

```


And the output when I try to apply it:
```
support@cameras:/etc/netplan$ sudo netplan apply
/etc/netplan/00-installer-config.yaml:27:14: Error in network definition: expected sequence
      routes:
             ^
```

How is this better?

---

### Post by The Cog on 2021-05-21
Yaml syntax is rather hard to get used to. I'm guessing, but I think your indenting for the route is wrong, and missing a space before the 'to'. Try this:```

network:
  ethernets:
    eno1:
      dhcp4: true
    eno2:
      dhcp4: true
    enp193s0f0:
      addresses:
      - 10.199.200.100/24
      gateway4: 10.199.200.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 1.1.1.1
        search: []
    enp193s0f1:
      dhcp4: true
    enp193s0f2:
      dhcp4: true
    enp193s0f3:
      addresses:
      - 10.199.199.100/24
      nameservers:
        addresses: []
        search: []
      routes:
      - to: 239.0.0.0/8
        via: dev enp193s0f3
  version: 2

```
Or you may find this easier to read:```
network:
    ethernets:
        eno1: {dhcp4: true}
        eno2: {dhcp4: true}
        enp193s0f0:
            addresses: [10.199.200.100/24]
            gateway4: 10.199.200.1
            nameservers:
                addresses: [8.8.8.8, 1.1.1.1]
                search: []
        enp193s0f1: {dhcp4: true}
        enp193s0f2: {dhcp4: true}
        enp193s0f3:
            addresses: [10.199.199.100/24]
            nameservers:
                addresses: []
                search: []
            routes:
            - {to: 239.0.0.0/8, via: dev enp193s0f3}
    version: 2


```

---

