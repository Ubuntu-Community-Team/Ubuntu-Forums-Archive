---
title: "Samba choosing random ports to browse with"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Vuen on 2006-10-13
Hey all, running Kubuntu on Edgy. I'm trying to configure my firewall to allow Samba to browse the network. I've whitelisted all outgoing traffic, and I've opened the required ports 137-139 and 445 for incoming traffic. These allow me to share files by IP address (smb://192.168.0.X/) and allow other people on my network to access me just fine.

However when I try to browse smb:/ or access someone by netbios name, Samba keeps choosing a random port in the 1100 range on which to browse, and fails because the firewall blocks it. So far my logs show it's tried 1006, 1008, 1025, 1026, 1166, 1167, 1169, 1173... If I turn the firewall off, I can browse the network just fine.

Why is it doing this? Why isn't it just using the default ports?

Here's my smb.conf: [http://pastebin.ca/200972](http://pastebin.ca/200972)

---

