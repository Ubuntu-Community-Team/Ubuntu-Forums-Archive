---
title: "Advice request for absolute security"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by sarikan on 2008-09-04
Hi, I'd appreciate your help about a networking setup. I will be providing support to an institution over a remote connection. 
I will have to connect from different locations, different networks, almost anyting from free hotspots to other company networks, with their own security. I will have to transfer data, perform remote desktop connections to windows machines on the institution network, download and upload files to ftp, again in the institutuion network etc. 
I'll mostly be using a windows laptop, but a linux client is also likely. 
The IT guys have offered setting up a vpn server for the purpose which will use Ubuntu. Do you think openvpn server on Ubuntu can guarantee topmost security and privacy? No one, in any circumstances should be able to see the data that is being transferred, no eyedropping, no packet analysis etc. Due to nature of their data, they are very sensitive about this. In theory, openvpn should make me feel safe about it, but I am not a network guy, so I'd appreciate your advice. Do you have other suggestions? 

Kind Regards

---

### Post by mrsteveman1 on 2008-09-04
Openvpn should work but i think if you do that you have to use an openvpn client as well, which isn't a big deal but a consideration. I seem to remember its not PPTP or L2TP like most VPNs, but their own protocol.

Works fine though i've used it before, and either way there are other VPN servers available in the repos if you must use something that works with other clients.

---

### Post by sarikan on 2008-09-04
Hi, 
I've asked the same question in openvpn list too, and the responses showed that it is a good solution. Lucky for me, OpenVPN has a windows client, which is reported to be working just fine. 
Thanks for your response.

---

