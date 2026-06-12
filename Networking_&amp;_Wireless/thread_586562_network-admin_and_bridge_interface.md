---
title: "network-admin and bridge interface"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by gvagenas on 2007-10-22
Hello all,

I am using Ubuntu 7.10 and having a question about network-admin tool.
The network-admin tool is  excellent choice for someone who needs to change different network profiles, but what happens when it comes in the picture a bridge interface?

All i need is to have roaming profiles AND bridge interface. In details, i want all the times the eth0(the physical connected interface) to be in promisc mode, but the br0 IF to change the settings (ip address etc) according to the profile....

I manage to do it by manually edit the /etc/network/interfaces file, but every time the network-admin tool applies a new profile, these settings go away...

Is there a way to add the br0 settings in the /root/.gnome2/network-admin-locations/ files?

Regards

---

### Post by vaalbygaardsvej on 2007-12-07
well i read somewhere that you could just ad the bridging commands to /etc/rc.local instead. but this does not work for me. hope to hear your result.

---

