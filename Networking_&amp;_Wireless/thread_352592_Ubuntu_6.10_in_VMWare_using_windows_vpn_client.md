---
title: "Ubuntu 6.10 in VMWare using windows vpn client"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by jpick_21 on 2007-02-03
I am trying to setup a dev box from home and need some help.  The VPN we use at work only has a windows client, so I am running vmware on my home xp box with an ubuntu vm.  The vm is set to use NAT and can access machines by ip across the vpn running in my windows machine.  My only problem is that dns is not working from the vm.  

Does anyone know how I could fix this issue?

---

### Post by kd7swh on 2007-02-03
try using dnstop to see if there is any dns traffic at all. 

on another note vpnc is a great linux vpn client its free and in the repos.

---

