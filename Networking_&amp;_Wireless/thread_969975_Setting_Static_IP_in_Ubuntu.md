---
title: "Setting Static IP in Ubuntu?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by SerenityKill3r on 2008-11-03
Hey guys,

I've been trying for hours to set a static IP in Intrepid to no avail. I'm just after switching to Wicd as I heard it was better at handling connections than the default network manager.

I'm hard wired to a wireless router, and ports are open, but if I set the static IP in wicd, its still blocked according to the uTorrent Port Checker (best browser based one in my opinion).

Please Help.

Thanks,

Chris

---

### Post by SerenityKill3r on 2008-11-03
Anyone?

---

### Post by SerenityKill3r on 2008-11-03
Please, this is urgent!

---

### Post by maxhax on 2008-11-03
Well you should suppress NetworkManager, then run these.


> sudo ip route flush all

> sudo ifconfig eth0 <ip> netmask <mask>

then

> sudo route add default gw <gateway_ip> dev eth0

Then modify /etc/resolv.conf for DNS.  Add the following and save

> sudo vi /etc/resolv.conf

add these lines

> nameserver <ns1>
nameserver <ns2>

Ping your gateway ip.  If that works then do an nslookup on some domain.  I think google will actually let you ping them.  If that works you're up and running.  

Again, you'll want to suppress NetworkManager or else the roaming mode stuff is going to come back. 

I think you can actually do the above through the NetworkManager/GUI, but I never really figured that reliably out.  I just knew how to do this from headless installs so I always went with that.

---

