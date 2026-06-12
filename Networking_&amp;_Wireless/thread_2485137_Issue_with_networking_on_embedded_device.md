---
title: "Issue with networking on embedded device"
date: 2023-03-20
forum: Networking &amp; Wireless
---

### Post by reachrobotics on 2023-03-20
Hi Community

I'm having some issues with an embedded linux device and I was hoping I could get some insight posting on here. 

So far, my embedded devices have been running Ubuntu 18.04, but I have recently updated to 20.04, and have now encountered some networking issues. 


In terms of environment/setup, I have a local (isolated from the office) network the embedded device is on with an access point for my laptop. The access point is a GL-AR750S on IP address 192.168.1.1.  There are four other (static IP) devices on this network that I can access (IPv4 Addresses: 192.168.1.201, 192.168.1.202, 192.168.1.203, 192.168.1.204) while my embedded device (192.168.1.236) is not responding to network requests. 

Previously, on the Ubuntu 18.04 devices, this same connection worked, and I set static IP using the following interfaces file. 
Under /etc/network/interfaces.d/eth0 


```
auto eth0


iface eth0 inet static
address 192.168.1.236
netmask 255.255.255.0
gateway 192.168.0.1

```

However, this approach does not work in Ubuntu 20.04. 
So I installed netplan and placed the following yaml file under /etc/netplan/networkConfig.yaml.
However this didn't fix the issue. However I still can't ping anything else on this isolated network from the embedded device. Nor can I ping the embedded device from my laptop. 
 


```
network:
    version: 2
    renderer: NetworkManager
    ethernets:
        eth0:
            dhcp4: no
            addresses: [192.168.1.236/16]
            nameservers:
                addresses: [192.198.1.0, 192.168.1.1, 8.8.8.8]
            routes:
            - to: default
              via: 192.168.1.0

```

This is the output of nmcli
```


eth0: connected to netplan-eth0
        "eth0"
        ethernet (nvethernet), 48:B0:2D:76:36:3F, hw, mtu 1500
        ip4 default
        inet4 192.168.1.236/16
        route4 192.168.0.0/16
        route4 0.0.0.0/0
        inet6 fe80::4ab0:2dff:fe76:363f/64
        route6 fe80::/64

```


This is the output of route -n
[TABLE="width: 500"]
[TR]
[TD]Destination[/TD]
[TD]Gateway[/TD]
[TD]Genmask[/TD]
[TD]Flags[/TD]
[TD]Metric[/TD]
[TD]Iface[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]0.0.0.0[/TD]
[TD]192.168.1.0[/TD]
[TD]0.0.0.0[/TD]
[TD]UG[/TD]
[TD]20100[/TD]
[TD]eth0[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]169.254.0.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.0.0[/TD]
[TD]U[/TD]
[TD]1000[/TD]
[TD]docker0[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]172.17.0.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.0.0[/TD]
[TD]U[/TD]
[TD]0[/TD]
[TD]docker0[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]192.168.0.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.0.0[/TD]
[TD]U[/TD]
[TD]100[/TD]
[TD]eth0[/TD]
[TD][/TD]
[/TR]
[/TABLE]


 I have access to all the hardware for this problem, and I have tried substituting an older embedded device with Ubuntu 18.04 on it, which I can successfully ssh into and it can ping each device on the isolated network. The only difference between these devices is operating system version. This has me really confused so I'd appreciate any help at all

Thanks

---

### Post by chili555 on 2023-03-21
> renderer: NetworkManagerIs Network Manager running on this embedded device? Is there a desktop GUI environment?

Please see: ```
cat /usr/share/doc/netplan/examples/static.yaml
```I suspect that you want:

```
renderer: networkd
```Your spacing, indentation, etc. appear wrong; perhaps that is the result of posting it here.

Does this tell us anything interesting?

```
sudo netplan --debug apply
```

---

