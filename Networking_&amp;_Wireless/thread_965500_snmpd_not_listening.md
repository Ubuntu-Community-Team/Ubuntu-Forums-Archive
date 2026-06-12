---
title: "snmpd not listening"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by westsyde on 2008-10-31
Hello,

I have tried getting snmpd to work on my Ubuntu 8.04 desktop and am stumped. As a newbie, I am willing to bet I may have misconfigured but wanted to see if someone in the forums has ever run into this.

I configured snmp, can do a local snmp walk fine, but dont see port 161 listening. I read somewhere that snmp:all in hosts.allow was something to try but it didnt work for me. I have removed and re-installed to the same effect.

I made a change in SNMPOPTS= SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid $
  {global.ipv4[eth0]}:161 10.1.1.2'

But that didnt work. Although if I remove -smux -p I can see smux on port 199 show up. 

My OS is desktop 8.04 and running a VIA board with two gig lan NICs. Thanks in advance for any and all ideas.

---

