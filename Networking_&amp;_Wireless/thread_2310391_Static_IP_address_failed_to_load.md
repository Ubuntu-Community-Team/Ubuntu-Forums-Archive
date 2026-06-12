---
title: "Static IP address failed to load"
date: 2016-01-18
forum: Networking &amp; Wireless
---

### Post by CrAzY12 on 2016-01-18
[ATTACH=CONFIG]266827[/ATTACH][ATTACH=CONFIG]266823[/ATTACH]

I have done my research and there are plenty of examples on how to set up a static ip address. But the static ip address fails to load still
I am using a VM fusion Ubuntu 15 server. I have configured the /etc/network.interfaces correctly (as shown in the attachment) and I am not sure what is going on.
The virtual network adaptor is on, I have doubled check the spacing of the new static ip address, restart the server and nothing seems to load eth1. Any suggestions will greatly be appreciated.


Here was my problem. For some reason Ubuntu Server 15.10 gave me a weird interface named en0167777736 during set up(shown in screen shot). and Ubuntu Server 14.0 did not. Which confused my virtual network adapter. [ATTACH=CONFIG]266828[/ATTACH]

---

### Post by Doug S on 2016-01-18
Could you post the output of "ifconfig". How do you know your VM has an interface named "eth0"?

---

### Post by CrAzY12 on 2016-01-18
Doug,

As requested. And could you explain your second question more clearly? When I add a virtual NIC to connect to my 10.10.20.X network I never have messed with the VM interface other than creating the 10.10.20.X network.

---

