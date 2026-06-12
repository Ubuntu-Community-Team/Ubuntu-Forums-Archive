---
title: "netplan does not configure static IP address (any more)."
date: 2021-10-29
forum: Networking &amp; Wireless
---

### Post by rozaki777 on 2021-10-29
I have been using netplan to configure a static IP address. The purpose is to use some web camera (has a fixed IP address) system. 
The file (/etc/netplan/99-static-ip.yaml) for netplan is as follows:

```
network:
        version: 2
        renderer: networkd
        ethernets:
                enp61s0:
                        dhcp4: false
                        dhcp6: false
                        accept-ra: false
                        addresses: [192.168.222.100/24]
                        mtu: 9000

```

Today, I found my machine cannot connect to the camera. Before, ping 192.168.222.10 (which is the IP address of the camera) worked, but now looses 100% of packets. 
I did 'sudo netplan apply' and even rebooted. Nothing changed, ping does not go through.


The result of 'sudo netplan --debug apply' was:

```

 sudo netplan --debug apply
** (generate:100231): DEBUG: 15:39:52.194: Processing input file /etc/netplan/01-network-manager-all.yaml..
** (generate:100231): DEBUG: 15:39:52.194: starting new processing pass
** (generate:100231): DEBUG: 15:39:52.194: Processing input file /etc/netplan/99-static-ip.yaml..
** (generate:100231): DEBUG: 15:39:52.194: starting new processing pass
** (generate:100231): DEBUG: 15:39:52.194: We have some netdefs, pass them through a final round of validation
** (generate:100231): DEBUG: 15:39:52.194: enp61s0: setting default backend to 1
** (generate:100231): DEBUG: 15:39:52.194: Configuration is valid
** (generate:100231): DEBUG: 15:39:52.194: Generating output files..
** (generate:100231): DEBUG: 15:39:52.194: openvswitch: definition enp61s0 is not for us (backend 1)
** (generate:100231): DEBUG: 15:39:52.194: NetworkManager: definition enp61s0 is not for us (backend 1)
(generate:100231): GLib-DEBUG: 15:39:52.194: posix_spawn avoided (fd close requested) 
(generate:100231): GLib-DEBUG: 15:39:52.196: posix_spawn avoided (fd close requested) 
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:enp61s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp61s0:
      accept-ra: false
      addresses:
      - 192.168.222.100/24
      dhcp4: false
      dhcp6: false
      mtu: 9000
  renderer: networkd
  version: 2


DEBUG:no netplan generated NM configuration exists
DEBUG:enp61s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp61s0:
      accept-ra: false
      addresses:
      - 192.168.222.100/24
      dhcp4: false
      dhcp6: false
      mtu: 9000
  renderer: networkd
  version: 2


DEBUG:Link changes: {}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp61s0
DEBUG:netplan triggering .link rules for wlp62s0
DEBUG:enp61s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp61s0:
      accept-ra: false
      addresses:
      - 192.168.222.100/24
      dhcp4: false
      dhcp6: false
      mtu: 9000
  renderer: networkd
  version: 2

```

Any good idea to work-around this trouble? 
I use Ubuntu 20.04.3 LTS on Alienware m15 R4. 
Kernel version is 5.9.10-050910-generic.

---

### Post by TheFu on 2021-10-29
And the routing table?
Also, if there isn't a router in this subnet, you'll want to set the "gateway" to be the other device.

---

### Post by chili555 on 2021-10-30
> DEBUG: 15:39:52.194: NetworkManager: definition enp61s0 is not for us (backend 1)Netplan says Network Manager is in charge. That is where I'd set the static IP address, not netplan.

---

