---
title: "ABP Easylist + iptables, possible?"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by AVT- on 2008-09-19
Good morning,

Firstly, if it's against the forum's rules to post about ad blockers, as it is on some other forums I visit, I'd like to apologize ahead of time. I'll remove this if someone notifies me that this is the case.


What I have working now:

Mythbuntu system, basically acts as a router. Internet = eth0, Ethernet = br0 (eth1,eth2,ath0). This currently works.


What I'm trying to do:

Block advertising websites from all the computers that may access the internet through this machine, using [Easylist]("http://easylist.adblockplus.org/adblock_rick752.txt").


I'm thinking this may be possible by writing a script:

1) Checks Easylist to see if it's been updated.
2) If no, stop running
3) Delete everything it's blocked on previous run
4) Block everything that's in the list
5) Repeat every 24hrs, and on startup


Unfortunately that's where my ideas end. The only scripting language I'm familiar with Lua. From here, I have absolutely no idea what to do. Maybe someone can send me in the right direction?

---

