---
title: "Vpnc (cisco VPN client) routeing problem"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by giliredbaron on 2008-02-14
Hi all,

I have Ubuntu 6.06 server and I'm trying to connect to remote cisco using vpnc. 
From Windows I can ping my host when I connect to the VPN. this is because the windows client makes some routings.
This is my vpnc.conf on the Ubuntu 
```
Interface name tun3
IPSec gateway 217.*.*.*
IPSec ID VPNtest
IPSec secret #####
Xauth username myuser
Xauth password mypass
Target networks 10.X.X.99/32
DNSUpdate no

``` 

In my windows I get this IP: 10.201.11.1 whit 10.201.11.2 as default GW.
On my Linux some times I get 10.201.11.1 and some time I get 10.201.11.2. 
When I get 10.201.11.1 and I add a route to 10.201.11.2 so it can be the default GW, the Linux complains about "Network is unreachable"... So I add this route :
route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.201.11.1 dev tun3
and then I can add the route.
But I can't ping my server or connect to it.

Any ideas?
Gili

---

### Post by schwieb on 2008-02-14
Hello,  
You may need to force vpnc to use a UDP connection rather than TCP.  You can do this either in the config file or the command line.

At the command line try:
```
sudo vpnc --natt-mode cisco-udp yourconfigfilename 
```

Add this command to a line in your config file for a permanent solution:
```
NAT Traversal Mode cisco-udp
```

Hope that works for you!

---

