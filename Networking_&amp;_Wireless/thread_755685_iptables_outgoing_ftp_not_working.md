---
title: "iptables: outgoing ftp not working"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2008-04-15
I just set a firewall with iptables (I will atach my script if needed).
I have two eth cards (eth0 LAN, eth1 Internet)
If am forwarding traffic for dns, pop and smtp, etc and all works fine, except...
I can not connect with outgoing ftp.
I do:
```
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 20:21 -j ACCEPT
```
I get the prompt for the password form ftp sites, but once filled, I can get no connection.
Is there any aditional rule I have to add to allow ftp outgoing connections?
Thanks a lot!

---

### Post by SpaceTeddy on 2008-04-15
ftp is a shitty protocoll when it comes to firewalls. Sorry to say it like that, but that is my opinion :)

what you need to do is enable connction tracking, load the contrac_ftp modules, use statefull firewall rules and allow related connections to pass...

in other words, you need something like this:

```
 sudo modprobe ip_nat_ftp ports=21
sudo modprobe ip_conntrack_ftp

sudo iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -p tcp -m tcp -m state --dport 21 --state NEW -j ACCEPT
sudo iptables -A FORWARD -p tcp -m tcp -m state --sport 20 --state RELATED -j ACCEPT
sudo iptables -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT
```

this will load the neded modules, and allow ftp connection (active and passive) to pass through your firewall... or so they work for me :) if you still run into problem, don't hesitate to ask :)

---

### Post by jmvidalvia on 2008-04-15
Worked!
I should have posted it some hours before! I would have saved a couple of them.
I thought I was becoming silly...
Why isn't it explained anywere, in the web: you can't imagine how many sites I visited and how many test I did.
So simple: trying to go out for ftp!
Thank you very much!!!:D

---

