---
title: "Ad-Hoc problem"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by fmpfmpf on 2008-05-20
i have 2 laptops and both have WLAN.
Laptop A has Ubuntu 7.10
Laptop B has Ubuntu 7.04

i am trying to link the 2 laptops using Ad-Hoc
Laptop A is the transmitter and B is the receiver

in A, i type "ifconfig eth2 10.10.10.1 netmask 255.255.255.0 broadcast 10.10.10.255 up"

B is now connected to "Test"
However, when i type "ping 10.10.10.254", it says:-
From xxx.xxx.x.xxx icmp_seq=2 Desination Host unreachable
From xxx.xxx.x.xxx icmp_seq=3 Desination Host unreachable
From xxx.xxx.x.xxx icmp_seq=4 Desination Host unreachable
and so on until i hot Ctrl + C

What is the problem?
pls help me

p/s :- i am used this website for instructions.
[http://www.wlug.org.nz/WirelessSetupNotes](http://www.wlug.org.nz/WirelessSetupNotes)

thank you

---

