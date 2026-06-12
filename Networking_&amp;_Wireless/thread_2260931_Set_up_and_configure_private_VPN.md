---
title: "Set up and configure private VPN"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by verlyn13 on 2015-01-15
Greetings,

I am looking to install a headless computer at my parents' house in the United States that I can connect to it via VPN from my house in Egypt.  I would like to connect to the computer via VPN from my Ubuntu (and Windoze) boxes here in Egypt so that I can manage my parents' LAN and have a public IP address from the US when convenient.

- What are minimum hardware requirements for this type of computer?  I am thinking maybe an intel NUC or similar low power type device.  

- I am looking for a step-by-step guide for the appropriate software and packages to install on the server and host machines to make this work, but I can't seem to find exactly what I'm looking for (especially the part that gives me internet access from the vpn server).  It seems like an openVPN server should be able to do it from what I've read.  

- I also need some advice on how to forward the correct ports on my parents' router so I can access the machine away from their LAN.  

Any help on this matter is greatly appreciated.  I have a basic knowledge of how networking works (like samba file sharing), but I have never done something this advanced.
Jeff

---

### Post by TheFu on 2015-01-15
A NUC would be fine for most US bandwidth, so would a Rpi actually. If they have less than 100Mbps connection, the Rpi is fine.
Yes, openvpn with IPSec is most likely what you want. Do not use pptp. The Egyptian government certainly can hack that.

OpenVPN server is non-trivial to setup. It only required 1 port to be opened on the server side. Because it is extremely flexible, it is also extremely complex. Good luck.  

I would strongly suggest that you setup ssh using keys for another remote access method to your parents.  ssh is much easier to get working, only requires 1 TCP port to be opened as well (use a non-standard port and please follow the best-practices in the next link so you don't get hacked; definitely DO NOT ALL PASSWORDS!!!!!!!!!!!) and can be used as a poor-man's VPN too.  [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)  If you might want to run a remote desktop, get the NUK to run an x2go-server, not the Rpi.

You can get ssh working in a few minutes. openvpn generally takes days the first time, hours the 2nd and minutes after that.  ssh is minutes almost always.

---

### Post by SeijiSensei on 2015-01-15
I use OpenVPN with a simple static-key setup to create a full-time tunnel to my servers in the cloud.  A computer in my house acts as the OpenVPN client and sets up a tunnel with one of my virtual servers.  All that is required is for one machine to be visible on the Internet.  If you can forward a UDP port from your parents' router back to the VPN device, you can leave it running and connect to it from anywhere on the net. The hardware requirements are minimal.  A Raspberry Pi is more than sufficient.

You only get one IP with this arrangement.  If you want to have multiple devices connecting simultaneously the configuration is much more complex.  But for a point-to-point tunnel it's hard to beat OpenVPN in a static-key configuration:  [http://openvpn.net/static.html](http://openvpn.net/static.html)

---

