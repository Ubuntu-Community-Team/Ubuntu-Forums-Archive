---
title: "Broke Network, I think using MoBlock"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by glok_twen on 2007-06-24
Hi - this is for my home network. The setup is pretty simple, just a bunch of PC's and laptops hooked to a netgear router. Somehow, I think by using/misusing MoBlock, I have messed up my network. 

Basically all I can do to tell this node is on the network is to connect to my router at 192.168.1.1 from a browser. Everything else fails.

Here are some more details. Any ideas what to try?

- Neworking had always worked fine - no issues, i never tinkered with it
- Then after a session yesterday when I started MoBlock and ran it using the GUI program I downloaded from the HOWTO, next time i re-booted the node I get no network.
- Here is the status now:
- When I ping the router, the ping command hangs
- But I can successfully connect to the router using my browser
- The system name used to show up in the router connection table but now that field is blank - the MAC address is still there, and the static IP address is being picked up correctly
- Using the browser to access anything outside my router just leads to a connection error
- I have no firewall running on the Ubuntu node (that I ever setup knowingly anyhow)
- Printing to a print server on the home network fails
- The node is not pingable from other pc's on the home network
- Other pc's can in fact get out of the home network
- I have tried /etc/init.d/networking restart; logging via gnomefailsafe session with no avail

Can you help?

Thanks,
GT

---

### Post by glok_twen on 2007-06-24
update is that i can now successfully connect to nodes on my own lan, but still can't get outside my router with a browser. one thing i can do is the command "host gmail.com" -- it seems to return success ("gmail.com has address 64.233.171.83 ...." - meaning DNS is working correctly???). But then, "ping gmail.com" returns: "connect: Network is unreachable"

Any suggestions??

---

