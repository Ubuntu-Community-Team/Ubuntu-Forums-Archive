---
title: "Dynamic IP Address DDoS"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by Nikola_Petkovic on 2015-01-17
Hi everyone, sorry if i'm posting in the wrong topic, i'm quite new here.
Currently i just bought a new Ubuntu VPS with SSH access, however, there is a person which keeps ddosing my apache2 server with a dynamic ip address.

The ip seems to keep starting with 108.162 each time. Can i use iptables to block this somehow?

---

### Post by Lars Noodén on 2015-01-18
Is the attack coming from that one network and is the load it imposes in Apache itself (or its scripts) and not just on the network?

If so then you can use [whois](http://manpages.ubuntu.com/manpages/trusty/en/man1/whois.1.html) to find the network and then enter that into UFW.  The second line in whois' output should give you the CIDR address, something like  108.162.16.0/29, depending on which IP you put in.

---

