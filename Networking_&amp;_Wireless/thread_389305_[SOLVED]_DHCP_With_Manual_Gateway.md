---
title: "[SOLVED] DHCP With Manual Gateway"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by ReverendJ1 on 2007-03-20
I am wondering how you set up DHCP with an alternative default gateway. The reason I ask is we have two internet connections at my work, a filtered for most users and unfiltered one for administrative purposes. DHCP will select the filtered one, but I need to be able to use the unfiltered one to connect to remote servers, etc.

---

### Post by Mr. C. on 2007-03-20
Using DHCP with a multihomed system is a little peculiar.  DHCP is designed to provide networking information so that user's do not have to be concerned.  As such, DHCP provides a default route (which you are calling gateway).

In your case, since you have two NICs, you can use DHCP, even on both NICs, but must override the default route manually, since two competing DHCP servers creates an undefined situation.

I presume you have your NICs on two seperate layer 2 networks, as they should be.  This implies two DHCP servers (or DHCP relaying).

Use the route command to change the route upon bringup of the second interface.  This can be accomplished in /etc/network/interfaces or via scrtip in /etc/networking/if-up.d.

MrC

---

### Post by ReverendJ1 on 2007-03-21
Mr. C - Thank you for your help! Although you did incorrectly presume I have two NICs. I only have one NIC, we just have two internet gateways here. I couldn't figure out how to get it working in /etc/network/interfaces, so I wrote a script and threw it in the /etc/**network**/if-up.d folder. Works great!

---

### Post by Mr. C. on 2007-03-21
I see.  In this case, all you need to do is change the default route.

MrC

---

### Post by ReverendJ1 on 2007-03-21
Yeah, thats what I did. This is my script - 
```
#! /bin/sh
route delete default
route add default gw XXX.XXX.XXX.XXX
```

---

### Post by Mr. C. on 2007-03-21
Excellent.

Now modify it so you can pass a single parameter, like filtered / unfiltered or -f / -u that allows you to swap between the two:

change_gateway -f
change_gateway -u

Without any parameters, it can default to the default route of your choice.

MrC

---

### Post by ReverendJ1 on 2007-03-21
Cool. Thanks for the idea. I now have a script named 'gateway', which I put in my /usr/bin folder so it was in my PATH, then I put a script called 'gatewaysetup' which I put in my /etc/network/if-up.d folder. Now my gateway is automatically set and I can change it any time by typing gateway -f.
gateway
```
#! /bin/bash
if [ "$1" == "-f" ]; then
	sudo route delete default
	sudo route add default gw xxx.xxx.xxx.1
	echo Now on filtered gateway.
else
	sudo route delete default
	sudo route add default gw xxx.xxx.xxx.2
	echo Now on unfiltered gateway.
fi
```

gatewaysetup
```
#! /bin/bash
gateway
```

---

### Post by Mr. C. on 2007-03-21
Nice.

Move the "sudo route delete default" above the if, and remove it elsewhere.

MrC

---

### Post by ReverendJ1 on 2007-03-21
Oops. Will do. Thanks again.

---

