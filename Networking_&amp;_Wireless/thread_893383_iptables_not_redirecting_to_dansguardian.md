---
title: "iptables not redirecting to dansguardian"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by kung fu buntu on 2008-08-18
I have installed dansguardian (and squid since its a dependency).
I have configured DG and it works when I set the browser to user 127.0.0.1:8080 as a proxy.
I am now trying to make it all transparent by making iptables to redirect the traffic.
For some reason it's not working.

iptables -t nat -A PREROUTING -i $NIC -p tcp --dport 80 -j REDIRECT --to-port 8080

I'm using the web browser, iptables and dansguardian on the same computer. But the final objective is to affect only an internal NIC (that is were other computers connect to mine).

Why doesn't this work?

I haven't configured squid, because I don't really need it. But is this the cause? DG is already working without it if I configure the proxy in the browser.

Thanks

---

### Post by kung fu buntu on 2008-08-18
Anyone?
Some help? :(

---

### Post by SpaceTeddy on 2008-08-19
mhm - the rule should work. Can you run a tcpdump on your $NIC to see if the packets are rewritten ? also, are there any rules in INPUT that would block these requests to port 8080 (This is not FORWARD anymore).
other than that, i can only see that your directive is --to-port while the iptables man page states that it should be --to-ports
don't know if that makes a difference. Otherwise, your rule should work. OR i don't see why it should not work... 

:confused:

---

### Post by kung fu buntu on 2008-09-20
> **SpaceTeddy said:**
> mhm - the rule should work. Can you run a tcpdump on your $NIC to see if the packets are rewritten ? also, are there any rules in INPUT that would block these requests to port 8080 (This is not FORWARD anymore).
other than that, i can only see that your directive is --to-port while the iptables man page states that it should be --to-ports
don't know if that makes a difference. Otherwise, your rule should work. OR i don't see why it should not work... 
:confused:

I used wireshark and filtered results with
tcp.port == 8080
But had no hit... It seems nothing is being rewritten.

BTW, what I meant by not working is that traffic isn't redirected, that means that I can access the web directly.

I have INPUT rules (with default policy to DROP), but like I said, I have web access, so I don't think nothing is being blocked.

I also have one rule in nat because my computer is also acting as a gateway.


Does anyone knows what is wrong?
How can I redirect traffic from NIC:80 to localhost:8080 ?
Thank you.

---

### Post by kung fu buntu on 2008-09-21
Anybody....? :'(

---

### Post by kung fu buntu on 2008-09-23
*bump* :(

---

### Post by NoReflex on 2008-09-23
Just a wild and probably stupid guess here : are you sure $NIC points to the interface you want? Maybe posting the output of sudo iptables -L will help identify the problem.

Best wishes,
NoReflex

---

### Post by kung fu buntu on 2008-09-24
I have 2 NICs.
One is connected to the internet and the other works as a gateway to a second computer.
I only want to redirect/filter the traffic of the second computer, so that would mean the NIC that connects to it.
Or am I missing something?

Can this be something to do with my other iptables rules? I have one Postrouting rule in the iptables nat ruleset.

---

