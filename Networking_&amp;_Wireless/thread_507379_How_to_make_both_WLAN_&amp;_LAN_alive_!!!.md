---
title: "How to make both WLAN &amp; LAN alive !!!"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by ducminh.mr on 2007-07-22
hi all,

I have a problem. could anyone can share some thing for me.
In my office, there are WLAN and LAN.
My labtop connect to both above connections.
But if I unplug the LAN connection, I can connect to internet through WLAN.
if plug the LAN, cannot connect to Internet.

So How to both connect to internet through WLAN and connect to other PCs in the LAN network???
anyone help me.

Thanks.

---

### Post by PaulFr on 2007-07-23
Are you able to connect to the Internet from any other PC on the LAN ? Or is it that the systems on the LAN cannot connect to the Internet at all ?

One possibility if the answer to the second question is yes: The problem could be in your default router configuration. This is what I think could be happening:

1. When you connect to the WLAN, the DHCP for that interface gives you a gateway and a default route.
2. When you subsequently connect to the LAN, the DHCP for the LAN interface must now be giving you another gateway and a default route.
3. This second default route causes all packets bound for the Internet to now go out the LAN interface.

To verify if this is what is happening, use the command ```
netstat -rn
``` when you only have the WLAN interface connected, and again after you connect the Ethernet interface, and see the entry for 0.0.0.0 (default) - if that has changed, this is the problem.

Hope this helps.

---

### Post by ducminh.mr on 2007-07-23
thanks for the reply,

actually, it is little bit complicated.
The Wirelesss Access Point use HDCP, and when I connect to, my laptio is allocated by one IP address. (192.168.0.11, default gateway is 192.168.0.1)

The LAN connection use static IP, and cannot connect to internet via this connection. (10.0.0.10)
The IP address of both connections is not changed where plug/unplug from Laptop.

My expectation is:
when the browse connect to the internet, it will use the Wireless connection.
And when I access other PCs on LAN, it will use LAN connection.

but when I use both connection, only LAN can use. I cannot access internet via WLAN.

HELP me, how to direct the connections as i expected.
thanks

---

### Post by PaulFr on 2007-07-24
Please run the command **netstat -rn** in a terminal (from the Applications -> Accessories -> Terminal menu option) as suggested in my earlier post twice, once when only the WLAN is connected and once, when both the LAN and the WLAN are connected, and post the output here.

---

### Post by cacycleworks on 2007-07-24
This piques my curiosity as well. There are times I would like to do some network setup/testing via the wired LAN port on my laptop while connected to the network via wireless. Is there a way to configure Network Manager (or in my case KNetworkManager) to activate both interfaces?

( thinking out loud ) 
I could make another instance of network manager... knetworkmanager  --nofork ... then pick the manual configuration option to use KDE's network managing interface (which can't handle WPA for wireless) to set up the wired lan ...... Hmmmmmm. must remember this to try.
( /thinking -- too much smoke coming out of head, can't see monitor )

---

