---
title: "No Internet Connection on Ubuntu server after kernel update."
date: 2024-08-13
forum: Networking &amp; Wireless
---

### Post by thoreee on 2024-08-13
[COLOR=#0C0D0E][FONT=-apple-system]I have done an update via sudo apt get update && sudo apt upgrade. I upgraded to Ubuntu 22.04.4 LTS.
Also, I have upgraded the Kernel to GNU/Linux 6.5.0-1027-oracle aarch64.
After the update, I wasn't able to access the Instance via SSH. I can only access the instance via cloud console.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I don't know much about networking and have no idea how I can restore Internet access.
I have googled a bit and done these things:[/FONT][/COLOR]
ping 1.1.1.1
```
ping: connect: Network is unreachable
```

dig askubuntu.com @1.1.1.1
```
;; UDP setup with 1.1.1.1#53(1.1.1.1) for askubuntu.com failed: network unreachable.
;; no servers could be reached

;; UDP setup with 1.1.1.1#53(1.1.1.1) for askubuntu.com failed: network unreachable.
;; no servers could be reached

;; UDP setup with 1.1.1.1#53(1.1.1.1) for askubuntu.com failed: network unreachable.
;; no servers could be reached
```

[COLOR=#0C0D0E][FONT=-apple-system]ip addr gives me the following output:[/FONT][/COLOR]
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 02:00:17:00:e1:21 brd ff:ff:ff:ff:ff:ff
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.8.0.1/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::7e95:61d8:aa77:ad19/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:16:0b:c5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
```


[COLOR=#0C0D0E][FONT=-apple-system]The Output of cat /etc/netplan/*.yaml:[/FONT][/COLOR]
```
network:
version: 2
renderer: networkd
ethernets:
    enp0s3:
        dhcp4: true
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    ethernets:
        enp0s3:
            dhcp4: true
            match:
                macaddress: 02:00:17:00:e1:21
            set-name: enp0s3
[COLOR=#0C0D0E][FONT=-apple-system]sudo lshw -C network:[/FONT][/COLOR]
*-network                 
       description: Ethernet controller
       product: Virtio network device
       vendor: Red Hat, Inc.
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: msix bus_master cap_list
       configuration: driver=virtio-pci latency=0
       resources: iomemory:800-7ff irq:48 memory:13001000-13001fff memory:8003008000-800300bfff
     *-virtio1 DISABLED
          description: Ethernet interface
          physical id: 0
          bus info: virtio@1
          logical name: enp0s3
          serial: 02:00:17:00:e1:21
          capabilities: ethernet physical
          configuration: autonegotiation=off broadcast=yes driver=virtio_net driverversion=1.0.0 link=no multicast=yes
```


[COLOR=#0C0D0E][FONT=-apple-system]sudo cat /etc/network/interfaces:[/FONT][/COLOR]
```
cat: /etc/network/interfaces: No such file or directory

```[COLOR=#0C0D0E][FONT=-apple-system]Has anyone an idea what I could do? Tank you very much![/FONT][/COLOR]

---

### Post by TheFu on 2024-08-13
Your yaml file appears to be corrupted.  Fix that.

As a guess, it looks like the top 6 lines are repeated. Don't do that.  If you just miscopied the file contents when posting here, then I have no idea.

If you can't ping 1.1.1.1, you don't have any internet, so any internet related commands won't work (like dig).

---

