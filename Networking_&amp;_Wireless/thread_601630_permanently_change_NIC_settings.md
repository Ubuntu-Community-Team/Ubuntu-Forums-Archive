---
title: "permanently change NIC settings?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by akahige on 2007-11-03
I recently upgraded to a Netgear GA311 10/100/1k adapter. Everything seems to work fine. Since the card (and my switch) supports jumbo frames, I want to take advantage of that. Searching through the forums gave me the solution to increasing the mtu so that the frame size is bigger:

```
sudo ifconfig eth1 mtu 7200
```

Everything switches accordingly and flies along as expected.

The thing that doesn't work is that the setting is not persistent between reboots -- and I'm wondering how I can permanently change it.

Thanks!

---

### Post by Lambert on 2007-11-04
If you're using a static ip, you simply open the /etc/network/interfaces file and under the devices name you enter 

```

mtu 7200

```

If you're using dhcp then do this.

edit /etc/dhcp3/dhcpd.conf and add

option interface-mtu 7200;

sudo /etc/init.d/dhcp3-server restart

edit /etc/dhcp3/dhclient.conf

add interface-mtu to the end of the request list, 

sample:

```

request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name,
netbios-name-servers, netbios-scope, interface-mtu;

```

---

### Post by akahige on 2007-11-04
Thanks for posting back.

Your instructions make sense, but the files present on my system (or not, as the case may be) are making it a little hard for me to follow.

I'm running DHCP, so...

> **Lambert said:**
> If you're using dhcp then do this.

edit /etc/dhcp3/dhcpd.conf and add

option interface-mtu 7200;
This file does not seem to exist on my system (running Feisty). Wasn't clear if I'm supposed to be adding to it, or creating it, but under the assumption that I was to create it...


> sudo /etc/init.d/dhcp3-server restart
No such thing exists in my init.d directory. In fact, I didn't see anything conspicuously related to DHCP in init.d.


> edit /etc/dhcp3/dhclient.conf

add interface-mtu to the end of the request list, 

sample:

```

request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name,
netbios-name-servers, netbios-scope, interface-mtu;

```

I follow what you're saying, but since I had problems with the aforementioned other things, I con't know that I should be jumping ahead and doing this yet.

What am I missing?

Thanks for helping...

---

