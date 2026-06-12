---
title: "network and wifi card = 2 different routes"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by luc.oger on 2007-06-08
I am using two different connexions: a network cable one in one site and a wireless one in another site
the network connexion is defined with fixed IP, DNS and gateway but the wireless one is fully dhcp with other DNS and gateway.
A large part of the parameters can be easily defined for each ethernet ID but not the gateway...
can someone help me defining the right route files

---

### Post by Andra on 2007-06-08
sorry, what's that you cannot set, in what case you encounter a problem?

---

### Post by luc.oger on 2007-06-12
I need to define the correct parameters of the route inside the file in order to not having to correct the gateway eachtime when I move from wired connexions with fixe IP at work and  wireless DHCPd connexions elsewhere (home or in travel)

---

### Post by Andra on 2007-06-13
what do you use to set these parameters?
What's in /etc/network/interfaces file?
I don't have an Ubuntu computer where I would use configuration like you describe but otherwise it works (gateway address is received by dhcp).

---

