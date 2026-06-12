---
title: "Netplan Config Help for MaaS Region Controller"
date: 2019-05-31
forum: Networking &amp; Wireless
---

### Post by godsync on 2019-05-31
I have made this yaml for a 4 nic bond and a static IP but I need to add four VLANs to the bond. The vlans are 77, 88, 99, 333 could someone help me with this config? I also use the configuration for a KVM bridge with br0 and need that to still work. 

Thank you for help in advance

[https://gist.githubusercontent.com/RCFilm/f1916c69530f896029fa969dcceeae1a/raw/f05953ddb95f260b8e47b084d2bfa5bc29d5d8b2/01-network-manager-all.yaml](https://gist.githubusercontent.com/RCFilm/f1916c69530f896029fa969dcceeae1a/raw/f05953ddb95f260b8e47b084d2bfa5bc29d5d8b2/01-network-manager-all.yaml)

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

---

### Post by TheFu on 2019-05-31
netplan is yaml. yaml is indentation sensitive.  Use [code tags]("blog.jdpfu.com/code_tags") to fix the post above so it looks like it does in an editor/terminal.
Nobody can help until that is fixed.

I cannot help at all with netplan. Sorry.

---

### Post by #&amp;thj^% on 2019-05-31
Just my observation:
A working sample config:
```

network:
  version: 2
  renderer: NetworkManager
  #renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
      optional: true
      addresses: [XXX.XXX.196.33/20]
      gateway4: XXX.XXX.192.254
      nameservers:
        addresses: [XXX.XXX.192.80]
    enp4s0:
      dhcp4: true
  bridges:
     br0:
       dhcp4: true
       dhcp6: false
       optional: true
       interfaces: [enp4s0]
```
**Hint:  bridges get a new MAC address.**
Yours:
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
Oops forgot the important part,:p
```
ip link set enp4s0 up 
ip link set br0 up
```
Just in-case it wasn't obvious.

---

