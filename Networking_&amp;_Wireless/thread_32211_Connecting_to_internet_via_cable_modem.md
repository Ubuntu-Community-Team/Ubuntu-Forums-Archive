---
title: "Connecting to internet via cable modem"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by defkewl on 2005-05-06
Does anybody know what do we need to do in order to connect to internet via cable modem?

I'm using a Motorola Surfboard 5100
I connect to the PC by Ethernet card.

Could anybody give me a clue on this?

---

### Post by Rhawi Dantas on 2005-05-06
sudo pppoeconf

And then just configure it... I don't know much of your kind of connection but its pretty much this...

---

### Post by defkewl on 2005-05-06
It didn't work. I think the command you gave me was meant for a telephone modem

---

### Post by Professor X on 2005-05-06
Check out [The Cable Modem HOWTO](http://en.tldp.org/HOWTO/Cable-Modem/index.html).

---

### Post by defkewl on 2005-05-06
The manufacturer said that the problem is with the network driver. Where can I update the network driver?

---

### Post by blueplazma on 2005-05-06
What exactly is the problem?  All you should have to do it plug the ethernet cable into your computer, and then run dhclient to get an IP address.  That's all it's ever taken for me on Comcast.

---

### Post by crane on 2005-05-07
[QUOTE=blueplazma]What exactly is the problem?  All you should have to do it plug the ethernet cable into your computer, and then run dhclient to get an IP address.  That's all it's ever taken for me on Comcast.[/QUOTE]

Same here with charter.

Are you congiged fro dhcp?Who is your provider?

---

### Post by defkewl on 2005-05-07
No we get the IP address from the ISP

What's so funny is that I can ping to the modem but I can't ping to the ISP gateway.
My IP : 202.169.231.201
The ISP gateway: 202.169.231.1
When I ping the ISP gateway it said: Destination host unreachable. How could this be possible when my ip and the isp gateway has the same class?

I have started /etc/init.d/networking too
I even turned off iptables

Still could not connect to the internet. :(

---

### Post by defkewl on 2005-05-08
I've already identified the problem and fixed it. All you need to do is uncheck the configuration > enable dhcp server from the cable modem ip address. I need to do this since the ISP already gave me an Ip address.

---

### Post by rasgward on 2006-08-24
I just got internet switched from Ntelos DSL to Adelphia cable internet. I don't know the specs for the Cable service, like DNS and all that stuff. When the distro was installed I already had the DSL connected and it auto configured it. Now, I have this Surfboard 5100(actually I picked up a 4100 from a Goodwill Thrift Store two days ago for $6, so I will be using this instead of the cable company rental modem.) Anyway, this seems to be the best thread for me to try what is suggested. I am not in front of my computer at home, so i will try when I get back. Up to this point I have had no success, due to lack of information I needed to have given the computer...hostname, etc. -Greg
If what is already posted is not what I need, can someone direct me in a good way.

---

