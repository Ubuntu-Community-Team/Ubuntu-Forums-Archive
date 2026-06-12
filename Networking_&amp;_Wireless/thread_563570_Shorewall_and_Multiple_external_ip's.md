---
title: "Shorewall and Multiple external ip's"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Biermann on 2007-09-30
I have five ip's from my ISP and i got an ubuntu machine with six nic's.
eth0-4 is external and eth5 is for the internal LAN.

I want to be able to route traffic from the lan to diffrent external ip:s depending on what port is used. For example i want traffic from eth5 on port21 to use eth1, traffic from port 6887 to use eth2 and so on. I also want all traffic from one ip on the internal LAN to go through eth4.

I've tried som configurations with shorewall, but nothing is working good. Anyone got an idea on how to do?

---

### Post by helgman on 2007-10-04
I'm pretty sure you can do it with iptables:

[iptables](http://linux.die.net/man/8/iptables) (man-page)
[Linux iptables HOWTO](http://www.linuxguruz.com/iptables/howto/)
[Iptables Tutorial 1.2.2](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

And I'm fairly sure there are more examples [out there](http://www.google.com/search?hl=en&q=iptables).

Regards,
Helgman

---

### Post by Biermann on 2007-10-13
Can't find any guides or tips on how to configure an iptables script or shorewall for the stuff i need... :(  anyone?

---

### Post by helgman on 2007-10-14
I don't have the time to do this for you but if you read the manual you see a few things that might be of interest for you.

a) You can use NAT to make it look like packages from the internal networks come from the interface they leave on.

b) There are two parameters called -i and -o that specify what interface the traffic comes in and leaves on. The [manual](http://linux.die.net/man/8/iptables) says this about them:

> **-i, --in-interface **[!] *name*
    Name of an interface via which a packet was received (only for packets entering the **INPUT,** **FORWARD** and **PREROUTING** chains). When the "!" argument is used before the interface name, the sense is inverted. If the interface name ends in a "+", then any interface which begins with this name will match. If this option is omitted, any interface name will match. 
**-o, --out-interface **[!] *name*
    Name of an interface via which a packet is going to be sent (for packets entering the **FORWARD,** **OUTPUT** and **POSTROUTING** chains). When the "!" argument is used before the interface name, the sense is inverted. If the interface name ends in a "+", then any interface which begins with this name will match. If this option is omitted, any interface name will match.

Play around with them some and see what happens.

As for using Shorewall I don't have a clue - if I find the time I'll install it and have a look. The same things goes for iptables ...

Regards,
Helgman

---

### Post by cecilkorik on 2008-02-11
Sorry for digging up a dead thread, but I found the answer to this question after much experimentation, and it's actually fairly simple with shorewall. So for anyone who finds this thread from searching, like I did, here's the answer.

Assuming you're using NAT/IP Masquerading between your public IPs and your local network, here's all you have to do:

Go into your /etc/shorewall/masq file, and where you currently have something specifying your NAT like:

eth0    eth1

You can put a bunch of extra rules in here (BEFORE the eth0 eth1 line) to specify outbound addresses for specific hosts or ports. It works like a charm. Here are few examples of what you can add (assume your internal LAN is 192.168.1.* and your public IPs are xx.25.26.*):

# Forces all outbound traffic for your local PC 192.168.1.77 to appear as if it is coming from xx.25.26.100
eth0    192.168.1.77    xx.25.26.100    

# Forces all outbound traffic on tcp port 25 (smtp) to appear coming from public IP xx.25.26.99
eth0    eth1    xx.25.26.99    tcp    25

You can also specify your default outbound address explicitly at the end of the eth0 eth1 line if you don't like the default one you automatically get:
eth0    eth1    xx.25.26.1

Here is what my masq file looks like (eth0 is my public NIC, eth3 is my local NIC):

eth0    eth3    xx.xx.xx.72    tcp smtp
eth0    192.168.50.6    xx.xx.xx.72
eth0    eth3    xx.xx.xx.70

---

