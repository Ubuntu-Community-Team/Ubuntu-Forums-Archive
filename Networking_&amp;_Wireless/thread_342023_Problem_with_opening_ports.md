---
title: "Problem with opening ports"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by chaffeur on 2007-01-19
Hi!
I'm using kubuntu 6.10 and I've had no problem to forward my netgear WGR614 v4 router's port (it's wireless but I'm using a wire) until some days ago. Suddenly applications like aMule and utorrent ( through wine) which had worked fine stopped working properly ( aMule gets only lowID and utorrent shows a red exclamation point).
I have no idea what might have created this problem but I think it might have something with installing xcfe ( through apt-get install xubuntu-desktop) to do. I did this some days ago and before this i've had no firewall or similar but i'm guessing xcfe might had installed this.

All help is appreciated. Thank you!

*** NOTE: Solution found! See my last post. ***

---

### Post by kingmonkey on 2007-01-19
Has your IP changed?

---

### Post by dannyboy79 on 2007-01-19
im sure that your ip address has changed. so whatever ip you're forwarding to within your router, that's what the ip has to be on your computer.
Example: In router config, you tell it to forward ports 6881 thru 6891 to ip 192.168.0.4

now the computer that you run utorrent on has to be ip 192.168.0.4 or it won't work. the other obvious thing is if you have any firewall rules. sudo iptables -L should have nothing or else it should have ports 6881 thru 6891 open. That should do it.

---

### Post by chaffeur on 2007-01-19
Thanks for replying.

I also thought my ip had changed (as I'm using DHCP) but It's still the same.
iptables -L gives this

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


which means no rules, right?

---

### Post by chaffeur on 2007-01-19
HALT!

It seems as I've found the solution for this problem...
Pull the plug and reinsert in the netgear router fixed it all. VERY silly.

Well, sometimes the solutions comes easily.
Sorry for bothering you. Thanks for your time.

---

