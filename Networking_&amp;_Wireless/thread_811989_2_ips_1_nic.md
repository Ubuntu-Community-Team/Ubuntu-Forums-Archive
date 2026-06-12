---
title: "2 ips 1 nic?"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by mbarak on 2008-05-29
Hi I was wondering if it was possible to have two completely different IP addresses on the same network card.
I would like to have my ubuntu box be DMZ (which is only possible with DHCP on my router) and also be a part of the network.

As of right now all computers on my network get everything from the one server computer (ex: dhcp, dns, internet, everything)

The reasons behind this is purely for fun/education - this isn't at all necessary but would make life a lot easier for me especially since ubuntu is so much more versatile compared to my router.  I understand very well the security implications of this but, I trust the security of my ubuntu box and also i trust the security of the odds (who would want anything from my computer? theres nothing there anyways)

Thanks in advanced for any help/advice

---

### Post by bluefrog on 2008-05-29
virtual IP

e.g.
eth0
eth0:1

problem is (might be) packets for two different networks are travelling thru the same card hence could be a lot of loss.

---

### Post by elamericano on 2008-05-29
Right, just set it up with ifconfig:
sudo ifconfig eth0:1 192.168.1.1 netmask 255.1255.255.0

You may receive more multicasts due to the second network, but you probably won't notice. This is over the wire, right? So, there won't be any loss. I'm not sure what that comment was about. You're only limited by your total bandwidth.

---

### Post by mbarak on 2008-05-29
Unfortunately that doesn't work
My router only allows dmz to computers that are to which it assigns ip-addresses through dhcp
as soon as I enable eth0:0 with a static IP my router thinks (correctly) i have a static IP and disables dmz for my computer 

also the dhcp on the router interferes with the dhcp on my server

if it helps i have a 2wire router and the dmz is called "DMZplus"
apparently traffic is still filtered through the firewall on the router (to allow port forwarding for other computers) and is not sent directly to my computer

---

