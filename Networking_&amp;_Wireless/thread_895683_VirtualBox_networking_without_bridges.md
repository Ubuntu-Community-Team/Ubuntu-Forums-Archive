---
title: "VirtualBox networking without bridges?"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by EvilMarshmallow on 2008-08-20
Hey,

I've been setting up a VM so I can manage active directory on my company's network.  My virtual XP can see the network and access the internet, but it's address-translated in VirtualBox to be on a 10.1.* network.  I'd like the virtual machine to contact my company's dhcp server and get a direct address so that the Active Directory Admin tools will work.  How do I set up VirtualBox to not create a subnetwork?

---

### Post by jimv on 2008-08-20
You need a bridge:

[https://help.ubuntu.com/community/VirtualBox#Networking](https://help.ubuntu.com/community/VirtualBox#Networking)

---

