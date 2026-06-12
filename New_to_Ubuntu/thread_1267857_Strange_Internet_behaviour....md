---
title: "Strange Internet behaviour..."
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Jancarel on 2009-09-16
Dear Ubuntu Friends,

Since a few months I am having problems with my Internet access. I connect via a cable modem and have a hardware router/firewall installed. This setup has been working fine for years. Beginning of June, overnight, I am having Internet problems with both connected computers. The computers are hardwired, no wireless LAN. For instance, I am getting the message that a new software update is available. When I try to install this update, the computer cannot find the source of this update. It looks as if the Firewall blocks the site. In the mean time I have tried three different Firewalls, same results. When I remove the Firewall it seems to work fine. My question is now: why has this allways worked, with Firewall installed, until June. I called my provider and they say that when it works without Firewall, the problem is not on their side. I am just puzzled why this happens. Thanks for your help...

Jan

---

### Post by Cypher on 2009-09-16
Which site is it accessing and getting the error from? You can drop to the terminal and type "sudo apt-get update" and "sudo apt-get upgrade" to see what happens and cut-n-paste the output so we can help you specifically..

Regards

---

### Post by LewRockwell on 2009-09-16
> **Jancarel said:**
> Dear Ubuntu Friends,

Since a few months I am having problems with my Internet access. I connect via a cable modem and have a hardware router/firewall installed. This setup has been working fine for years. Beginning of June, overnight, I am having Internet problems with both connected computers. The computers are hardwired, no wireless LAN. For instance, I am getting the message that a new software update is available. When I try to install this update, the computer cannot find the source of this update. It looks as if the Firewall blocks the site. In the mean time I have tried three different Firewalls, same results. When I remove the Firewall it seems to work fine. My question is now: why has this allways worked, with Firewall installed, until June. I called my provider and they say that when it works without Firewall, the problem is not on their side. I am just puzzled why this happens. Thanks for your help...

Jan

not enough specific information for anything other than wild speculation and fruitless assumptions

.

---

### Post by bigboy_pdb on 2009-09-16
What do you mean by three different firewalls? Are they all software firewalls or are you using some combination of software firewalls and a router with a firewall?

Also, have you tried pinging the router ("ping 192.x.x.x") and outside of the network (ie. "ping google.com")?

Another thing that you can try doing is to use a live CD and see if you can get an internet connection with that.

---

### Post by superprash2003 on 2009-09-16
what  hardware firewall are you using?

---

