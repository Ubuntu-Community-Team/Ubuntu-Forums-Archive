---
title: "Networking problem, configuring interface, gigabit LAN"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by kavoura on 2008-06-21
I have two PCs running Ubuntu and I want to network them together. One PC is running Ubuntu 7.10 and one is running 8.04.

Each PC has the following:
100 Mbit/s ethernet interface, 1 Gbit/s ethernet interface.

The 100 Mbit/s interface on each is connected to an Internet router which is also a DHCP server, so they get the IP address from that. I have no problems accessing the Internet via those connections.

The 1 Gbit/s interface is connected to a gigabit hub, and each PC will set its own IP address within a suitable range.

From the System/Administration/Network Tools menu, I get a window with a drop down list of 3 interfaces, loopback and eth0 and eth1. 

On the 8.04 PC, eth0 is gigabit and currently no IP information is listed for it.
For eth1 there is the IP address it gets from the router and it has the Internet connection.

When I click on the Configure button to the right, I get the following error:

```
The interface does not exist
Check that it is the correct type and is correctly supported by your system.
```

I get this error message for both eth0 and eth1 interfaces on the 8.04 PC.

I have also used the gigabit interface for accessing the Internet and it worked perfectly, so I know that Ubuntu is able to use the gigabit interface.

On the Ubuntu 7.10 PC there is no problem with this.

However, I managed to set an IP address from System/Administration/Network.

I have set an IP address on each PC for the gigabit connection, one is 192.168.1.3 (7.10 PC) and the other is 192.168.1.6

But so far I cannot get a connection between the two PCs via gigabit. I also want to know how to disable file sharing and print sharing on the 100 Mbit/s interface, so that that slower interface is used for the Internet only, and the gigabit interface is used only for file sharing. So what do I do?

---

