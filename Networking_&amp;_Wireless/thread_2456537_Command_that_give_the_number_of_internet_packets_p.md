---
title: "Command that give the number of internet packets per port"
date: 2021-01-13
forum: Networking &amp; Wireless
---

### Post by Hans_van_Leeuwen on 2021-01-13
The command "netstat -i" give the number of internet packets that is send and received per network intertface.
netstat -i

 iface      MTU Met          RX-OK RX-ERR RX-DRP RX-OVR          TX-OK TX-ERR TX-DRP TX-OVR
ens160   1500     0  31452931          0     3982           0  19043725         0          0           0

 
The tool "iptraf" give the number of internet packets per interface  and per port.
This monitor show the number of internet packets send and received by  port 22 so by ssh en sftp and also by port 443 so by Samba.

 Is there a command that give the number of internet packets per port as simple output number that can be used in a bash script?

---

### Post by TheFu on 2021-01-13
ifconfig?  oops.  per port - I was thinking per network port, not per IP port. sorry.

---

