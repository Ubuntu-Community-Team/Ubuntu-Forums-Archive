---
title: "Which IPTABLES are correct for using APT with a socks proxy?"
date: 2022-03-11
forum: Networking &amp; Wireless
---

### Post by han85 on 2022-03-11
Hey guys!

Which IPTABLES are correct for using APT with a socks proxy? (with connection tracking)

This?

**iptables -A OUTPUT -s 127.0.0.1/8 -p tcp -m tcp --sport [PORT] -m conntrack --ctstate ESTABLISHED -j ACCEPT**

or?

[B]iptables -A OUTPUT -d 127.0.0.1/8 -p tcp -m tcp --dport [PORT] -m conntrack --ctstate ESTABLISHED -j ACCEPT


[/B]I am a bit confused with -sport/-dport rules (INPUT/OUTPUT) for this scenario.

Only OUTPUT or INPUT rules, or both?

It would be nice if you could tell me which iptables rule is correct/wrong for my scenario with APT (APT updates via a socks proxy).

If applicable, please post here the correct iptables rules for this APT scenario (APT updates via socks proxy).

Thanks all! :-)

---

### Post by The Cog on 2022-03-11
Whether you need to add ACCEPT to OUTPUT rules, INPUT rules or both depends on what you have already configured, because by default nothing is blocked.
It is common practice to allow all processes on the box to talk to all other processes on the same box via the loopback address.
```
iptables -A INPUT -i lo -J ACCEPT
```
You also need to add an OUTPUT clause if you chose to block outgoing traffic as well. 
The nice thing about this is that it covers all protocols and the port number question goes away.

---

### Post by han85 on 2022-03-11
some rules at my iptables:  
[B]iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT[/B]

---

### Post by han85 on 2022-03-11
I would like to have

**iptables -A OUTPUT -o lo -j DROP**

and then add some iptables OUTPUT @ lo rules myself with conntrack.

would it work like this?

[B]iptables -A OUTPUT -o lo -j DROP
iptables -A OUTPUT -s 127.0.0.1/8 -p tcp -m tcp --sport [PORT] -m conntrack --ctstate ESTABLISHED -j ACCEPT[/B]
or this?
[B]iptables -A OUTPUT -o lo -j DROP
iptables -A OUTPUT -d 127.0.0.1/8 -p tcp -m tcp --dport [PORT] -m conntrack --ctstate ESTABLISHED -j ACCEPT


[/B]what still irritates me is[B]

--dport / --sport rules.

[/B]if I want to use loopback e.g. with socks proxy via 't o r' as single rule irritates me[B]
-s 127.0.0.1/8 ... --sport [PORT]
or
-d 127.0.0.1/8 ... --dport [PORT]

[/B]To understand, Socks Proxy runs on loopback and connects to the 't o r' network via OUTPUT rule [PORT] to use Apt Updates over it.then it should be from the iptables rule:[B]

iptables -A OUTPUT -d 127.0.0.1/8 -p tcp -m tcp --dport [PORT] -m conntrack --ctstate ESTABLISHED -j ACCEPT

[/B]This** -s 127.0.0.1/8 and --sport [PORT] **iptables rule would be wrong which I posted here for my scenarion, right?

**-s (SOURCE) + (SOURCE-PORT)** is used for INPUT rules when someone wants to connect to my PC from outside e.g. via the 't o r' network, did I understand that correctly or am I wrong?

when **-s (SOURCE) + (SOURCE-PORT) rule**? 
when **-d (DESTINATION) + (DESTINATION-PORT) rule**?

If you had a moment to explain it to me in a simple and understandable way I would be grateful and happy.

---

### Post by The Cog on 2022-03-11
Why on earth do you want to prevent processes on the PC communicating with each other? Lots of things will break.
You can't block based on source port - the source port is always a random number.

---

### Post by han85 on 2022-03-12
For the reason of security purposes ;-)

My created thread can be considered EDITED.

Have now got it done.

---

