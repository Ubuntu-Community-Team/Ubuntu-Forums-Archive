---
title: "Issue with static IP"
date: 2016-10-13
forum: Networking &amp; Wireless
---

### Post by juillard on 2016-10-13
Hello I am running ubuntu v16.0.4.1 Workstation and am having some issues setting a static IP. 
The machine itself is running on a VM on Vmware Workstation 12, I am using the same network settings as other VMs that I can reach just fine, however I cannot reach the Ubuntu VM via Ping. The Ubuntu VM can also not ping the host machine or other things on my network. 

I first tried setting the IP statically from the network manager in the GUI however this did not work. 

Below are the settings I used: 
Address:172.24.28.49 Netmask 255.255.254.0 Gateway 172.24.28.1 DNS 172.22.0.3
I stopped and restarted the network adapter however I couldn't reach anything on the network. 

I then edited the network config file under at /etc/network/interfaces

Below is what my file looked like:
 
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


auto ens33
iface ens33 inet static
address 172.24.28.49
netmask 255.255.254.0
gateway 172.24.28.1
dns-nameserver 172.22.0.3

However, when I use this file and do a print of my routes, the table is shows as below: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.24.28.0     *               255.255.254.0   U     0      0        0 ens33


I'm not extremely familar with linux but is there a flag or something I am missing in this file that will cause it to automatically add this route? 
If you need anything else I would be happy to provide it to you.

---

