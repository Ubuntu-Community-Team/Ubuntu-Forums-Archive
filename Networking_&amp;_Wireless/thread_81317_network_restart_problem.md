---
title: "network restart problem"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by darth_vector on 2005-10-24
hi all,

i have my ethernet card set up ok, but whenever i do an

/etc/init.d/networking restart

i lose comms completely. i cant even ping machines in my lan. if i try i get the following:

connect: Network is unreachable

if i try to ping something outside the lan i get the usual dns error

ping google.com
ping: unknown host google.com

or with a public ip i get the same Network unreachable error.

i can still ping myself on the loopback port. things arent that bad!

im an ubuntu n00b, but i've been using redhat and fedore for a while. this has me stumped. any ideas?

thanks in advance

---

### Post by MakubeX on 2005-10-24
Yup, i have the same problem. I tried configuring the network using the GUI instead.

---

### Post by darth_vector on 2005-10-26
ok, recent development:

the route command prints out a routing table with the loopback port and the default gateway (the router) before i restart networking, but these entries appear to be deleted after the restart.

any ideas anyone?

---

### Post by phreaky- on 2006-04-05
Since recently I got the same problem, when I restart the network with /etc/init.d/networking restart. I loose the NIC completely. route -n doesn't give any output at all after that. and route add default gw 192.168.1.1 gives as error SIOCADDRT: Network unreachable.

If i change the address to 192.168.1.100 with ifconfig eth0 192.168.1.100. The output of route -m give me the wrong gateway 192.168.1.0 instead of 192.168.1.1 so i change that with route add default gw 192.168.1.1 and everything works again but if I do /etc/init.d/networking restart it loses the NIC completely only a restart of the computer helps me out.

I use kernel 2.6.15.6 any idea anyone?

---

