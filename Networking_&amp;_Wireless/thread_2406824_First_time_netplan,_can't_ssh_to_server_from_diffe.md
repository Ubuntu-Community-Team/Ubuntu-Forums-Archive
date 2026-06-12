---
title: "First time netplan, can't ssh to server from different subnet"
date: 2018-11-26
forum: Networking &amp; Wireless
---

### Post by jshurak on 2018-11-26
Morning,


This is my first time working with netplan.  I have a server on a lan subnet and wireless clients on a separate subnet.  There are no firewall rules between these subnets.  I can ssh fine within the lan subnet, but not from the wireless subnet. I can reach other machines on the lan from wireless, but not this one.  I'm not sure exactly what is going on here. I don't know if its something with my netplan file or some other configuration on 18.04.1.  Netmask is correct. Here is my netplan file



```
network:
    ethernets:
        eno1:
            addresses: [10.10.20.3/26]
            gateway4: 10.10.20.1
            nameservers:
                    addresses: [10.10.20.1]
            dhcp4: false

```

---

### Post by wyliecoyoteuk on 2018-11-26
Netplan yaml files are fussy about indentation etc.

try```
ip a
```
and
```
netplan --debug generate.
``````

```

---

### Post by jshurak on 2018-11-26
```
** (generate:13684): DEBUG: 16:13:07.463: Processing input file //etc/netplan/50-cloud-init.yaml..
** (generate:13684): DEBUG: 16:13:07.463: starting new processing pass
** (generate:13684): DEBUG: 16:13:07.463: eno1: setting default backend to 1
** (generate:13684): DEBUG: 16:13:07.463: Generating output files..
** (generate:13684): DEBUG: 16:13:07.463: NetworkManager: definition eno1 is not for us (backend 1)

```

---

### Post by wyliecoyoteuk on 2018-11-26
What is the output from
```
ip a
```

It may be as simple that your network card name is en01 (enzero1), not eno1

If not using cloud-init, our netplan yaml should ideally be /etc/netplan/01-netcfg.yaml

You might want to disable or even remove cloud-init, as detailed here:

[https://nucco.org/2018/05/ubuntu-18-04-chronicles-removing-cloud-init.html](https://nucco.org/2018/05/ubuntu-18-04-chronicles-removing-cloud-init.html)

This is an example yaml file, indentation is important.

```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    en01:
      dhcp4: no
      dhcp6: no
      addresses: [10.10.20.3/26]
      gateway4: 10.10.20.1
      nameservers:
         addresses: [10.10.20.1/26]
```

---

### Post by wyliecoyoteuk on 2018-11-26
examples here

[https://netplan.io/examples](https://netplan.io/examples)

---

### Post by jshurak on 2018-11-26
thanks. There doesn't seem to be an issue with formatting...at least, I'm not getting any messages when applying netplan. Here is the output from ip a

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether d4:ae:52:c4:87:ac brd ff:ff:ff:ff:ff:ff
    inet 10.10.20.3/26 brd 10.10.20.63 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::d6ae:52ff:fec4:87ac/64 scope link

```

---

### Post by wyliecoyoteuk on 2018-11-26
Well, that looks like the NIC is up and running, has an IP address,etc.
Can you ping it?

---

### Post by jshurak on 2018-11-26
I can ping both the opposite gateway from either subnet.  I can ping hosts from each subnet to each other, just not this server.

---

### Post by wyliecoyoteuk on 2018-11-26
Have you tried a traceroute?

---

### Post by jshurak on 2018-11-26
Hi thanks, its all local, so I don't expect traceroute to show much.  This machine does dual boot.....and I use the same IP address. I wonder if that has something to do with it.  I would expect a host warning, but not a total lack of communication.  I will try re-assigning its IP to be unique and go from there.

---

### Post by jshurak on 2018-11-26
So, I ended up reinstalling the OS and manually setting the static IP during installation. Everything is working fine now.

---

### Post by xubuntu84 on 2018-11-27
Can you share the yaml that was created by the installer? I'm curious what was different.

---

