---
title: "Router set up WAN: wlan0, LAN: eth0"
date: 2015-09-22
forum: Networking &amp; Wireless
---

### Post by yosukesan on 2015-09-22
Hi 


I need a help to make my laptop a temporary router.
I am trying to connect my rasbian machine via my ubuntu laptop to install several package.


I managed through ping from 192.168.10.1 (rasbian machine) to 192.168.100.1 (router).
However, there is no return from 8.8.8.8.


I spent nealy a month but still unable to make it. Please someone give me clues.

Reference:
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)


The following is my network configuration.


----------------------------
ROUTER ( mobile wifi )
----------------------------
 192.168.100.1
 ( not sure about WAN addr probably the router has one, but can not check it ) 
 Accoding to the manual, this router only support ipv4.


----------------------------
ubuntu-laptop
----------------------------
 eth0: 192.168.10.2
 wlan0: 192.168.100.100


 # netstat -r -n
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
 0.0.0.0         192.168.100.1   0.0.0.0         UG        0 0          0 wlan0
 169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
 192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
 192.168.100.0   0.0.0.0         255.255.255.0   U         0 0          0 wlan0


 $ less /proc/sys/net/ipv4/ip_forward 
 1


 $ less /proc/sys/net/ipv4/ip_dynaddr
 1


 # iptables --list
 Chain INPUT (policy ACCEPT)
 target     prot opt source               destination         


 Chain FORWARD (policy DROP)
 target     prot opt source               destination         
 ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
 ACCEPT     all  --  anywhere             anywhere            
 LOG        all  --  anywhere             anywhere             LOG level warning


 Chain OUTPUT (policy ACCEPT)
 target     prot opt source               destination  


----------------------------
rasbian
----------------------------
 eth0: 192.168.10.1


 # netstat -r -n 
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
 192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
 192.168.100.0   192.168.10.2    255.255.255.0   UG        0 0          0 eth0

---

### Post by helgman on 2015-09-22
The problem is (most likely) that your router (mobile wifi) do not have a route back to the 192.168.10.0/24 network. The easiest solution would probably be to set up masquerading on the Ubuntu-router and hide network 192.168.10.0. That way you do not need to make the mobile wifi router aware of its existence.

There is some information about masquerading (NAT) in the document you link to in your post. You can also find some information here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) (section 4.1).

If you can modify the router (mobile wifi) then you might be able to create a static router from it to network 192.168.10.0/24 but then I cannot point you to any documentation ... ;-)

---

### Post by yosukesan on 2015-09-23
Thanks for the NAT information helgman.

I forgot to mention. I tried it as my first hands, set every machines in 192.168.100.0/24 network, but the router does not allow this configuration.
I found my mobile router can switch to PPPoE mode which uses global IP. Masquerading it might be the solution for me.

---

### Post by helgman on 2015-09-23
I just re-read your original post and the rasbian does not seem to have a route to the internet. You need to make sure that it has a "default route" pointing to the ubuntu-laptop:

```
sudo route add default gw 192.168.10.2
```

Now your packages should be able to reach 8.8.8.8 but on the way back your internet facing router might not be able to hand them correctly.

---

### Post by yosukesan on 2015-09-27
After setting the default gateway on my rasbian, it can access to the global address.

Thank very much helgman.

---

