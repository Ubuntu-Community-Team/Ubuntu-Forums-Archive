---
title: "Issue with bonding, no internet"
date: 2016-08-23
forum: Networking &amp; Wireless
---

### Post by sm_ashiq on 2016-08-23
I tried to bond broadband wifi with 4g mobile usb tethering in my **ubuntu 16.04** system. 

  I configured /etc/network/interfaces as below 
  

#primary network interface
auto wlp5s0
iface wlp5s0 inet manual
bond-master bond0
bond-primary wlp5s0

#the second network interface
auto enp0s29u1u1
iface enp0s29u1u1 inet manual
bond-master bond0

#bond0 configuration
auto bond0
iface bond0 inet dhcp
bond-mode 6
bond-miimon 100
bond-lacp-rate 1
bond-slaves wlp5s0 enp0s29u1u1

  
I also tried [I]iface bond0 inet static

[/I]but I am not getting Internet. when i ping 8.8.8.8, I get reply **"Destination Host Unreachable"**
  
Please help me to solve the issue.

---

