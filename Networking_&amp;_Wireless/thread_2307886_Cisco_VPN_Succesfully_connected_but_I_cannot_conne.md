---
title: "Cisco VPN: Succesfully connected but I cannot connect through RDP"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by Liselot_Wolters on 2015-12-29
Hi,

I'm quite new to Linux and Ubuntu. I have tried to connect to my work-pc using Cisco-VPN and RDP (Remmina).  I get this message: VPN-connection is successfully established. But I cannot connect to my work-pc by RDP and I also cannot ping its IP-adress. I've searched the internet and found that I had to manually add the IP-adress, subnetmask and gateway of my work-pc to the IPv4-routes of the VPN-configuration and check the box before 'Use this connection only for resources ...'. I did and it worked. But today I tried again to connect and have the same problem as before. The VPN-connection seems to be successfull, but I cannot ping the IP-adress of my work-pc and cannot connect with RDP. I don't know what else to do.
My work-pc (Windows 7) is configured to enable RDP. Previously, I used my MacBook to connect and I've never had any problems.

I will appreciate your help.
Liselot

---

### Post by Liselot_Wolters on 2015-12-31
I sort of solved the problem. When I use the command terminal to make the VPNC-connection, it works well.

---

