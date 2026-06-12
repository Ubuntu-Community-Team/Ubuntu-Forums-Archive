---
title: "Duplicate Default gateway"
date: 2020-12-28
forum: Networking &amp; Wireless
---

### Post by fulcrumfoxbat on 2020-12-28
Hi,

I have an issue with my Ubuntu 20.04.1 LTS , in that it has not internet connection.
I finally tracked this down to the default gateway.

>route


> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eno1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1
192.168.1.1     0.0.0.0         255.255.255.255 UH    100    0        0 eno1


I am seeing two default gateway entries.
 if I remove one of them 
>sudo ip route del default via 192.168.1.1 dev eno1

I am fine it all works I have internet access
If I reboot the server the deleted line comes back

But I now have to to this every time I start the server.

- where is the default lines coming from?

Does anyone know?
I have spent 4 days on this and it's driving me crazy. and it should be easy right?

Why is my delete gateway not being saved?
What process is put that "back" and is there a another file I i need to edit?

Thanks

---

### Post by TheFu on 2020-12-30
Deleting from the CLI doesn't save.  Adding from the CLI doesn't save either.

Which of the 5 different ways are you using to configure your network settings? Are you using network-manager, nm-cli, netplan or scripts to setup the IPs and routing?

Why have 2 IPs on the same interface on the same LAN? Generally, that isn't useful for most people.

---

