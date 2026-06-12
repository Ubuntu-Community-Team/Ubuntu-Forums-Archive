---
title: "Can't access the internet on Server through Window PC bridge, no static IP..."
date: 2015-03-25
forum: Networking &amp; Wireless
---

### Post by ganawa on 2015-03-25
Right now, I'm using my Windows PC to bridge the wireless adapter and the LAN Ethernet, and that Ethernet is connected to a switch where my physical Ubuntu server is also connected. Ive set a static IP for the server, and everything works fine I can access samba shares on the windows PC and ssh into the server, but I have no internet connection. 

Ive tried a variety of different things. When I connect the server straight to the PC, with the original dhcp interface file I have internet access but I cant access the shares or ssh; the IP is the same as the Windows machine(expected). When its static it won't work at all. 

Ive tried adding the dns server(192.168.0.1) in the interface file and tried setting the gateway to the windows machine and tried setting it to the actual gateway(192.168.0.1), when its connected to the switch with a static IP, this doesn't work either. 

Ive been attempting to use ICS in windows instead  of bridging the adapter, and I've had trouble doing this also. The server with dhcp gets a 167.* auto address, and wont work at all with a static address. 

When I try to set a static address on the LAN Ethernet on the windows to (192.168.0.199, server ip), and the same ip on the Ubuntu server I get a IP conflict. 

How can I set a static ip for the server using the windows computer as a bridge, and still be able to access the internet?

---

