---
title: "LACP on ubuntu 17 not working"
date: 2017-10-02
forum: Networking &amp; Wireless
---

### Post by afmiller on 2017-10-02
Hello, I've been having issues trying to set up LACP on my ubuntu 17 machine. I've added the bonding to the modules file as well done modprobe bonding. Below is my current interface file set up.

#nic 1
auto enp5s0f0
iface enp5s0f0 inet manual

#nic 2
auto enp5s0f1
iface enp5s0f1 inet manual

#bond
auto bond0
iface bond0 inet static 
 address x.x.x.x
 netmask x.x.x.x
 gateway x.x.x.x
slaves enp5s0f0 enp5s0f1

Ive tried to comment out the nic lines like some tutorials show with no luck. When I do an ifcong, it does show bond0 being there with no IP address. I have a Norte switch that has already been configured for LACP as I am switching from free NAS to a custom set up using ubuntu. Any help would be greatly appreciated as I've tried multiple tutorials with each one being different and no luck.

nrian

---

