---
title: "wireless up but cannot get to any site"
date: 2017-02-05
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2017-02-05
After reinstalling (clean) 16.04 my wireless connection on my laptop indicates it's connected, but I cannot get to any site.
Attached is the output from the wirless-info script.
The wireless worked fine before the reinstall and also works straight away when booting the LiveCD

---

### Post by lister171254 on 2017-02-06
If somebody can explain why the following worked I mark this post as solved.

I commented out all entries in /etc/network/interfaces, rebooted and now things work as expected, even to the extend that when I plug the ethernet cable in, it becomes the primary interface and vice versa.

Thanks

---

### Post by Hadaka on 2017-02-06
Hi, you currently have Network Manager managing your network.
```
##### network managers ##################
Installed:
    NetworkManager
```
Your /etc/network/interfaces file should only have these 2 lines when the network is managed by Network Manager
```
auto lo
iface lo inet loopback
```
The type of configuration you attempted is used only when Network Manager is deleted and you choose to manage
the network in the "Manual Method" you cannot have both. So this entry when removed, allowed Network Manager
to manage your connection as it is designed to do.
*Not correct
```
##### interfaces ########################
source /etc/network/interfaces.d/*
auto lo
iface lo inet loopback

auto enp5s0f2
iface enp5s0f2 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 208.67.222.222 208.67.220.220
```
Please use **Thread Tools**,upper right area of your thread to mark your thread solved.
Thanks.

---

### Post by lister171254 on 2017-02-06
Given that the Desktop iso never has the right options for my partition needs, I always install the server release and the install the Desktop over it.
I guess that's how I ended up with  /etc/network/interfaces as well as the Network Manager files in /etc/network/interface.d

In either case, I think it's a bug/oversight as the Network Manager installation should sort this out

---

### Post by kurt18947 on 2017-02-06
> **lister171254 said:**
> Given that the Desktop iso never has the right options for my partition needs, I always install the server release and the install the Desktop over it.
I guess that's how I ended up with  /etc/network/interfaces as well as the Network Manager files in /etc/network/interface.d

In either case, I think it's a bug/oversight as the Network Manager installation should sort this out

I've never used the server iso so don't know - The server .iso comes with NetworkManager? I'm a little surprised at that, I assumed anyone installing a server would want to configure the network to suit.

---

### Post by wildmanne39 on 2017-02-06
> **kurt18947 said:**
> I've never used the server iso so don't know - The server .iso comes with NetworkManager? I'm a little surprised at that, I assumed anyone installing a server would want to configure the network to suit.No the server .iso does not come with network manager, the OP states that they installed the desktop on the server install themselves.

---

### Post by Hadaka on 2017-02-07
Hi,  *If you want to set a manual static connection in Network Manager it is done in the
settings of IPv4..setting the Method to manual and adding your data ..see attached.
[ATTACH=CONFIG]273580[/ATTACH]

---

