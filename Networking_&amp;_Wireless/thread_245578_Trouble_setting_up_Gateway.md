---
title: "Trouble setting up Gateway"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by can8dnSix on 2006-08-28
Hi, I am trying to set up a gateway on a linux box.
eth0 - external NIC
eth1 - internal NIC

So far, I have assigned the static IP address which works on my notebook (what Im on now) but doesn't seem to work on eth0. Secondly, I've assigned 192.168.1.232 for the internal interface. I can't seem to get eth0 working on the Ubuntu box.

Is there a walk through or any ideas that might help me fix this problem. 

Topology: 
The Ubuntu box is the gateway to the Cisco router. This box is replacing a Slackware box that managed to get fried over the weekend from an electrical storm. A windows domain used to go through the Slackware box, which is now dead; thus, I need to get this Ubuntu box working. Any help will be greatly appreciated!

Can8dnSix

---

### Post by can8dnSix on 2006-08-28
Ok, well now I can get out into the WAN, but not the LAN. Anyway, thanks in advance. 

Can8dnSix

---

### Post by can8dnSix on 2006-08-28
OK, how do I have traffic go to 192.168.1.232 (LAN) to eth0 (WAN)? How can I forward the Internet traffic from the domain, through the Ubuntu box, to the Internet?

Thanks,

Can8dnSix

---

### Post by Original Brownster on 2006-08-28
Hi,
You gateway box (ubuntu) needs one entry to say all traffic on my lan subnet (192.168.1.255) route through eth1
another to say default gateway (address of your cisco router if this is the route to the outside world) through eth0

check the man page for the 'route' command.

you can experiment by creating temporary routes with:

$ route add -net 192.168.1.0 netmask 255.255.255.0 dev eth1

this creates a route so the ubunto box sends all traffic destined for the lan to your eth1 card and out onto your lan where hopefully one of your pc's will receive it.

$ route add default gw dev eth0

send anything else through eth0 (you've connected to your cisco router)


In the above both nics have their own ip, your eth1 should have an address in your lan range 192.168.1.x

eth0 should have one suitable to talk to your cisco router. could even be discovered via dhcp.

check the routing table with:
$ netstat -rn

interface config with:
$ifconfig -a

once your happy with the routing entries, make the permanent by creating a file as below (cut from someone elses post)

Create that file /etc/network/if-up.d/static-routes as follow
#!/bin/sh
# Set static routes
#
/sbin/route add -net foo bar
/sbin/route add -net foo bar


your laptop and other pcs only need one entry and thats a default route to the ubuntu box which is now the gateway.

route add default gateway 192.168.1.232


> **can8dnSix said:**
> OK, how do I have traffic go to 192.168.1.232 (LAN) to eth0 (WAN)? How can I forward the Internet traffic from the domain, through the Ubuntu box, to the Internet?

Thanks,

Can8dnSix

---

