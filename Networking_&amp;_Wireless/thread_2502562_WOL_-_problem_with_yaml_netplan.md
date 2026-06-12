---
title: "WOL - problem with yaml netplan"
date: 2024-11-19
forum: Networking &amp; Wireless
---

### Post by goupil35000 on 2024-11-19
Hi,
I have a problem with the configuration of my networks in Ubuntu 24.04.
I am in a school with this configuration:
- a local network with a server;
- wifi for Internet with WPA2 Entreprise

The students are able to connect on the computers and enter their credits for Internet. They are able to use the local network too.

But I need to allow special users to login in a computer and power on the others computers using WOL on local network and be able to connect all remote computers on internet. 

My biggest problems:
- the yaml file in /etc/network changes his name each time a student connects;
- the names of the interfaces change too : it's not eth0 and wlan0.

I tested one solution on raspberry pi and it worked except for wol : the solution was to ssh to remote computers and change the content of the yaml file in /etc/network which has always the same name (and it's the same for interface names) and to then apply netplan.

But on amd64, due to changes of the name of the interfaces and the name of the yaml, I don't know how to do it. Plus I need to activate WOL.

Thanks to share a solution if one exits.

Tom

---

