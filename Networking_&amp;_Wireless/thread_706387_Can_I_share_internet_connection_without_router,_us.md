---
title: "Can I share internet connection without router, using extra ethernet port?"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by kung fu buntu on 2008-02-24
My computer has 2 ethernet ports, whereas one of them is connected to the modem.
I was wondering if I could use my extra RJ45 port to provide internet access to another computer.

Any ideas or how-tos to accomplish this?
And what are the main disadvantages in doing this? (ATM I'm waiting for another router)

Thank you.

---

### Post by Iowan on 2008-02-24
Yes it can be done - unfortunately I don't have specifics.  The "connected" machine can be set up as a router. Disadvantage would be "un-routering"  later.

---

### Post by k_grdn on 2008-02-24
Hi,

Connect your second machine to your primary machine with a crossover cable, give your second interface a private address.

On your primary machine use iptables to SNAT (masquerade) your internal private to external public, don't forget to echo 1 > /proc/sys/net/ipv4/ip_forward.


Set the default GW on your secondary machine to the address of your second interface.

Regards,

k_grdn

---

### Post by blastus on 2008-02-24
The easiest way is to install FireStarter and setup [Internet Connection Sharing](http://www.fs-security.com/docs/connection-sharing.php)

```
sudo aptitude install firestarter
```

Once you understand the networking concepts involved, it's really a snap to setup--no difficult commands to remember or anything.

---

### Post by kung fu buntu on 2008-02-25
I'm having some troubles getting this working...

```
	INTRA_NETWORK="192.168.50.0"
	GATEWAY_IP="192.168.50.1"
	SECONDARY_PC_IP="192.168.50.2"

primary computer
	# NIC connected to the internet
	PRIMARY_PC_EXT_NIC="eth2"
	# NIC connected to the second computer
	PRIMARY_PC_INT_NIC="eth3"

	# set the internal NIC as the gateway for the secondary pc
	ifconfig $PRIMARY_PC_INT_NIC $GATEWAY_IP
	# enable forwarding
	echo 1 > /proc/sys/net/ipv4/ip_forward

	iptables -t nat -L
	# to flush the nat table
	# iptables -F -t nat
	iptables -t nat -A POSTROUTING -o $PRIMARY_PC_EXT_NIC -j MASQUERADE


secondary computer
	SECONDARY_PC_NIC="eth1"

	ifconfig $SECONDARY_PC_NIC $SECONDARY_PC_IP
	route add -host $SECONDARY_PC_IP $SECONDARY_PC_NIC
	route add -net $INTRA_NETWORK netmask 255.255.255.0 $SECONDARY_PC_NIC
	route add default gw $GATEWAY_IP
```

The secondary computer can't ping its gateway :(
Any ideas?

@ k_grdn
You mentioned SNAT, but as far as I could see it requires a destination IP, but my external IP is dynamic. So that doesn't seem to be the best idea... or am I missing something?


BTW, will I be able to run servers on my secondary computer? Example: each computer running an FTP server on different ports... and what about on the same port?

Thank you.


EDIT:
another thing, my secondary computer also has 2 NICs. The problem is that I can't tell one from another   o_O
Is there any way to know on which NIC I have my cable plugged?
Note that (for enabling network on my second computer) I tested both eth0 and eth1... and none worked.

---

### Post by kung fu buntu on 2008-02-26
Anybody? :(

---

### Post by HermanAB on 2008-02-26
Explained in here:
[http://aeronetworks.ca/eeepc-howto.html](http://aeronetworks.ca/eeepc-howto.html)

Just scroll down a bit.  It is in there.

---

### Post by kung fu buntu on 2008-03-01
Thank you for the link HermanAB. I was able to get things working, even though the fact that I was droping ping request on my computer (the gateway) made things somewhat cryptic at first.

However I still have some problems.
Namely, I'm unable to get the client computer (the one that connects to the gateway) to listen on a port. In particular, I can't get emule fully working (it works but I get a low-ID at the client computer).

I tried doing this:
iptables -I FORWARD -i $PRIMARY_PC_EXT_NIC -o $PRIMARY_PC_INT_NIC
iptables -I FORWARD -o $PRIMARY_PC_EXT_NIC -i $PRIMARY_PC_INT_NIC
:rolleyes: but it didn't work very well.
Any idea on how do I solve this?

Is it possible to have both computers listen at the same port?

---

