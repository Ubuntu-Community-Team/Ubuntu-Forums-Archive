---
title: "HOW-TO monitor traffic on router?"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by lazertek on 2008-07-20
I wanted to keep to keep my home network monitored and keep track of the usage. I found out that I can use the opendns which will keep track of how much traffic is going through and which websites are visited. It has to be done through the router in order to monitor all computers usage. Is there any other way?

---

### Post by lisati on 2008-07-20
Wireshark? Use the router's built-in log?

---

### Post by tturrisi on 2008-07-20
To monitor all lan traffic you need to use a router.  Home routers usually have a built in switch that lan devices/comps connect through.  Most home routers have built in logging functions and the logs can be forwarded to a designated comp on the lan.

Wireshark will only work to monitor all comps on the lan IF all comps are connected to a hub, not a switch.  (connect all to a hub and connect the hub to the router switch)  You can't monitor traffic on a switch unless the switch is a managed switch, as the type in the home router.  A swicth sends ONLY the data to and from the specific ip address whereas a hub sends data to all ip adddresses connected to it.

---

### Post by Paris Heng on 2008-07-20
Use a switch/hub to connect to your router, then, install the SNMP client (without server) in the linux box, you can start monitoring!
Wireshark is not a good practice, it use for troubleshooting and high level of monitoring, if you feel it fine for you, no harm for you to try, but using git, you will feel bore faster. hehe

:guitar:

---

### Post by lazertek on 2008-07-25
but that way I would have install it on every computer on my network. What I wanted to do is monitor the whole network without having to do any tweaking in any computer.

---

### Post by tturrisi on 2008-07-25
Read my post above.
The ONLY way to monitor ALL switched lan traffic is via the router logs.  A home router has a built in switch, thus all traffic is switched.  The ONLY other way to monitor ALL switched traffic is to place a hub between the router switch and the computers:

```

		COMP w/ Wireshark
		|
ROUTER		- HUB - COMP
		|
		COMP

```

---

