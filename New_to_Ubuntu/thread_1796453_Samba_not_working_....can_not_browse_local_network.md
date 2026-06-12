---
title: "Samba not working ....can not browse local networks"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by perro68 on 2011-07-03
I am having a problem setting up a samba server so i can share a folder across my home network

When i set up the configuration file i set 3 folders to share

and when looking at the folder the icon indicates they are shared

How ever when i open dolphin > network > samba shares > 

i get the following msg "unable to find any workgroups in your local network. This might be caused by an enabled firewall"

How ever when i open dolphin > network > i see each machine on the network

but when i click on the samba server i do not see any of the shares i set up

This is the case even when using dolphin on the samba server


CAN SOMEONE PLEASE HELP ME WITH THIS

i have no idea how to resolve this issue

PLEASE HELP

---

### Post by perro68 on 2011-07-03
I am not using network manager ...i uninstalled it  and installed wicd

not sure if that is relevant or not

---

### Post by perro68 on 2011-07-04
I take it i will not get any assistance here

---

### Post by rosencrantz on 2011-07-04
If you have a working internet connection, using wicd shouldn't be the problem. Can you post your samba config file and the output of sudo iptables -L to clarify your problem?
BTW, 'bump' is a more neutral way to bump up your thread ;-)

---

