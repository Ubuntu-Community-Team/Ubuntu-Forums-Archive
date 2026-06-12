---
title: "Ubuntu 18.04: Networking has stopped working on KVM guests."
date: 2018-05-08
forum: Networking &amp; Wireless
---

### Post by nbritton on 2018-05-08
The networking in my KVM guest VMs has stopped working. I attach the VMs to a bridge, any bridge, and then I try to ping another guest VM on the same bridge, or the hypervisor host, or the gateway and all I get is "Destination Host Unreachable". I can't ping any other host from within the VM. Networking was previously working just fine for the last two months and it just stopped working without notice. I've undefined the VMs and recreated them and still the same problem persists. I've tried rebooting. I've tried ripping out most of the netplan config. No dice. Short of tearing the whole system down and starting over I don't know what to do to fix this. I haven't made any changes to the physical network.

Below is my netplan config:
```

network:
  version: 2
  renderer: networkd


  ethernets:
    eno3: {}
    eno4: {}
    dummy1: {}
    dummy2: {}
    dummy3: {}
    dummy4: {}
    dummy5: {}
    dummy6: {}


  bonds:
    bond1:
      interfaces: [eno3, eno4]


  bridges:
    internet:
      interfaces: [bond1]
      addresses: [10.10.1.2/16]
      gateway4: 10.10.0.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
    vbridge1:
      interfaces: [dummy1]
      addresses: [10.100.0.2/24]
    vbridge2:
      interfaces: [dummy2]
    vbridge3:
      interfaces: [dummy3]
      addresses: [10.12.0.2/24]
    vbridge4:
      interfaces: [dummy4]
    vbridge5:
      interfaces: [dummy5]
      addresses: [10.13.0.2/24]
    vbridge6:
      interfaces: [dummy6]

```

---

