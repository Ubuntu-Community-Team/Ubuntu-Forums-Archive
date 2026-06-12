---
title: "nat server"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by nenduvel on 2007-09-12
Greetings,

I'm trying to get a nat server running on my ubuntu desktop (with 192.168.0.1 and 192.168.150.3) and connect him with another ubuntu desktop(192.168.0.2). I can ping from the 'nat server' to the 'other' ubuntu in both directions, and the nat server has internet access. 

then I activate nat on the nat server by next the rule

iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 192.168.150.100

so that the outgoing connections from 192.168.0.1 will be translated to 192.168.150.100. This doesn't work.

I already tried [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
and [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html) but these where no help for me. (I tried dhcp but static will do just fine)

ip_forwarding is on

root@heverlee-desktop:~# cat /proc/sys/net/ipv4/ip_forward 
1

and i use the same nameserver for both pc's

any suggestions? i will be grateful

---

### Post by robert_pectol on 2007-09-12
This may help you:

[http://rob.pectol.com/content/view/5/28/](http://rob.pectol.com/content/view/5/28/)

You can also install something like dnsmasq on the NAT gateway to provide dhcp and DNS services to your internal host(s).  Good luck.

---

### Post by nenduvel on 2007-09-13
thanks for the info!
The problem was my ip address
The network looked like this

192.168.0.2 --------192.168.0.1/192.168.150.3 ------------------------192.168.150.253
host---------------------nat server---------------------------------------------- router

the outgoing ip address for my nat had to be 192.168.150.3 not 192.168.150.100 because my nat server only had 1 ip address.

your file made me think ;-)

thanks again for the support!

---

