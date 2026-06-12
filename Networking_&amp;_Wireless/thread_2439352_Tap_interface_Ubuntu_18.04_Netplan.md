---
title: "Tap interface Ubuntu 18.04 Netplan"
date: 2020-03-26
forum: Networking &amp; Wireless
---

### Post by rudl2 on 2020-03-26
I am using Ubuntu 18.04 LTS as OS for an industrial control. (PLC) On my machine, I have two network cards. One network card is for programming, the other for the communication with my drives. (EtherCAT) To configure my drives there is also an ethernet communication over EtherCAT. (EoE)
This only as introduction.
My Problem is: I need a tap interface.
I did the following configuration in netplan:

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp1s0:
   dhcp4: true
   optional: true
  enp0s31f6:
   dhcp4: true
   optional: true
 bridges:
  br0:
   dhcp4: true
   dhcp6: false
   addresses: [[192.168.100.100/24]("http://192.168.100.100/24")]
   interfaces: [enp0s31f6]
```

When I enable the tap interface:
```
sudo ip tuntap add tap0 mode tap
 sudo ip link set tap0 up

```

And connect it to my bridge interface:
```
  sudo brctl addif br0 tap0.
  
```

I can connect from enp0s31f6 to the drives over EoE.

The problem is after a restart the configuration of the tap interface is gone and Netplan does not support tap interfaces anymore.

Of corse I could write a script that executes the code above at startup. But I am searching the proper way.

I am thankful for every hint! :p

---

### Post by cclaunch on 2020-05-12
Hi, I am also trying to get EoE going in 18.04, however we're not using netplan.  Would you mind giving any further details on how you got the eoe connected to the tap?  I don't see where you actually bridged the drive.  My task is to figure out a way to automate this as well so hopefully we can help each other.

---

