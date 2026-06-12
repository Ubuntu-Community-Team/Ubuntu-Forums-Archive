---
title: "Cant connect using ubuntu under VMware"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by eroica on 2007-03-08
hello,
i just installed vmplayer and downloaded ubuntu 6.10 appliance. i cant get the networking to work. ifconfig command shows eth1 is up but no ip address is assigned. i have interface setup for dhcp. i'm running on win2k as the host os, i see no dns entries in resolv.conf either. I also can ping localhost ok.My connection is thru a proxy.any suggestions on how to get this working. i'm just trying ubuntu out for first time and am not at all familiar with it.sorry if you dont handle ubuntu running under vmplayer. i thought i'd post and  give it a try.thanx....

---

### Post by Floppyjoe on 2007-03-11
> **eroica said:**
> hello,
i just installed vmplayer and downloaded ubuntu 6.10 appliance. i cant get the networking to work. ifconfig command shows eth1 is up but no ip address is assigned. i have interface setup for dhcp. i'm running on win2k as the host os, i see no dns entries in resolv.conf either. I also can ping localhost ok.My connection is thru a proxy.any suggestions on how to get this working. i'm just trying ubuntu out for first time and am not at all familiar with it.sorry if you dont handle ubuntu running under vmplayer. i thought i'd post and  give it a try.thanx....

Have you tried to issue the command:
```
sudo dhclient eth1
```
The Vmware Virtual machine should see your host machines network adapters and be able to use them. I haven't ever worked with a proxy before so I don't know a whole lot about them.

---

