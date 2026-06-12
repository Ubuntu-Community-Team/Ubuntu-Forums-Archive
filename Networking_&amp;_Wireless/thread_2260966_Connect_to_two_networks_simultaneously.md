---
title: "Connect to two networks simultaneously"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by Sivakumar_Nataraja on 2015-01-15
I want to connect to two networks simultaneously using the Ethernet and in-built WiFi or to two WiFi networks by installing an additional WiFi adapter.


My requirement: I have two sets of devices (Group A and group B) that need to communicate with each other but not directly. There is no internet at the location. Group A devices are connected to WiFi router A and group B devices to WiFi router B (It is necessary that they should not be connected to the same router). I want the Ubuntu device to connect to both router A and router B and act as an intermediary between the two groups. The Ubuntu device should receive messages from Group A (through router A), process the information and send notification of the result to Group B (through router B) and vice versa.


Questions:


[LIST=1]
[*]How do I setup Ubuntu to connect to two networks simultaneously?
[*]How do I identify which network a message is from and handle that message accordingly?
[*]How do I specify the target network for my notification and send it to that network?
[/LIST]


Thanks.

---

### Post by newbie-user on 2015-01-15
I assume the Ubuntu box has dual NICs. You can make Ubuntu into a router:

1. Disable the routing functions on the wifi routers and use them as access points only.
2. enable IP forwarding in Ubuntu by uncommenting the following line in /etc/sysctl.conf
[INDENT]*#net.ipv4.ip_forward=1*[/INDENT]
3. add nat masquerading to iptables by passing the command:
[INDENT]*iptables -A POSTROUTING -t nat -j MASQUERADE*[/INDENT]
4. set up routing tables for the clients

If you want, you can also set up DHCP service on Ubuntu which services both networks, also DNS or whatever other network service you need.

---

