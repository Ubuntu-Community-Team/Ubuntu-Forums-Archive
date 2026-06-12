---
title: "Netplan bond/bridge MTU setting not being honored on Bionic system"
date: 2018-12-07
forum: Networking &amp; Wireless
---

### Post by andre-o on 2018-12-07
*****EDIT***  I solved this, I had the mtu setting on the 'parameters: ' level, rather than under the bond and bridge device.**


I'm running Netplan on an 18.04 system.  I've been able to workout and convert most of my network configuration from my 16.04 systems to Netplan for 18.04, however I've run into an issue now when trying to set the MTU to 9000 on a bridge that uses a bond that is part of a VLAN.


My configuration:


```
    # Ceph network configuration
    network:
      version: 2
      renderer: networkd
      ethernets:
        eth2:
          dhcp4: no
          dhcp6: no
          optional: true
          mtu: 9000
        eth3:
          dhcp4: no
          dhcp6: no
          optional: true
          mtu: 9000
      bonds:
        bond1:
          interfaces: [ eth2, eth3 ]
          parameters:
            mode: 802.3ad
            mii-monitor-interval: 100
            lacp-rate: fast
      vlans:
        bond1.220:
          id: 220
          link: bond1
          mtu: 9000
      bridges:
        br-ceph-access:
          addresses: [ x.x.x.x/24 ]
          interfaces: [ bond1.220 ]
          parameters:
            forward-delay: 9
            hello-time: 2
            max-age: 12
            stp: false

```

I've added 'mtu: 9000' to both NICs that are part of the bond, and to the VLAN as well.  I've done this, because the adding 'mtu: 9000' to the bond interface or the bridge interface produces the error "unknown key mtu"


In any case, the `mtu: 9000` setting is not honored, as you can see here in the relevant sections of `ip a` (notice `mtu 15000`):


```
    4: eth2: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond1 state UP group default qlen 1000
        link/ether b2:07:76:18:10:5b brd ff:ff:ff:ff:ff:ff
    5: eth3: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond1 state UP group default qlen 1000
        link/ether b2:07:76:18:10:5b brd ff:ff:ff:ff:ff:ff
    10: br-ceph-access: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
        link/ether 4e:b5:52:25:a4:c5 brd ff:ff:ff:ff:ff:ff
        inet x.x.x.x/24 brd 172.16.238.255 scope global br-ceph-access
           valid_lft forever preferred_lft forever
    11: bond1: <BROADCAST,MULTICAST,MASTER> mtu 1500 qdisc noop state DOWN group default qlen 1000
        link/ether b2:07:76:18:10:5b brd ff:ff:ff:ff:ff:ff

```

So where am I going wrong here?  What is the proper way to set mtu with Netplan?  Have I discovered a bug that needs to be reported?

---

### Post by andre-o on 2018-12-07
I resolved this by placing the mtu setting under the right level -- i.e., under the bond/bridge device rather than under 'parameters: '

The working config:
```
# Ceph network configuration
network:
  version: 2
  renderer: networkd
  ethernets:
    eth2:
      dhcp4: no
      optional: true
    eth3:
      dhcp4: no
      optional: true
  bonds:
    bond1:
      interfaces: [ eth2, eth3 ]
      mtu: 9000
      parameters:
        mode: 802.3ad
        mii-monitor-interval: 100
        lacp-rate: fast
  vlans:
    bond1.220:
      id: 220
      link: bond1
      optional: true
  bridges:
    br-ceph-access:
      optional: true
      addresses: [ x.x.x.x/24 ]
      interfaces: [ bond1.220 ]
      mtu: 9000
      parameters:
        forward-delay: 9
        hello-time: 2
        max-age: 12
        stp: false

```

---

### Post by godsync on 2019-05-31
That looks great.
I was wondering if you could help with my config

I am trying to achieve adding four VLANs to my config without messing up my bridge or bonds.

The VLAN's are 77, 88, 99, 333

[https://gist.githubusercontent.com/RCFilm/f1916c69530f896029fa969dcceeae1a/raw/f05953ddb95f260b8e47b084d2bfa5bc29d5d8b2/01-network-manager-all.yaml](https://gist.githubusercontent.com/RCFilm/f1916c69530f896029fa969dcceeae1a/raw/f05953ddb95f260b8e47b084d2bfa5bc29d5d8b2/01-network-manager-all.yaml)

_______
```

network:
    bridges:
        br0:
            addresses:
            - 10.0.77.2/24
            dhcp4: false
            gateway4: 10.0.77.1
            nameservers:
                addresses:
                - 10.0.77.1
                - 8.8.8.8
            interfaces:
                - bond0
    bonds:
        bond0:
            interfaces:
            - eno1
            - eno2
            - eno3
            - eno4
            parameters:
                mode: balance-xor
    ethernets:
        eno1:
            addresses: []
            dhcp4: false
            dhcp6: false
        eno2:
            addresses: []
            dhcp4: false
            dhcp6: false
        eno3:
            addresses: []
            dhcp4: false
            dhcp6: false
        eno4:
            addresses: []
            dhcp4: false
            dhcp6: false
```
__________________

---

