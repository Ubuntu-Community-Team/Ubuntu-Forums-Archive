---
title: "figthing with firewall configuration and samsung network printer"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by Pitero on 2016-06-16
Hi,

I'm new here and it's my first post thus I would like to say Big Hello to all members. :) Moreover I'm quite new Ubuntu user thus I need clear answers for my questions. Can I count on you? :) Big thank you in advance. :)

Getting to the point. I've configured my Samsung SCX-3205W printer and scanner and everything worked fine until I've turned on firewall. After some forums reading and some fighting I've discovered that it's sufficient to add the following rule to graphical Gufw:

Policy: allow
Direction: In
Interface: All Interfaces
Log: Do not Log
Protocol: Both
From: 192.168.8.20 (my printer ip) Port: empty
To:  empty Port: empty

And to set Outgoing default policy to Allow.

However when I set Outgoing default policy to Deny it stopped to work.

I've expected then adding a new simple rule would be enough

Policy: allow
Direction: Out
Interface: All Interfaces
Log: Do not Log
Protocol: Both
From: empty Port: empty
To:  192.168.8.20 (my printer ip) Port: empty

However it doesn't work. Printer/scanner is not detected. :( Of course I could set default outgoing policy to allow but I would like to understand how the firewall in Ubuntu works. Why denying all out traffic and setting one rule as some kind of exception doesn't solve problem? It doesn't seem that there is any conflict with other rules (all other rules are allow type only). I was wondering perhaps it's somehow related with v6 and I should add also similar rules for v6?

And the end one small additional question - where gufw and ufw keeps all the rules? In what file? (ex. if I would like to backup it)

---

### Post by Pitero on 2016-06-17
One thing more, before printing starts, there are some strange broadcast messages (according to /var/log/ufw.log), examples:

Jun 16 21:52:05 m kernel: [ 7170.219737] [UFW AUDIT] IN= OUT=wlp2s0 SRC=192.168.8.2 DST=255.255.255.255 LEN=43 TOS=0x00 PREC=0x00 TTL=64 ID=62098 DF PROTO=UDP SPT=33292 DPT=3289 LEN=23 
Jun 16 21:52:05 m kernel: [ 7170.219742] [UFW ALLOW] IN= OUT=wlp2s0 SRC=192.168.8.2 DST=255.255.255.255 LEN=43 TOS=0x00 PREC=0x00 TTL=64 ID=62098 DF PROTO=UDP SPT=33292 DPT=3289 LEN=23 
Jun 16 21:52:05 m kernel: [ 7170.219749] [UFW AUDIT] IN=wlp2s0 OUT= MAC= SRC=192.168.8.2 DST=255.255.255.255 LEN=43 TOS=0x00 PREC=0x00 TTL=64 ID=62098 DF PROTO=UDP SPT=33292 DPT=3289 LEN=23 
Jun 16 21:52:06 m kernel: [ 7171.223617] [UFW AUDIT] IN= OUT=wlp2s0 SRC=192.168.8.2 DST=255.255.255.255 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=62269 DF PROTO=UDP SPT=45676 DPT=1124 LEN=45 
Jun 16 21:52:06 m kernel: [ 7171.223623] [UFW ALLOW] IN= OUT=wlp2s0 SRC=192.168.8.2 DST=255.255.255.255 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=62269 DF PROTO=UDP SPT=45676 DPT=1124 LEN=45 
Jun 16 21:52:06 m kernel: [ 7171.223633] [UFW AUDIT] IN=wlp2s0 OUT= MAC= SRC=192.168.8.2 DST=255.255.255.255 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=62269 DF PROTO=UDP SPT=45676 DPT=1124 LEN=45

I'm just wondering what to do with these broadcast messages. Perhaps it's possible to block them and still having printing active?

---

### Post by SeijiSensei on 2016-06-17
You probably need to permit traffic to and from the 255.255.255.255 broadcast address. 

Is this machine connected directly to the Internet, or is it behind a firewall router?  If the latter, I don't see much value in running a firewall on the computer itself.  All my machines run without firewalls, and I've never had a security problem in decades.

If it's a laptop, and you use it in insecure locations like a coffee shop, then you should turn on the firewall.

---

### Post by Pitero on 2016-06-17
It's laptop and I would prefer to keep firewall on. I'll try with allowing broadcast address but I'm wondering why printing driver requires sending broadcast if it has ip adress given? Any explaination?

---

### Post by Pitero on 2016-06-17
Ok, allowing broadcast messages to ip 255.255.255.255 to destination ports 3289, 1124, 161 (for samsung scx-3205w printer) helped. But still I'm very interested is there any possibility to work without these broadcast messages. Moreover I'm wondering if this configuration could be improved, thus any comments/suggestions are still welcomed.

---

### Post by SeijiSensei on 2016-06-18
I believe it is the method by which CUPS locates printers on the network. 

Also DHCP requires broadcasts to locate the DHCP server.

---

