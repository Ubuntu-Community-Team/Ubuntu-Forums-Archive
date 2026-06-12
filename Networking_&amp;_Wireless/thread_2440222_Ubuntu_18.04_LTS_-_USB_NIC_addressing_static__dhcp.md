---
title: "Ubuntu 18.04 LTS - USB NIC addressing static / dhcp simultaneously"
date: 2020-04-07
forum: Networking &amp; Wireless
---

### Post by ch33zw1z on 2020-04-07
Quick Background:
- Laptop to serve as pihole server for two separate VLANS that are isolated
- Older laptop running Ubuntu 18.04
- Onboard NIC: enp5s0 - no issues
- USB NIC: enx001060315e39 - Two IP's assigned. I want a static IP or 10.0.86.32, and the DHCP address it picked up needs to go away.

When I first boot, the network config looks like this, and both the 10.0.86 IP's are pinging.
```
:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 88:ae:1d:13:4b:7d brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.32/24 brd 192.168.1.255 scope global enp5s0
       valid_lft forever preferred_lft forever
    inet6 fe80::8aae:1dff:fe13:4b7d/64 scope link
       valid_lft forever preferred_lft forever
3: enx001060315e39: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:10:60:31:5e:39 brd ff:ff:ff:ff:ff:ff
    inet 10.0.86.32/24 brd 10.0.86.255 scope global enx001060315e39
       valid_lft forever preferred_lft forever
    inet 10.0.86.10/24 brd 10.0.86.255 scope global secondary enx001060315e39
       valid_lft forever preferred_lft forever
    inet6 fe80::210:60ff:fe31:5e39/64 scope link
       valid_lft forever preferred_lft forever
4: wlp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether c4:46:19:22:53:2f brd ff:ff:ff:ff:ff:ff

```

Netplan looks like this:
```
 cat 50-cloud-init.yaml
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        enp5s0:
            addresses:
            - 192.168.1.32/24
            gateway4: 192.168.1.1
            nameservers:
                addresses: [192.168.1.32, 192.168.1.31]
        enx001060315e39:
            addresses:
            - 10.0.86.32/24
            gateway4: 10.0.86.1
            nameservers:
                addresses: [10.0.86.32, 10.0.86.1]

# version: 2

```

I noticed the verbiage at the to of the .yaml file, but not quite sure I want to do that..figured I'd ask here

If I run the command: sudo netplan apply, that clears up the dual IP problem, but 10.0.86.32 also stops working.

I've dug thru these links this morning, but can't quite figure out where I'm going wrong

[https://netplan.io/troubleshooting](https://netplan.io/troubleshooting)

[https://netplan.io/troubleshooting#debugging-issues-with-the-networkd-backend](https://netplan.io/troubleshooting#debugging-issues-with-the-networkd-backend)


Any guidance is appreciated...

---

### Post by ch33zw1z on 2020-04-08
I reloaded the same version ubuntu on a different laptop with the USB NIC installed. I configured it manually. After install completed, the laptop rebooted, showed the NIC's as intended. When I plugged in the ethernet cable to the USB NIC, the same behavior. Somewhere, the DHCP service is being told to apply to this USB NIC. If I run 'sudo netplan apply', I see the same behavior. The DHCP IP disappears from the adapter, but the interface stops working (while still showing only the static IP)

And the onboard NIC, which had it's cable attached the entire install, is working just fine.

---

### Post by ch33zw1z on 2020-04-10
Update: It appears to be the installation of pihole adds a dhcp service that gets confused when multiple NIC's are present. This isn't an Ubuntu issue at this point.

---

