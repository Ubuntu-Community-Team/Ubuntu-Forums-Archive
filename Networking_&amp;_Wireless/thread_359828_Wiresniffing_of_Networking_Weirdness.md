---
title: "Wiresniffing of Networking Weirdness"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by grmbrand on 2007-02-12
I'm running Xubuntu 6.10 on a laptop. From my home LAN this morning I had no difficulty navigating out to web sites outside of my home LAN. From my office LAN I can't get to external web sites but have no trouble hitting intranet websites and no trouble doing things like Telnet, FTP and SSH to external hosts. Note that the five other machines in my cubicle, running various flavors of Windows, Linux and Unix, are not having this problem. Our IT department does not have any restrictions that are preventing this communication.

When I run wireshark from both the laptop and other machines on the same hub, I see that the laptop correctly resolves the target host name ([www.google.com](www.google.com) is resolved to an IP address) and starts sending out TCP SYNs to the google address. The latop never receives an ACK from google.

If anyone is interested in looking over the trace file, let me know. None of the recently suggested IPv6 hacks seems to make a difference one way or the other. My best guess is that perhaps the SYN is malformed, though an examination in Ethereal yields no obvious anomalies.

One interesting difference: when I nslookup on Google, I get the following:

> 
Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.161.99
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.161.147
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.161.104


My PC uses the .147 address in its SYN and subsequent communications with Google, but my laptop uses the .104 address. Could there be something to that? Is the laptop IP stack using the wrong address?

---

