---
title: "iptables port forwarding"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by z662 on 2008-03-25
Hello, I recently turned an old computer into what is now my router, running ubuntu 7.10 server edition.  I am having trouble getting it to forward ports to my webserver on port 1337.  my webservers ip address is 192.168.0.101

Here is my iptables script.  

#my routers eth cards...
#eth0 = internet
#eth1 = internal LAN 192.168.0.1

sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
  sudo iptables -A FORWARD -s 24.144.129.1/1 -o eth1 -j ACCEPT
  sudo iptables -A FORWARD -d 192.168.0.0/24 -m state --state ESTABLISHED,RELATE
D -i eth1 -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j DNAT --to 192.168.0.101:1337
sudo iptables -A FORWARD -i eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT


can someone please help me?

---

### Post by SpaceTeddy on 2008-03-25
```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j DNAT --to 192.168.0.101:1337
```
the rewrite part of the port forwarding looks alright. This will forward anything from the eth0 network on port 1337 to your internal server (why port 1337 ?)

however, that is only half of what you need. If your forward chain is set on drop/reject, you will also need to allow connections to pass through the Forward chain (the paket has only been rewritten - not passed accept yet. i am not sure if the nat table even can accept pakets)...

so, try inserting this rule into your FORWARD chain and see if it works then
```
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 1337 -m state --state NEW -j ACCEPT
```

hope it works :)

---

### Post by z662 on 2008-03-25
thank you, i will not be able to make the changes until later tonight, but i will definitely post and let you know the results.... so just to clarify, do i need this rule at all? or should i just replace the following rule with your second 

sudo iptables -A FORWARD -i eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT

thanks again for your quick response

also, for curiosity sake, my webserver sits on port 1337 because i have armstrong as my ISP and they block all incoming common ports ( it sucks)

---

### Post by SpaceTeddy on 2008-03-25
you need both rules...

the first one is the acctual rewrite - i.e. the forwarding to your internal machine.
the second one lets the pakets the pass to through the paket filter.

---

### Post by z662 on 2008-03-26
unfortunately it still doesnt want to work...here is my updated script

sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
  sudo iptables -A FORWARD -s 24.144.129.1/1 -o eth1 -j ACCEPT
  sudo iptables -A FORWARD -d 192.168.0.0/24 -m state --state ESTABLISHED,RELATE
D -i eth1 -j ACCEPT
  sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j DNAT --to 19
2.168.0.101:1337
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 1337 -m state -
-state NEW -j ACCEPT

---

### Post by SpaceTeddy on 2008-03-26
> **z662 said:**
> 
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

ok, this masquerades anything that going on eth0 and is from your internal network. this rule makes sense...

> **z662 said:**
> 
sudo iptables -A FORWARD -s 24.144.129.1/1 -o eth1 -j ACCEPT

this allows any paket comming from 127.255.255.255 or lower and goes to the internal network. This rule does not make any sense to me, especially the definiton of the ip seems somewhat... strange. What is the purpose behind this ?

> **z662 said:**
> 
sudo iptables -A FORWARD -d 192.168.0.0/24 -m state --state ESTABLISHED,RELATED -i eth1 -j ACCEPT
this will allow any paket from the internal network which has previously had a connectons to pass as long as it comes from the internal network. This makes sense, but does NOT allow incomming connections... i think this is where i messed since i did not read this properly... 

> **z662 said:**
> 
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j DNAT --to 192.168.0.101:1337
this is the port rewrite... looks good

> **z662 said:**
> 
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 1337 -m state --state NEW -j ACCEPT
when i wrote this i did not take your other rules into account... or rather their restrictions... it still applies, but there might be one more thing you need to do... 



i will write down the ruleset as i would define it... also, i will leave the rule out that i do not understand. if it is needed then just paste it back in... 

> #delete anything in the Forward chain
iptables -F FORWARD
#set default policy for Forward to drop (specificially allow)
iptables -P FORWARD DROP

#rules
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j DNAT --to 192.168.0.101:1337
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -m state --state NEW -i eth1 -o eth0 -s 192.168.0.0/24 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 1337 -m state --state NEW -j ACCEPT


i think that is it... also, when applying these rules and they do not work again, try to set your default policy to ACCEPT and test again. this way the FORWARD chain does not get in your way and you can test the plain rewrite. Of course, that is not a permanent state, but for a short test it should not do any harm :)

[EDIT]
why is your webserver running on 1337 ? why not on 80 ?

---

### Post by z662 on 2008-03-30
Thanks for the response, sorry I have been pretty busy with school work lately and havent really had time to mess with the iptables....my webserver runs on port 1337 because my ISP blocks all incoming ports below 1024. I flushed my rules and applied your new changes but it still is not working...I am more confused now than ever with these rules...they just refuse to work for me. In regards to your question of why I had that rule in there, I just tried following an example I found online with a Debian system...Can anybody help me get these rules to work?????  Thanks

---

### Post by SpaceTeddy on 2008-03-30
mhm - the first thing we should make sure is that the pakets are really reaching your router. once it is known we have a working connection the port forwarding is the second step.

so how about you replicate the configuration of your webserver to the router and run it there on port 1338. if you can reach that you know at least that the connection it reaching your computer.

please keep me updated on how that goes

PS: as an alternative you can also use the ssh server and rewirte it's port in the /etc/ssh/sshd_config if you do not want a full blown webserver :)

---

### Post by z662 on 2008-03-30
Ok, what i did to test it was instead of using my url:1337 to reach it, i just put in the local ip 192.168.0.101:1337 and my webserver will work fine...so i know everything is properly setup other than my router...it just refuses packets coming in from the internet.

---

### Post by z662 on 2008-05-12
does anyone have any ideas?

---

### Post by leptogenesis on 2008-06-04
I was having trouble similar to this, and it turned out to be unrelated to iptables.

Two things you may want to look at.  First, try adding some logging, to see whether the packets are getting through:

```
#delete anything in the Forward chain
iptables -F FORWARD
#set default policy for Forward to drop (specificially allow)
iptables -P FORWARD DROP

#rules
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j LOG
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 1337 -j DNAT --to 192.168.0.101:1337
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -m state --state NEW -i eth1 -o eth0 -s 192.168.0.0/24 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 1337 -m state --state NEW -j LOG
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 1337 -m state --state NEW -j ACCEPT
```

The log messages should show up in /var/log/kern.log - for each connection attempt, there should be two messages for packets very close in time.  The first should have the DST=[Router's IP Address], and the second should have DST=192.168.0.101.  If that's the case, then it's likely that iptables is doing the right thing.  If not, post what does get printed.  Also, post the output from 'sudo iptables -L' and 'sudo iptables --table nat -L'

From there, try using wireshark.  Wireshark just listens to every packet that goes across the wires; hence, you can see if the packets are making it onto the local network.  In my case, I discovered that the firestarter firewall on the real destination computer was blocking the packets.  This surprised me greatly, because this computer had been behind a different router before and hadn't had any problems with port forwarding.  Firewalls can do odd things I guess...

---

