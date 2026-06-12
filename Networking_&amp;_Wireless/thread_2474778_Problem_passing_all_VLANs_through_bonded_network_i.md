---
title: "Problem passing all VLANs through bonded network interfaces"
date: 2022-05-07
forum: Networking &amp; Wireless
---

### Post by cneeper on 2022-05-07
Ubuntu Server 20.04 being used with KVM to host multiple virtual machines. Multiple NICs are bonded using 802.3ad and an appropriately configured smart switch. Several bridges are configured to specific individual VLANs. My netplan YAML configuration works and I can assign any given virtual machine's network interface to whichever bridge interface I want and it will successfully communicate on the intended VLAN in the overall network. However, I have one virtual machine that I need to bridge ALL VLANs to and I'm having problems getting that to happen via the bonded interfaces. (If you're familiar with VMware ESXi, what I'm trying to achieve is equivalent to VLAN 4095.)

Below is a simplified version of my YAML. The host Ubuntu server's IPv4 address is assigned to the br_admin bridge, which is the VLAN used to communicate with the host. I can place a virtual machine on a specific VLAN by configuring the virtual machine's interface to the appropriate bridge interface. I had hoped to be able to pass all VLANs through to a virtual machine by configuring the vm's interface to br_allvlans. But that doesn't seem to work as I had hoped. I've been researching this for quite a while and would greatly appreciate any suggestions! 

EDIT:  Additional info -- It DOES work as desired if I edit my YAML to assign my bridge (br_allvlans) to a *_single_* interface instead of a bond (bond0). It's only when I try to bridge to the bond that it won't work.

```
network:  version: 2
  renderer: networkd
  ethernets:
    all_eth:
      match:
        # match all network interfaces
        name: "en*"
      dhcp4: no
      dhcp6: no
      optional: true
  bonds:
    bond0:
      interfaces: [ all_eth ]
      parameters:
        mode: 802.3ad
        transmit-hash-policy: layer2+3
        min-links: 1
        mii-monitor-interval: 500ms
      dhcp4: no
      dhcp6: no
      link-local: []
  bridges:
    br_allvlans:
      dhcp4: no
      dhcp6: no
      link-local: []
      interfaces: [ bond0 ]
    br_admin:
      addresses: [ 10.1.1.11/24 ]
      gateway4: 10.1.1.1
      nameservers:
          search: [corp.domain.com, domain.com]
          addresses: [10.1.1.1]
      dhcp6: no
      link-local: []
      interfaces: [ vlan1001 ]
    br_wan:
      dhcp4: no
      dhcp6: no
      link-local: []
      interfaces: [ vlan1005 ]
  vlans:
    vlan1001:
      accept-ra: no
      id: 1001
      link: bond0
    vlan1005:
      accept-ra: no
      id: 1005
      link: bond0

```

---

### Post by cyclingrunning on 2022-08-23
Hi,

I'm facing exactly the same problem. Did you found any solution?

---

### Post by cneeper on 2022-08-23
Unfortunately, no. I spent a fair bit of time on this, but did *not* find a solution.

On my servers and in my use case, though, bonded NICs are just a luxury and not a necessity. In fact, after not finding a solution, I ended up shifting my perspective a bit and re-assigned the NICs in a way that works well for my use case, albeit without the redundancy.

I hope you find a solution that works for your own needs.

---

### Post by cyclingrunning on 2022-08-24
Thank you for your feedback. It really seams not be possible to pass vlan taggs on bonded interfaces to VMs.
I finally solved that by switching back from netplan to /etc/network/interfaces.

---

