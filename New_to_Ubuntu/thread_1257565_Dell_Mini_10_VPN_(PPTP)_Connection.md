---
title: "Dell Mini 10 VPN (PPTP) Connection"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Rick Ross on 2009-09-03
I am new to the UBUNTU community and in need of assistance. From reading through many of the other posts already listed I have noticed that asking can be the key to the help I am looking for. 
My problem is that I cannot connect to the Wireless VPN at my school. I begin by trying to add the VPN Connection Manager (PPP generic) at which point I recieve an error message stating that the application conflicts with other software and that software needs to be removed before I can run 'network-manager-pptp'. But to this point I am unable to discover the piece of software which needs to be removed.
Any suggestions,advice, or direction would be greatly appreciated. 

BTW- I am currently running version 8.04....... which I also am unable to upgrade currently

---

### Post by schwascore on 2009-09-06
VPN is neither wireless or wired, it is a protocol for remote access to a LAN when you are on another network.  

Perhaps you are trying to connect to the schools wireless LAN/WAN?  If that's the case, then you don't need any VPN software.

Can you access other wireless networks outside of school?

---

### Post by Rick Ross on 2009-09-07
First thank you for the response this has been driving me mad. To answer your question, yes I can connect to other wireless networks but my school offers instructions for connecting to the VPN network which state that i must download the VPN connection manager ppp generic but until this point the computer refuses to allow me to add this program and i am unable 2 access any web sites while connected to the wireless the school has because i need to sign in which i am unable to do until the VPN is set up correctly

---

### Post by itchyball on 2009-09-15
I have the same problem.  Last night Dell had me do a clean install with reinstall disk, then update through update manager. Today they informed me there is nothing more they can do, it's a problem with Ubuntu. I need to connect through a VPN to set up a remote desktop with my company.

Did you get it working?

---

### Post by Rick Ross on 2009-09-16
Sorry until this point I am also still in the dark as to how to get my VPN working correctly

---

### Post by colinmacdonald on 2010-01-06
Looks like the problem is that the network-manager-pptp package is not up to date, so that it conflicts with the current version of network-manager.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/392614](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/392614)

I think we're pretty much stuck waiting for it to be updated.

---

### Post by hambidextrous on 2010-02-07
This is affecting me as well.  I need to add a VPN, but no of the packages available work.

---

