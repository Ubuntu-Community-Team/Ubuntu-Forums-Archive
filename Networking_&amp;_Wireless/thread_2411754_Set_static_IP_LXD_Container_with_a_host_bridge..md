---
title: "Set static IP LXD Container with a host bridge."
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2019-02-03
Trying to move all services into containers. Currently I give my containers static IP's via mac address in my dhcp server config file. However if I move my dhcp and dns into a container, how do I give that container a static address. Will it just serve itself a dhcp address once it is booted or do I need and how to set a static ip to that container manually?

*EDIT* Feels like a useless post. Probably the simplest idea occured to me, simply configure a netplan profile inside the container. Problem solved.

---

