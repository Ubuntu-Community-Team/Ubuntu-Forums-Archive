---
title: "Bonding in ubuntu 20.04"
date: 2020-06-03
forum: Networking &amp; Wireless
---

### Post by nick-kostov on 2020-06-03
Hello everyone.
In order to create (networking teaming) bonding in ubuntu I have implemented the following:
As you can see I am using an IP and the DHCP option.

```
auto eno1
iface eno1 inet manual
    bond-master bond0
    bond-primary eno1
auto eno2
iface eno2 inet manual
    bond-master bond0

auto bond0
iface bond0 inet dhcp
    address 192.168.100.84
    gateway 192.168.100.255
    netmask 255.255.255.0
    bond-mode active-backup
    bond-miimon 100
    bond-slaves none    
```    



Since its a local network I did not expect the following to be a trouble:
dhcp to be set to static.
Once doing it I found out that I constantly suffer from dropping packets and can not even do sudo apt update.

This is the only way it worked out for me. 

If you have any suggestions on the matter I will be glad to hear you out guys.

---

