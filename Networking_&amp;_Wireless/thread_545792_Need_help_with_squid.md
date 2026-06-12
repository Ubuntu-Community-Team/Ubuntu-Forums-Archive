---
title: "Need help with squid"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by gendi on 2007-09-08
hi im a n00b here and i need some help setting up squid, i can work somethings out but iptables confuse the hell out of me.

i have a server in the IT lab at tafe which has onboard NIC and a PCI NIC, the onboard is connected to the net and i have another computer connected to the PCI NIC which i have a dhcp server supplying it with a IP address, i have set squid to act as a transparent proxy but when i try to surf the net on the dhcp'd machine it doesnt go anywhere.

from what can understand i need to set all traffic coming in from eth0 (dhcp server NIC) to go out through eth1 (net NIC) but i cant figure out howto get it to work, can anyone help me set this up?

sorry if that confuses anyone lol i really need some help.

---

### Post by kidders on 2007-09-09
Hi there & welcome,

> **gendi said:**
> sorry if that confuses anyone lol i really need some help.Your post *is* sort of confusing, but let's see if I have it right...

It looks as though you have a Linux box with 2 NICs, one of which is connected to the internet. The other is set up to DHCP-assign addresses to a small LAN. Rather than letting your DHCP clients access the internet on their own, you want to transparently proxy them using a squid install on the server.

Assuming I'm following you, you need to configure your server to redirect all packets arriving from the LAN & destined for port 80 to your proxy. There is a reasonably good overview at [http://tldp.org/HOWTO/TransparentProxy.html](http://tldp.org/HOWTO/TransparentProxy.html). Essentially...[LIST]
[*]Take a quick look at your iptables NAT rules, and be sure nothing in them might take precedence over a new rule you add to govern your proxying.
[*]Figure out the network interface the requests you want to proxy are coming from (let's call it eth1), and the local port your squid is listening on (let's call it 3128).
[*]Add an iptables rule to redirect TCP packets coming from eth1, and destined for port 80 to port 3128 instead.[/LIST]```
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
```Your suggestion about directing outbound traffic from one network interface to the other is close to what you would do if you *didn't* want to proxy your DHCP clients' web traffic ... a vastly more stable approach, but you wouldn't get to proxy the connections people were making.

I hope something in this post answers your questions. If not, be sure to let me know!

---

### Post by gendi on 2007-09-10
hey thanks mate for the info will try it out on wednesday.

it part of my networking project at TAFE but the teacher wont help, he just says to search the net and that so i learn by myself.

again thanks will reply if i cant figure it out.

---

### Post by kidders on 2007-09-10
Ahhh... In that case, transparent proxying has a number of characteristic shortcomings that are probably worth being aware of. Normally, posters requesting information on the technique are already familiar with them, but since your teacher is using it as a learning exercise, you might not be.

One is related to the fact that web browsers don't know the connections they make are being proxied, which can result in anomalous behaviour. Another has to do with HTTP over SSL. Transparently proxying HTTPS, also known as a "man in the middle attack", is not possible.

---

