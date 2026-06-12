---
title: "cannot surf the internet while connected to an openvpn network"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by dirac14 on 2008-11-01
Hello there. I 'm new in Ubuntu (i ve been using it for only one week) so please be patient with me. I am dealing with the following problem : I installed the kvpnc gui, configured my openvpn connection to my university and so i can succesfuly connect to that network (Note: i find it really difficult and annoying working in the terminal so i ve nothing to do with it!) . The problem is that whenever i m connected to the vpn network i cannot do anything in the internet (browsing, downloading etc).
Why does it happen and what can i do to fix this problem?

---

### Post by puppywhacker on 2008-11-01
The reason for loosing the network connection is that your the default route is overwritten when you open the VPN tunnel, So you will have to delete the default route and add a new route.

This is best done in a terminal. The command is "route"

---

### Post by dirac14 on 2008-11-01
Puppywhacker thank you for replying. But what exactly do i have to do?
Sorry for insisting but i 'm something less than a starter!

---

### Post by aris! on 2008-11-01
Sorry this is not the answer that you may expect but I thought you could help me since you have already connected to the net trough vpn.
I too want to establish a vpn connection with my university and to this end I use Kvpnc and openvpn. I have the configuration file the certificates needed but I dont seem to be able to put it together can you help?
I run ubuntu hardy.
The error I get from Kvpnc is  
error: OpenvpnManagementHandler: Got no greeting within 3 seconds from management interface, retrying.
when i try to run openvpn from the command line i get
tap dev not defined or somthing similar I cannot remeber now.
Please help.
Ah. Ubuntu user for 4 days only.

---

### Post by kevdog on 2008-11-01
Please post the exact error message if you can.

---

### Post by puppywhacker on 2008-11-02
Hi,

Aris, can you open a new topic? I don't know openvpn. 

The following works in windows in a similar fashion. This is about changing your routing tables on your PC. These changes are not persistant.

1. print your routing table before you connected to the VPN. The last line indicates your DEFAULT route.

```
jan@sneezy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.193.16.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         88.193.16.1     0.0.0.0         UG    100    0        0 eth0

```

So in this sample my default route goes over my ISP's router "88.193.16.1"

2. connect to the VPN and print the same again. You will see that your default gateway (0.0.0.0) has changed to the VPN's default gateway.

This means that all you internet traffic is now also going through the VPN connection, which doesn't work in your case.

3. remove the default route that the VPN created
```

ip route del default via 10.0.0.1 dev eth0

```

4. add the old default route from you internet provider
ip route add default via 88.193.16.1 dev eth0

5. check if your internet connection is working. 

Sometimes the DNS servers are changed by VPN's aswell. The following link goes to google, but doesn't need a DNS lookup.
[[http://66.249.91.99/]](http://66.249.91.99/])

goodluck!

---

### Post by Will Shackleton on 2010-04-24
In case anyone still has this problem, this shell script worked for me: (run as root)

```
#!/bin/bash

route del default

DG=`route -n | grep wlan0 | head -n 1 | awk '{print $2}'`
route add default gw $DG
```

This is a bit crude, but should work in most cases. Replace wlan0 with whichever interface you are using (probably eth0). Only tested with OpenVPN.

This script deletes the original default route, finds the gateway from another route entry, and sets it as the new default gateway.

Hope it works!

---

