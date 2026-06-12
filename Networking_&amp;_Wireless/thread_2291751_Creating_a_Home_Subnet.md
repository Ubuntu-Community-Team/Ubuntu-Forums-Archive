---
title: "Creating a Home Subnet"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by CosmicFlux on 2015-08-22
Hi,

I want to isolate part of my home network for the purpose of creating a lab environment.Obviously I don't want what I'm doing to affect my Home network or Internet access, so I'm trying to create a subnet. 

[LIST]I went into the router I'm using for the subnet and altered the DHCP pool to contain a range of 10.0.0.1-5 for the machines.[/LIST]
[LIST]I gave the internal IP address of the router (gateway and server) as 10.0.0.254.[/LIST]
[LIST]I made the external IP address of the router 192.168.1.145 so that my primary router saw it on the Home Network.[/LIST]

It's not working, though. I'm not sure if I've followed all the correcrt steps and what I'm missing.

Can anyone explain the process?


Cheers,
Cosmic

---

### Post by TheFu on 2015-08-22
Please draw a picture and label the IPs for every interface. Chances are that will make the issue jump out.

---

