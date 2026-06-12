---
title: "PPTP VPN Connection to CISCO RV042 connecting but..."
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by nalasha79 on 2014-06-05
I have just installed Xubuntu **14.04** on a couple of candidate PCs, and I am connecting to a CISCO RV042 router via a PPTP connection. I have selected the options that appear to connect to the PPTP tunnel (after a few attempts :-?). When I use the network manager I have a tab for the connection, but the IP address is the same for the PPTP connection as for the Ethernet connection that is used to create the VPN connection. Connected but not able to traverse the network.

When I open a terminal and issue the ifconfig command I am given the PPTP Link encap with the correct IP address for the remote network. I verified this over the remote management of the router via the Internet, and the remote router also shows the connection as active. I do not know how to contact the remote VPN network devices...

Ping -c 4 [ip address] will not bounce a response from anything on the VPN connection. I can ping on the local side of the connection. I am trying to reach an RDP session via PPTP VPN to the remote router (as my goal) using the Remmina app, but obviously I cannot get far under these circumstances. I am new to Ubuntu and I am running the Xubuntu "variant" "interface".. not sure how to call it...

Help?

---

