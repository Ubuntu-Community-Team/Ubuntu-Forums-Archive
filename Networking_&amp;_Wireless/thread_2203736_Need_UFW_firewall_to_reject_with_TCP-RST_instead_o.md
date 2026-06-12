---
title: "Need UFW firewall to reject with TCP-RST instead of ICMP"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by dfjarvis03 on 2014-02-04
Good evening to any one interested enough to read this.

It's been many years since I have played with a linux firewall... My beginnings were with ipchains right before iptables became the new thing, at which point I started using it... but that was a long time ago, and I haven't had the need to stay up to date. Now that I have found the need, I've found that ufw seems to be the new deal, and that it simply wraps iptables in a more user friendly way. Fine, I can deal with that... maybe.

Currently, I am planning on poking a hole in the firewall on my broadband router to forward a port to a back end linux host (easy and tested), but I do not want this port to show up in scans... so I though port knocking would be a good idea (easy and tested). I'm 99% to where I want to be.

To reach 100%, I need the firewall on my linux box to reject connections the same way the firewall on the broadband router does... If I try to access a blocked port on the router, it simply sends a a TCP RST, but if I hit the port that I forwarded, I either get no response (with ufw set to DENY), or I get an ICMP response (with ufw set to Reject).

IPTables allows you to influence the behavior when rejecting connections as documented at [http://www.linuxtopia.org/Linux_Firewall_iptables/x4550.html](http://www.linuxtopia.org/Linux_Firewall_iptables/x4550.html), achieving my goal by passing --reject-with tcp-reset to the rule.

My question is: Is it possible to configure ufw to reject with tcp-reset, rather than ICMP. I am using Gufw on the front-end, so maybe this is over simplifying things.

Thank you in advance for any recommendations or pointers in the right direction (other than google... already tried that, though maybe not hard enough).

---

### Post by tomearp on 2014-02-05
I couldn't immediately see a way to do it with ufw when looking through the [man page]("http://manpages.ubuntu.com/manpages/trusty/en/man8/ufw.8.html"). You might need to go for a more manual approach and use iptables on its own.

One thing that does concern me somewhat is that your router is rejecting packets to closed ports, thus advertising your presence. Assuming you are using NAT on your router I would expect it to implement a default drop policy for unrecognised connections.

---

### Post by dfjarvis03 on 2014-02-11
Hey tomearp,

I was thinking the same thing... go back to my roots and just use iptables directly. Honestly, UFW seems a bit complicated and overkill under the hood, but I can probably learn little from it in creating my chains.

It is certainly a bummer that the router responds with resets. I would prefer for it to drop silently, but couldn't find an option to make that happen..

---

### Post by tomearp on 2014-02-11
Yes, I think UFW has its place for people who just want to have something in place rather than nothing (a bit like Windows Firewall in that respect), but the moment you need something more it's got to be iptables.

If the router is responding to say ports are closed to traffic then it would suggest that there is no firewall running on the router. What make/model is it out of interest?

---

### Post by geopcgeo on 2014-10-20
Are you able to find this option through UFW? Can you please share it.

---

