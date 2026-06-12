---
title: "HOW-TO: Connect 2 routers using the WAN port on the 2 router"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by Ocxic on 2007-12-09
I've recently accomplished this and setup 2 separate networks. I did this for practice and to see if it was possible before I get my new DSL modem and wireless router. any way my basic config:


router2 (10.0.4.1) -> router/mdoem1 (10.0.2.1) -> internet

this is using a simpatico speed stream 6520 modem and d-link di-604 router.

first setup dsl modem / router as normal.

Then plug your computer into the d-link LAN port any will do. setup the dlink as follows with a static ip:

IP address: 10.0.2.2 <- this MUST be outside of your first router/ dslmodem DHCP range
net mask: 255.255.255.0
gateway: 10.0.2.1
PRI DNS : 10.0.2.1

under your firewall setting allow any/all traffic from the WAN port to the LAN on th d-link.

Now reconnect your computer to the speed stream.

go to Advanced -> Internet connection ->advanced settings -> add static route as follows

destination 10.0.4.0
net mask 255.255.255.0
next hop 10.0.2.2  <- this must be the ip addy of the d-link

add the route and connect a cable from a LAN port on the modem to the WAN port on the d-link, and now you should be able to use the second router and have entirely seperate networks


my speed stream network 10.0.2.0
d-link network 10.0.4.0
YAY!!!

This is my first how-to.. I hope this will help anyone trying to accomplish this

---

### Post by K.Mandla on 2007-12-20
Moved to Networking and Wireless.

---

