---
title: "can't remotely connect to Ubuntu, it keeps timing out! Please help!"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by seymourm on 2008-02-26
The Setup: I have a PC running 64bit Ubuntu in a virtual machine  ontop of 32-bit Vista, connected through ethernet to a DI-524 D-Link Router. The virtual machine has a bridged connection with the host, the virtual machine has it's own static IP address on the network. 

Connecting to the virtual machine from within the network using SSH <Username>@<LocalIP> (on the host or another pc on my home network) through SSH works fine. Port 22 is forwarded on the router, the port is open in the firewall.

So I visit [www.whatismyipaddress.com](www.whatismyipaddress.com) to find the IP of my network, and again type SSH <Username>@<IPOfNetwork>. It spends about two minutes trying to connect before it fails and times out. It doesn't ask me for a password of anything.

I'm completely stuck. Any Ideas?

Thanks.

---

