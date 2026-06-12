---
title: "[SOLVED] Belkin Router F5D8233-4"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by bwtranch on 2007-12-15
Hi folks. Been a while. Trying to get this router to work on an emachines 32-bit Intel running Ubuntu 7.10 as a host. Slave is a AMD 64 and that adapter seems to be working fine. I'm not the greatest at networks. lspci shows nothing installed. Don't know where I am going on this one, any help would be appreciated.

---

### Post by bwtranch on 2007-12-29
This was not easy to find for some reason. I noticed nobody had bothered to look at this post from a while back and here is the solution. [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Maybe the reason is is the fact they it wasn't the router at all, but the network adapter. And contrary to what some say. Don't put it in roaming 'cause it won't work!!! Here's a few other weird things: It'll be on eth1, set password type to WPA personal and you'll set up your own password.

If anybody has any comments about this I'd love to hear it. This may not be 100% kosher, but it works and just as fast as my wire. Running between T2 and T3.

---

