---
title: "Multi-homed network question"
date: 2019-06-02
forum: Networking &amp; Wireless
---

### Post by markosjal on 2019-06-02
I have Lubuntu 16.04 based system very customized. 

I have a question about networking and seems there is no clear info

First:

I have a machine that must connect to two networks.

eth1 is wired ethernet with International's access.
wlan2 is Wifi that connects to a scanner direct . The scanners DHCP server MUST assign the IP address or the scanner will not work It can NOT use a fixed IP. (THIS IS THE WAY THIS SCANNER WORKS IT CAN NOT BE CHANGED!)

This scanner is shared over the network with other machines by way of a custom app, over eth1.

wlan2 is not always connected. In fact the scanner will turn itself off after a few minutes.



Sometimes when I turn on the scanner and the wifi connects to it, I lose internet access. 

Interestingly enough I had another machine running ubuntu 16.04 and never had this issue when it was used as the scanner host.  I do not have the network configuration from that machine.


I have tried assigning fixed IP and google DNS to the eth1 , that seems to make no difference. 


Now in network settings I see that I can use DHCP addresses only on the wlan2 but I still have the issue. 

Any suggestions?

---

### Post by TheFu on 2019-06-02
routing table?

---

