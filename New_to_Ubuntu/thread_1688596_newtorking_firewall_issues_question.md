---
title: "newtorking /firewall issues /question"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by judderwocky on 2011-02-15
I'm trying to set up a custom firewall, and I want to use the opportunity to learn Iptables. 

However I am running into a very basic problem with determining the policy settings.

i want the default policy to:

iptables -P OUTPUT DROP

and I want to give access to myself by doing the following:

[B]iptables -A OUTPUT -p tcp --dport 80  -j ACCEPT

or 

iptables -A OUTPUT -p tcp --dport 80  -m owner myuserid -j ACCEPT

[/B]But that it isn't working. It just blocks everything including the www access.


Am i misunderstanding the usage of the policy ? I've read a bunch of tutorials and man pages but for some reason this policy concept isn't sticking. 

It thought the -A / -j was supposed to make this processed before the default (I.e. the end of your rules list, if nothing else applied)... however it appears it evaluates the rules, and then the policy on top of all of it.

I notice when ufw sets up its firewall, it definitely has the default policy for OUTPUT set to drop (b/c i put it that way) and that when I manually add these extra ports open, it adds those as additional chains.

So i created a new chain, but the policy default still is blocking everything::::

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         

Chain basic (0 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www

---

