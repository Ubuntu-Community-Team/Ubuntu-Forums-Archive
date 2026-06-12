---
title: "Squid, DansGuardian, router"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by michio on 2008-09-14
Hey everyone I am a pretty big noob so you guys might have to explain things step by step to me. 

I have set up on my 7.10 server box, Squid3 and Dansguardian. I currently run a wrt54gs with tomato. 

so it goes net ---> router ---> server. 

This setup was mainly to help block ads for everyone on my network as well as i suppose save a little bandwidth. Squid3 should be setup to be transparent. I did very little dansguardian configgin' just basically commented out the configured command.

I added 3 iptables commands to my tomato script (firewall) 
```
iptables -t nat -A PREROUTING -i eth0 -s ! 192.168.1.10 -p tcp --dport 80 -j DNAT --to 192.168.1.10:3128
iptables -t nat -A POSTROUTING -o eth0 -s 192.168.1.0/24 -d 192.168.1.10 -j SNAT --to 192.168.1.1
iptables -A FORWARD -s 192.168.1.0/24 -d 192.168.1.10 -i eth0 -o eth0 -p tcp --dport 3128 -j ACCEPT
```
192.168.1.1 = router
192.168.1.10 = squid box

It doesn't block ads. So this basically leaves me not knowing if the iptables commands aren't forwarding correctly or my squid setup isn't correct or possibly dansguardian isn't functioning as it should. 

I would like to know if there is a way I can test to find out exactly where my problem is occurring and then ultimately what I can do to fix it.

thanks in advance.

---

