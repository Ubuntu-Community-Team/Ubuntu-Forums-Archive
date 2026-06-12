---
title: "Trying to understand iptables/openvpn"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by AdeJczr on 2014-04-21
Hello,

I've recently (successfully) installed openvpn on my home server (Ubuntu Server 12.04) and can connect my Android smartphone and iPad. Yay.
I'm confused, however, as to how the connections get through my firewall as I have not made any exceptions in UFW for openvpn. Openvpn created a new interface called as0t0 and appears to have added some iptables rules. I normally use ufw since I do not understand the iptables syntax.

Sooo... 
[SIZE=3]1. Why is openvpn working when i havent allowed the ports through ufw?
2. What do the iptables rules mean that openvpn seems to have created?
3. What is as0t0?[/SIZE]

My goal is to be able to smile and see ufw managing access to my openvpn ports. Ultimately, i want to create an iptables rule to prevent someone from brute-forcing my admin WebUI (listening on port 943).

My ufw output:
```
Status: activeLogging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip


To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
25565                      ALLOW IN    Anywhere
32400                      ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere (v6)
25565                      ALLOW IN    Anywhere (v6)
32400                      ALLOW IN    Anywhere (v6)





```

My iptables output (snip)
```
Chain INPUT (policy DROP)target     prot opt source               destination         
AS0_ACCEPT  all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
AS0_ACCEPT  all  --  0.0.0.0/0            0.0.0.0/0           
AS0_IN_PRE  all  --  0.0.0.0/0            0.0.0.0/0            mark match 0x2000000/0x2000000
**AS0_ACCEPT  udp  --  0.0.0.0/0            192.168.1.4          state NEW udp dpt:1194**
AS0_WEBACCEPT  all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
**AS0_WEBACCEPT  tcp  --  0.0.0.0/0            192.168.1.4          state NEW tcp dpt:943**
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           



```

My ifconfig output:
```
as0t0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00            inet addr:172.27.224.1  P-t-P:172.27.224.1  Mask:255.255.240.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr *************** 
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae3:b5ff:fec6:5260/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:579553 (579.5 KB)  TX bytes:579553 (579.5 KB)



```

---

### Post by ian-weisser on 2014-04-23
Well, if it's anything like my VPN, the initial connection should be using Port 22, which you haven't blocked.

---

### Post by SeijiSensei on 2014-04-23
OpenVPN uses port 1194 by default and UDP as the transport mechanism.  It's very different from an SSH tunnel.

OP, something or someone put this line into your ruleset:
```
AS0_ACCEPT  udp  --  0.0.0.0/0     192.168.1.4   state NEW udp dpt:1194
```
That permits UDP connections from anywhere to the OpenVPN port.

I have no idea what the connection to 943 is for.  That's not a registered port in /etc/services.

---

### Post by AdeJczr on 2014-04-28
Port 943 was allowed by openVPN in order to for the admin WebUI to be accessed remotely. I guess what I'm wondering now is why don't the UDP 1194 and TCP 943 rules show up in the UFW interface?

---

