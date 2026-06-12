---
title: "Resolv.conf problem with PPPoE on boot"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by davidecapod on 2007-02-08
Hi all, I have a little problem regarding the resolv.conf.
I set up my ADSL connection using pppoeconf and chose to start it at boot: the problem is that on boot I don't find in resolv.conf my correct ISP dns address, but the IP of my modem/router, that is 192.168.1.1.
I have to restart manually the ppp connection with poff and pon dsl-provider, in this way in resolv.conf I have the two correct dns servers (212.216.172.62 and 151.99.125.1).
I tried to change eth0 from dynamic dhcp to static but with no luck, I have the same problem.
I attached my /etc/network/interfaces 

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
address 192.168.1.164
netmask 255.255.255.0
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

and /etc/ppp/peers/dsl-provider

noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
persist
usepeerdns
plugin rp-pppoe.so eth0
user "aliceadsl"

Many thanks
Davide

---

### Post by davidecapod on 2007-02-09
Ehm anyone? It should be quite easy to reproduce...

---

### Post by checho on 2007-02-10
Hi David! I used to have a similar problem. First you have to change back everything you did because making it static ip is not going to solve the problem, in fact I think is gonna make it worst. Ok, then run in console "ifdown eth0" and then "ifup eth0" that will reboot the ethernet card. Run "ifconfig eth0" and see if you have an inet address, NOT get confused with inet6, you can post all what you get here if you are not sure and I can check it. Well if you don't get an inet adress unplug your router and plug it again 30 sec later, Run in console "dhclient etho"  to get an inet adress. Then run in console "dig www.pcuser.com.au" and check if you can connet to it.( You may post what you get with this if still having problems). Check what you got for a nameserver either you can reach the adress or not. Then replace that number in /etc/resolv.conf . Finally run "chattr +i /etc/resolv.conf". This will make /etc/resolv.conf unaltereable (not going to alter, hope you understand me, as you may noticed english is not my first language). Because you got dhcp if ever you got no connection try again with the command dig because maybe the address is changed. This problem is common when you got a router modem combo. Let's see if it works for you. Good luck!

---

### Post by davidecapod on 2007-02-10
I did some more testing, it seems that sometimes I get the correct dns and sometimes not... I suspect this is related to different response times of dhclient, adsl synchronizing and ppp connection... anyway I made resolv.conf immutable as you suggested to avoid any problem.

Thanks
Davide

---

