---
title: "Bridge config in netplan does not come up  at boot"
date: 2019-07-11
forum: Networking &amp; Wireless
---

### Post by drg-sat on 2019-07-11
I had an ubuntu 18.04 working and decided to move it to a VM in Proxmmox.
 
Configuration includes a bridge, it was working fine in the previous system but it does not come up at boot in the Proxmox VM.
 
Here is my netplan config:
 
    ```
network:
        renderer: networkd
        ethernets:
                ens18:
                        dhcp4: false
                        addresses: [172.18.0.4/29]
                        gateway4: 172.18.0.1
                        nameservers:
                                addresses: [8.8.8.8]
                ens19:
                        dhcp4: false
                ens20:
                        dhcp4: false
                ens21:
                        dhcp4: false
        bridges:
                br0:
                        addresses: [10.0.0.1/16]
                        interfaces: [ens19, ens20, ens21]
                        gateway4: 10.0.0.1
                        dhcp4: false
        version: 2
```
 
When system is up I can run 
 
    netplan apply
 
and it works perfectly.
 
I have also tried as a temporal solution to use crontab to do this, 
 
    *@reboot netplan apply*
 
but it's not working either.
 
    *netplan --debug generate*
 
generates no error.
 
I've seen these messages in journalctl
[INDENT][I]Jul 11 10:20:49 kernel: br0: port 3(ens19) entered disabled state
Jul 11 10:20:49 kernel: br0: port 2(ens20) entered disabled state
Jul 11 10:20:49 kernel: br0: port 1(ens21) entered disabled state
Jul 11 10:20:49 systemd-networkd[643]: br0: Lost carrier
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 kernel: device ens19 left promiscuous mode
Jul 11 10:20:49 kernel: br0: port 3(ens19) entered disabled state
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 kernel: device ens20 left promiscuous mode
Jul 11 10:20:49 kernel: br0: port 2(ens20) entered disabled state
Jul 11 10:20:49 kernel: device ens21 left promiscuous mode
Jul 11 10:20:49 kernel: br0: port 1(ens21) entered disabled state
Jul 11 10:20:49 networkd-dispatcher[785]: WARNING:Unknown index 3 seen, reloading interface list
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 networkd-dispatcher[785]: WARNING:Unknown index 4 seen, reloading interface list
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 networkd-dispatcher[785]: WARNING:Unknown index 5 seen, reloading interface list
Jul 11 10:20:49 systemd-networkd[643]: ens19: Could not join netdev: No such device
Jul 11 10:20:49 systemd-networkd[643]: ens19: Failed
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-networkd[643]: ens20: Could not join netdev: No such device
Jul 11 10:20:49 systemd-networkd[643]: ens20: Failed
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-timesyncd[657]: Network configuration changed, trying to establish connection.
Jul 11 10:20:49 systemd-networkd[643]: ens21: Could not join netdev: No such device
Jul 11 10:20:49 systemd-networkd[643]: ens21: Failed[/I][/INDENT]
 
so I suspect interfaces are not ready when trying to create the bridge.
 
I've been looking for a way to execute the netplan apply after these interfaces are ready but haven't find how to. I believe the same service does both things.
 
Why is not applying configuration at startup?  I'm I loosing something? Is there an issue with Proxmox and Ubuntu bridge?

---

