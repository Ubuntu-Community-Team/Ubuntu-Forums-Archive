---
title: "Gets IP from DHCP, but cannot ping or connect to network"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by p_y2 on 2013-10-01
Hello!

I have been using Ubuntu 12.04 on my laptop since a long time and connected to many wired and wireless networks. But since I moved to a new place, I cannot connect to their office network.
The connection is wired ethernet. IPs and DNS are dynamically provided by the DHCP. From the other Windows and Linux machines, people can swiftly connect to the network, use intranet or Internet, or ping each other. But from my Ubuntu, I cannot do any network related work.

When I connect to the network, I can get IP easily from the DHCP server. But I cannot ping the gateway, other computers on the same network or any public IP on the Internet.
I am veteran with networking on linux, and hence know what IP should be there and what should be the respective gateway, and I know all of them are right, but I cannot connect to the Internet.

I can get IPs from DHCP, means there is connection. But other than getting the IPs, the connection gets dumb.

Has anyone faced a similar problem on Ubuntu 12.04?

---

### Post by The Cog on 2013-10-01
No. What you describe is not normal.

I would be inclined to investigate why you cannot ping other devices on the same network first - fixing that might fix everything. 
Please can you try to ping some other host on the same network for a short while, then capture the output of these commands:
```
ifconfig
route -n
arp -n
```

It might also be interesting to see the packets, so if you can run this command in one terminal and then try the ping in another terminal:
```
sudo tcpdump -n -p
```

and we'll wee what we can figure out from that lot.

---

