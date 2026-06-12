---
title: "How come my bond and bridge is down?"
date: 2018-08-09
forum: Networking &amp; Wireless
---

### Post by mattiash on 2018-08-09
I just added a bond interface and a bridge to my netplan file, but when checking the network bond0 and br0 is down, how come?

```

network:
    version: 2
    renderer: networkd
    ethernets:
        enp2s0f0:
            addresses: [10.10.1.80/24]
            gateway4:  10.10.1.1
            nameservers:
                addresses: [10.10.1.1]
            dhcp4: false
            optional: true
        enp2s0f1:
            addresses: [10.10.1.82/24]
            gateway4:  10.10.1.1
            nameservers:
                addresses: [10.10.1.1]
            dhcp4: false
            optional: true
        enp3s0f0:
            addresses: [10.10.1.84/24]
            gateway4:  10.10.1.1
            nameservers:
                addresses: [10.10.1.1]
            dhcp4: false
            optional: true
        enp3s0f1:
            addresses: [10.10.1.86/24]
            gateway4:  10.10.1.1
            nameservers:
                addresses: [10.10.1.1]
            dhcp4: false
            optional: true


    bonds:
        bond0:
            interfaces: [enp3s0f0, enp3s0f1]
            addresses: [10.10.1.90/24]
            gateway4: 10.10.1.1
            parameters:
                mode: 802.3ad
            nameservers:
                addresses: [10.10.1.1]
        
    bridges:
        br0:
            interfaces: [bond0]
            dhcp4: true
            optional: true

```

---

