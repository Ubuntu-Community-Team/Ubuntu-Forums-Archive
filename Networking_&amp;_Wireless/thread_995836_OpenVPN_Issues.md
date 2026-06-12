---
title: "OpenVPN Issues"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2008-11-28
HI,

I am having issue with my VPN - when our ppp connection is re-authenticated every 24hours the VPN fail to come back up.

I noticed that the file ipp.txt which should contain the client servers IP address contain two reference to the servers that are causing trouble.

so in ipp.txt it may contain

chrislynch 192.168.200.5
user2      192.168.200.9
server2    192.168.200.6
#these one cause the trouble then
server03   192.168.200.58
server04   192.168.200.68
server03   192.168.200.77
server05   192.168.200.44
server05   192.168.200.52
server04   192.168.200.85

I remove the line in the server.conf file that tell it to use ipp.txt when a connection drops to re-assign the IP and then I restarted the openvpn nad all connection came back up.

Is there a way to start a fesh ipp.txt file as it linked with the server cert???

I am also getting a message in my log relating to a server05 saying "bad source address from client [it IP], packet drop....

What is this message about - I've seen it mentioned and they say to create the ccd and have reference to the server in this case server05 I have this and the message is only appear for server05 and not the others.

Rgds
Chris

---

