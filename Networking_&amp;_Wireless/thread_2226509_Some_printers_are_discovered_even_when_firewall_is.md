---
title: "Some printers are discovered even when firewall is dropping traffic"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by GigabyteProduction on 2014-05-27
While on a network with iptables set to block all input and output except when it's ICMP or when it's loopback and I was watching xubuntu 14.04's printers window and it was finding like 6 out of the 20 printers that are on the network. I didn't test printing to them as I have iptables set to drop all for a reason but they were still being discovered. All of the printers had a location of about a 6 digit number like ipp://115462/ (it may be one digit more or less). I looked into ipp and it appears to be based on ip and http, so it should be blocked by iptables, but like i said i didn't want to test printing.

I want to know how my computer was discovering these printers, is there another part of the protocol that runs on layer 2 of the osi model (the layer before that effected by iptables) or can they broadcast with icmp? if it's just an icmp message that's broadcasting the printer's existence then that's fine, but otherwise this may be a hole in my security.

I realize i should have tested whether it was icmp while i was there but i didn't think of that at the time. My printer doesn't seem to be behaving like the others so i guess i'll have to test if it's icmp tomorrow if nobody here has a clue.

---

### Post by ian-weisser on 2014-05-27
Is your iptables really 'drop all' on input and output tables, or are there a few exceptions in there? Like existing connections?
Are you using Samba for network printing, or just CUPS?

If CUPS, look at tcp/udp ports 631, not ICMP.
Can you reproduce the issue while running wireshark or etherape so you can see the network activity?

---

