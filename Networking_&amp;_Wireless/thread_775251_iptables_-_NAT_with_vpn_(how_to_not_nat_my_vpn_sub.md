---
title: "iptables - NAT with vpn (how to not nat my vpn subnets)"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by scurry7 on 2008-04-29
I have setup a ubuntu firewall (with iptables), and vpn box (openswan)...
with no iptables statements my vpn works great to all subnets on the other side (10.0.0.0/24, 10.1.0.0/16, etc...).  When I setup iptables it tries to send all traffic out the internet interface.  My nat statment is ```
iptables -t nat -A POSTROUTING -o eth0 -s 10.6.0.0/16 -d 0/0 -j MASQUERADE

``` (maybe someone can specify a better way - if so please let me know).  
Okay so I flush my iptables ```
iptables -t nat -F
``` and setup this statment telling it to not nat traffic from 10.6.0.0 going to 10.0.0.0/24 ```
iptables -t nat -A POSTROUTING -o eth0 -s 10.6.0.0/16 -d ! 10.0.0.0/24 -j MASQUERADE

```
works great, until i add an addional subnet ```
iptables -t nat -A POSTROUTING -o eth0 -s 10.6.0.0/16 -d ! 10.1.0.0/16 -j MASQUERADE

```
once the two commands are in the nat table then nothing works.
someone please help me!!!

my main goal (what ever the best way to accomplish it) is to have nat setup (so my nodes on the lan can access internet) and allow traffic through my vpn tunnels (when destined for the 5 other subnets).

thanks in advance!

---

### Post by SpaceTeddy on 2008-04-30
mhm... i don't quite understand the setup yet. Where are the vpn clients ? who is routing where ? why do you have five subnets that each hold 65k IP addresses ?

could you please be so kind as to draw a picture of your setup (and include the essential ip addresses aswell)

at the moment my only idea is that somehow you are doing something to a route that is not supposed to happen - but what i don't know... i would need more information for that :)

hope we can figure this out :)

---

### Post by scurry7 on 2008-05-06
I found the answer, this is a point to point vpn (so no clients) and my ubuntu box is my site's (sever/router). I also have to do NAT so my nodes on the LAN can have internet access for all traffic not going to my private addresses.  Here is my iptables:
```

iptables -t nat -A POSTROUTING -o eth0 -s 10.6.0.0/16 -d 10.0.0.0/24 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -s 10.6.0.0/16 -d 10.1.0.0/16 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -s 10.6.0.0/16 -j MASQUERADE

```
so it accepts traffic destined to 10.0.0.0/24 and 10.1.0.0/16 (and puts it on the vpn) and all other traffic is Masqueraded (or NATed).

hope this helps someone out there...

---

