---
title: "internet connection adsl problems"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by jos de vooght on 2008-06-16
dear anybody,

i enter this forum because i got two linux drive machines, one ubuntu and one with a sidux interface, the last one - due to random updates managed with fluxbox. 
In the beginning both machines were doing well in the automatic connection to the interenet. When we dummies tried to make a network, for sharing directories, we messed up the router??  now the sidux machine cannot find the router.... can somebody help me setting this up?
thnxs
jos

---

### Post by SpaceTeddy on 2008-06-16
what is a sudix machine ? i've never heard that. Nevertheless, if there is something like /etc/network/interfaces on that machine, please post it's content... that is where the network configuration should be held. 

Also, try running the dhclient on the machine with the appropriate network interface... example:
```
sudo dhclient eth0
```
if eth0 is your network interface.

hope it helps :)

---

