---
title: "Mac Address Filtering IPTABLES"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-03-27
Hi All,

Just trying to setup a rule in my firewall that allows only certain clients to go through my A/P (ubuntu server)

```
iptables -A INPUT -m mac --mac-source ! 00:14:BF:7A:4D:2D -j DROP
iptables -A INPUT -m mac --mac-source ! 00:18:DE:A5:00:41 -j DROP

```
If I understand correctly what I have gleaned from reading around these rules should allow only these two mac addresses and drop everything else??? I gather this is what the  exclamation mark is for .......... is it in the right place? (I couldn't find the exact syntax usage in these examples.....:( )

I restart my firewall script and unfortunately it blocks traffic even from my two clients which i thought were allowed if I disable these rules everything is weet again



Any help?????

Greatly appreciated

---

### Post by andytof47 on 2007-03-27
O.k

I've been playing around with this for ages and am ready to admit defeat...........


Basically I want to allow these mac addresses and of course traffic on the server (I use it for browsing)

How would i do this?

Here is my firewall


PLEASE PLEASE PLEASE PLEASE can someone help?

```
iptables -t nat -A OUTPUT -p tcp -m tcp --dport 8080 -m owner --uid-owner squid -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp -m tcp --dport 80 -m owner --uid-owner squid -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080 
#iptables -t nat -A OUTPUT -i ath0 -p tcp --dport 80 -j REDIRECT --to-ports 8080 
#iptables -t nat -A OUTPUT -i eth0 -p tcp --dport 80 -j REDIRECT --to-ports 8080


iptables -I INPUT -p tcp --dport 33000 -j ACCEPT
iptables -I INPUT -p udp --dport 33000 -j ACCEPT
iptables -I INPUT -p udp --dport 5060 -j ACCEPT



# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Always Route Wireless Traffic through
iptables -t nat -A PREROUTING -i ath0 -p tcp --dport 80 -j REDIRECT --to-port 8080

# Always Route Wired Traffic through
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080



# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth1 -o ath0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
iptables -A FORWARD -i ath0 -o eth1 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE


# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward


```

---

### Post by Mr. C. on 2007-03-28
Before embarking on the path to create a firewall, one should become very familiar with the traffic patterns that flow in and out of an interface.

Install and run tcpdump, and start watching the traffic.  This will teach you that there is more to TCP/IP networking than the simplistic approach you are taking.

MrC

---

### Post by andytof47 on 2007-03-28
hey Mrc .........

I'm only after a little help on blocking out the mac's of other computers except the one I want.......not a black belt in Tai-Chi:) 

Anyway I will intall wireshark i think.....but that still doens't help me in the short term..... any links?

---

### Post by Mr. C. on 2007-03-28
But you are asking to break boards with your pinky.  You need at least a green belt.

MrC

---

### Post by andytof47 on 2007-03-29
> **Mr. C. said:**
> But you are asking to break boards with your pinky.  You need at least a green belt.

MrC

well said

---

### Post by flangemonkey on 2007-03-29
I am not a guru, but try removing the space between the ! and the MAC address.
hopefully this should work...

and, there are some harsh people in this thread, generally people on this forum are very helpful :/

Phill

---

### Post by doglikegroove on 2007-03-30
It's a sad state of affairs when a guy who doesn't even use Ubuntu, and just came across the thread on Google, has to register to a forum just to see a guy get help.

Andy,

What you need to understand is that packets continue fall through the filters until there's a match, and stop falling and are filtered as soon as there is one.

Let's look at what your two rule example does...

```

iptables -A INPUT -m mac --mac-source ! 00:14:BF:7A:4D:2D -j DROP
iptables -A INPUT -m mac --mac-source ! 00:18:DE:A5:00:41 -j DROP
```


So,  a packet comes in from :4D:2D. Rule 1 only applies if the address is NOT :4D:2D. This doesn't mean that because it **is** :4D:2D it gets accepted; it only means that it doesn't match the condition, and continues to fall through the ruleset.

Next rule? If you're not :00:41, you get dropped. Well, :4D:2D is not :00:41, so that's a match! Dropped. 

In order to get through both rules and not match and be dropped , a packet would have to be from both :4D:2D **AND** :00:41 at the same time, which ain't happening. 

What you want is to put in your "allows" and then make the last rule drop anything that hasn't matched your allow criteria. Something like this:

 ```

iptables -A INPUT -m mac --mac-source 00:14:BF:7A:4D:2D -j ACCEPT
iptables -A INPUT -m mac --mac-source 00:18:DE:A5:00:41 -j ACCEPT
iptables -A INPUT -j DROP

```


Or better yet, use the -P option to make the default policy of the chain DROP. The policy is what the chain will do if something falls through to the bottom.


 ```

iptables -P INPUT DROP
iptables -A INPUT -m mac --mac-source 00:14:BF:7A:4D:2D -j ACCEPT
iptables -A INPUT -m mac --mac-source 00:18:DE:A5:00:41 -j ACCEPT

```


Hope this helps.

---

### Post by andytof47 on 2007-04-01
you are a legend thanks for that insightful post of how and why!!!!!


seriously that was fantastic

---

### Post by flangemonkey on 2007-04-03
indeed, tahnks from me too

you have forwarded my knowledge of iptables far more than I have managed so far myself :)

Have a gold star :KS

---

