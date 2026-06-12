---
title: "XP computer connects, Ubuntu wont."
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by jseiser on 2007-03-23
The 2 computer lost internet overnight, and now i can connect with the xp one, but the ubuntu one will not connect to the internet.
Thge setup of the xp computer is 192.168.1.136
subnet 255.255.255.0
DG 192.168.1.1

can someone show me how to get the ubuntu computer set up to connect to the internet with an ip of 192.168.1.137 ?  The internet always works, but since it wont now i might as well set-up static ip's :)

---

### Post by chili555 on 2007-03-23
Not much information here...

Wired or wireless? What have you tried so far? Stop and restart networking? Reboot? 

In my opinion, setting static IP's is no more likely than DHCP to connect but is, in fact, harder to diagnose, because your interface always has an IP, whether it is actually connected or not. With DHCP, you only  get an IP address if you are well and truly connected.

Please restart networking:```
sudo /etc/init.d/networking restart
```Please let us know.

---

### Post by jseiser on 2007-03-23
its dsl coming in to a wired linksys router going to Feisty ubuntu computer  and a XP computer.
Ive tried power cycling, it was on DHCP but would not get any IP or connect to the internet.  THe xp computer was DHCP but connected and i then switched it to the static, so i could put the ubuntu one with the next ip and then open certain ports on my router.  Ive tried rebooting, dhcp, static ip and still cant connect.

---

### Post by jseiser on 2007-03-23
tried your command and still cant connect.

on ubuntu my settings are

ip 192.168.137
subnet 255.255.255.0
dg 192.168.1.1

host name ubuntu
automatic service discovery is checked (default?)

dns 216.206.238.37
216.206.238.5
search domain cros.net

)hosts Tab)
Ip - 127.0.0.1 local host
ip 127.0.1.1 ubuntu.cros.net ubuntu
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

in ip imfortmation it says 
IPv4 192.168.1.137 netmask 255.255.255.0 broadcast 192.168.1.255no scope
IPv6 Fe80::211:d8ff:feec:718e netmask 64 no broadcast scope - Link

state = Active

---

