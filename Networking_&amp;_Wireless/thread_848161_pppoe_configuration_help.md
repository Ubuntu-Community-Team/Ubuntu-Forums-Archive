---
title: "pppoe configuration help"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Tixer on 2008-07-03
So I run a server at home with two network interfaces, eth0 and eth1. eth0 is used to share between computers, and eth1 is used to connect with the outside world.

The problem I've been having has to deal with the pppoe configuration file, which unfortunately I don't know much about. 

Here is the file:

$ cat /etc/ppp/peers/dsl-provider
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
mtu 1484
multilink
maxfail 0
#holdoff 20
plugin rp-pppoe.so eth1
user [redacted]

So the first thing I want to do is have this dial on startup. After that, I want it to redial if it ever fails, and continue to redial if it fails an infinite amount of times. The last issue I've been having is that the dns servers change every time the connection is dialed (same with every other connection), so I want to make sure the dns servers remain what I specified them as, and cannot change.

---

### Post by superprash2003 on 2008-07-03
i remember a user creating a program which does exactly what you wanted , but im not able to find it now unfortunately.. About the DNS servers , read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. opendns servers ( 208.67.222.222 and 208.67.220.220) are used , you can change them to whatever you like..

---

### Post by Tixer on 2008-07-03
I know how to edit /etc/resolv.conf, and I know the domain servers I want to use (4.2.2.1), however, whenever I specify what I want, it reverts back every time a new connection is initiated, which the link you posted doesn't address.

---

### Post by superprash2003 on 2008-07-03
did you see that link?? you have to edit the dhclient.conf file not the resolv.conf file

---

