---
title: "I can't ping my router nor another computer in my LAN"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Ferio on 2008-03-31
Hello, I want to share files (and play *Battle for Wesnoth*) between this computer I'm in right now and another one. Both of them are running Ubuntu 7.10, and they share Internet connection through a router; both are configured to have a static IP in the LAN (mine is 192.168.1.2, and the other's is 192.168.1.3); router's default gateway is 192.168.1.1.

The problem is that I can access the webpage to setup the router using the default gateway, but I can't ping it or the other computer. I don't know if it's some security measure from the router, or maybe it's a Firestarter/iptables-related issue. All I know is that networking is not my strong point, and I'd like to get some information if possible to solve this little problem. Thank you in advance.

PS: I've googled for it and searched in the forums before I've made the decision to post; although I've found some similar questions, no one of them has solved my problem. I hope to find the light with you!

---

### Post by akks on 2008-03-31
Since you can acces it through the web page and not through ping check if your router is blocking ICMP requests  through some default firewall rules.

---

### Post by Ferio on 2008-04-03
That was it, indeed! I'll try to get on by myself with the file-sharing thingy, and I'll post if I find some problem. Thank you very much!

---

