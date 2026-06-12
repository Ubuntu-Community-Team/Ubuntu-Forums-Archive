---
title: "Transmission Bittorrent over OpenVPN tunnel only ?"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by dominik10 on 2015-07-01
Hello guys this is my first thread in the forum here so please be able to handel some noob questions xd

1.So what i want to do is run Transmission Bittorrent client over the openvpn tunnel can someone help me to build a simple vpn killswitch if the connection to the server drops?
in the end i only want to be able to run transmission over the openvpn connection without getting my real ip leaked !!!


sorry for my bad english :D

---

### Post by nlee2 on 2015-07-01
Is ip leak prevention only applicable to P2P? Would be simpler if it was for internet connection. You are asking for help to build a vpn killswitch for what network? Need to know more details of the tunnel, the server and your network topography.

Personally, I turn off nat on my wan port and route all my lan traffic out the tunnel. If the connection drops the ip leaked is my private ip address.

---

### Post by dominik10 on 2015-07-02
transmission should only be able to run over the openvpn connection so if the connection to the openvpn server drops all up and downloads will be stopped.

want i want is :

ipv6 disabled 
custom dns server from google or opendns 
transmission over vpn only with other words killswitch

thx dominik

---

