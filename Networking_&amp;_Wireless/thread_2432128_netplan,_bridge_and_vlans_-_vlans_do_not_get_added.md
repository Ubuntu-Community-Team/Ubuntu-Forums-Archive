---
title: "netplan, bridge and vlans - vlans do not get added to the bridges"
date: 2019-11-27
forum: Networking &amp; Wireless
---

### Post by jakkuk on 2019-11-27
So i'm trying to configure a host to use vlans on bridges on 18.04. I've read a bunch of manuals and have a NEARLY working config:

```
# cat /etc/netplan/50-cloud-init.yaml 
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    renderer: networkd
    ethernets:
        rename2:
            addresses:
            - 192.168.0.130/22
            critical: true
            gateway4: 192.168.0.1
            match:
                macaddress: 0c:c4:7a:xx:xx:xx
            nameservers:
                addresses:
                - 192.168.0.251
                search:
                - biuro.xxx.pl
            set-name: rename2
        rename4:
            match:
                    macaddress: 0c:c4:7a:xx:xx:xy
            dhcp4: no
            dhcp6: no
    vlans:
            vlan-dmz1:
                    id: 68
                    link: rename4
                    dhcp4: no
                    dhcp6: no
            vlan-lan:
                    id: 1
                    link: rename4
                    dhcp4: no
                    dhcp6: no
    bridges:
            br-dmz1:
                    interfaces: [ vlan-dmz1 ]
                    dhcp4: no
                    dhcp6: no
            br-lan:
                    interfaces: [ vlan-lan ]
                    dhcp4: no
                    dhcp6: no
    version: 2

```

I want to connect VMs under virsh/KVM using this host, that's why the bridges do not have any addresses.

so everything works nice, but the vlan-dmz1 and vlan-lan interfaces do not get added to the bridges. I need to add them manually to the bridges:

```
# brctl show
bridge name	bridge id		STP enabled	interfaces
br-dmz1		8000.325bf70b5729	no		
br-lan		8000.a2b35026070d	no		
# brctl addif br-dmz1 vlan-dmz1
# brctl show
bridge name	bridge id		STP enabled	interfaces
br-dmz1		8000.325bf70b5729	no		vlan-dmz1
br-lan		8000.a2b35026070d	no
```

The question is - where did I make a mistake? Or maybe there's a delay somewhere that needs to be added...

---

