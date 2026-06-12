---
title: "100% packet loss when pinging"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Skardal on 2007-09-09
I have a little problem now; I'm unable to ping hosts on the internet. I have tried from several machines on the local network, but all of them gets 100% packet loss. 
I've been looking at the routers firewall settings to see if there was an option that made it block them, but I can't find anything...

Just wondering...is there a specific port that ping uses, so that I may have forwarded this port, and hence the reply never returns to me?

---

### Post by enatiello on 2007-09-09
You're message is a little vague, so I am assuming you have a central firewall and are using NAT within the Trusted side,however most firewalls allow packets back in as long as the traffic originated from within the "Trusted" side of the firewall.  Also, you may want to look at your firewall logs to see if the ping packets are being denied.

---

### Post by Bothered on 2007-09-09
I think ICMP filtering can filter out pinging - you might want to try looking for that.

---

