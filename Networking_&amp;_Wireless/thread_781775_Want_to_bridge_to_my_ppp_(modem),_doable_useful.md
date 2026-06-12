---
title: "Want to bridge to my ppp (modem), doable? useful?"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by drink on 2008-05-04
I want to use a dummy net connection with my ppp for two reasons. Both are related to the fact that the ppp interface is nonexistent when not dialed up, but I do not want to use autodial. There are issues both with firewalling (doesn't really matter which one you pick, they all flail when an interface is missing) and with monitoring, e.g. with ntop - which must be restarted every time an interface disappears (well, when it reappears) if you want to monitor it when it comes back.

I google'd around (not very hard, but I'm on a modem...) :( and didn't find anything that seemed immediately applicable. It seems like I should be able to come up with a set of firewall and routing rules that send my internet traffic to a dummy interface, and I should be able to make ppp0 bridge to that interface. Then a couple of simple iptables statements in the ppp configs to deny all traffic to ppp0 except through the bridge, and it should work, right? Am I missing anything? And more importantly, does anyone have a better idea?

---

