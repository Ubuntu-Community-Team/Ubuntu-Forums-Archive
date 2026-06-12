---
title: "Lubuntu DHCP address range"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by Anders_Lind on 2014-04-17
Hope this is possible to solve.

I have a laptop with Lubuntu 13.10 where I get internet access through WiFi and then share it on the Ethernet side.

The problem is that the IP address on the Ethernet side is in the wrong address range. Eth0, DNS and DFGW have IP address 10.42.0.1 and the clients get addresses 10.42.0.*

I wish to have it all in address range 192.168.1.*

What files should I change in order to have the adress range 192.168.1.*?
 I have tried a bit in /etc/dhcp/dhcpd.conf but i don't get any result.

Thanks in advance

---

### Post by TheFu on 2014-04-17
There are reasons to AVOID 192.168.x.x addresses.  Just sayin'.   A few weeks ago, I re-IP'd my entire internal network (about 30 devices) to 172.22.x.x to make VPNs work from more places.  Basically, 192.168.0/1/2.x should be avoided. They are so common that it is likely to cause a conflict when at a client or traveling.

On my 13.10 netbook, the DHCP is handled by dnsmasq, but the config is from LXC.  This command found where that happened:```

$ find /etc -type f -print  -exec egrep '10.42.0' {} \; | tee /tmp/t
```

Then I just needed to look in /tmp/t for the specific file.

---

### Post by Anders_Lind on 2014-04-17
Thanks for your reply, but the search for "10.42.0" gave no answer. 


I begin to suspect that it is "hard coded" and not possible to edit. Someone who is more familiar with Lubuntu, feel free to confirm or deny.

---

### Post by TheFu on 2014-04-17
I use LXDE all day, most days.  This is NOT specific to that.
Check your network settings or the router (assuming a router is provided address ranges, which seems unlikely).

This can help too:
```
$ route
```

It may be a hard-coded "default" value for the DHCP server being used. You'll just need to find the config file and setting to change that.  dnsmasq.conf is what my system uses, but that points to other places to get more information ... like /etc/dnsmasq.d-available/  which points to other files that point to settings inside the virtual machine setup running here.

---

### Post by Iowan on 2014-04-17
What program are you running for DHCP?

---

### Post by Anders_Lind on 2014-04-17
> **Iowan said:**
> What program are you running for DHCP?

I think it's isc-dhcp-server 4.2.4 thats included in Lubuntu...

---

