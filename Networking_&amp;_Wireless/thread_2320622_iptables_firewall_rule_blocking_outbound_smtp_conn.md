---
title: "iptables firewall rule blocking outbound smtp connection --dport or --sport?"
date: 2016-04-15
forum: Networking &amp; Wireless
---

### Post by hillboy2 on 2016-04-15
I'm using phpMailer to send email through my gmail account and I'm also trying to harden up my firewall. The SMTP has been not working after adding firewall rules in particular the default **-P OUTPUT DROP** added once I got all the OUTPUT ACCEPT rules in place. 

The first problem was that to get a DNS resolution of smtp.gmail.com that phpMailer needed I had to open port 53 for udp. That was not obvious however only 5 hours of head banging on desk and now that's working.

Then my output rule for port 465 had to be a "--dport" and not "--sport" like in all the how to instruction found on the internet.

This works: **-A OUTPUT -p tcp --dport 465 -j ACCEPT**

This does not: **-A OUTPUT -p tcp --sport 465 -j ACCEPT**

Can someone explain the logic behind which is the source and which is the destination? Why are all the examples using the one that doesn't work?

---

