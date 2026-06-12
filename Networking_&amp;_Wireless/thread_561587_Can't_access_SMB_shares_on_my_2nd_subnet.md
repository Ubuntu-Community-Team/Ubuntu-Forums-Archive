---
title: "Can't access SMB shares on my 2nd subnet"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by gardener on 2007-09-27
Okay this should be a simple problem. Here is the topology

Internet ---> D-Link 524 Wireless router - - - (wlan0) Ubuntu Server Feisty (eth1) ---SWITCH-- Client 1 
                           |                                                                                                                |
                           |                                                                                                                |
                       XBOX Media Center                                                                                 Client 2


D-524: 192.168.0.1 DHCP enabled (.23-50)

Ubuntu Server wlan0: 192.168.0.24 
                         eth1: 192.168.1.1

The Ubuntu server doesn't like to bridge with my RT73 (DWL-G122) so I am using DHCP3 and iptables to create a separate NAT'd subnet

I was able to forward my Azureus port through the Dlink, and I have all the ports OPEN on the Ubuntu server. Open and forwarded (It's all already firewalled on the Dlink) I have tried adding forwarding rules for port 445 to iptables (which seems odd, shouldn't it forward EVERYTHING right now?) and it didn't work. There's a reason for this madness too, I didn't list all the devices wired or wirelessly connected to the dlink but it shouldn't matter.

Help! please! TIA!

Any suggestions? I can browse/transfer via Windows File Sharing between Client 1 and Client 2.

---

