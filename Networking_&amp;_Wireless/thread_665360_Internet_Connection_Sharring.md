---
title: "Internet Connection Sharring"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by csurlee on 2008-01-12
Hello all, 
I'm new in ubuntu server.
I have 2 compurets and one ubuntu server 7.10 on laptop connected with a switch. What i want to do is to make a internet connection sharring on the server and to use the internet on the computers true the server and for every computer i have one ethernet card. i dont want to by anything like a router or a ethernet card
So...
 Internet
 |
 |     Comp1
 |       |
 switch 
 |       |   
 |     Comp2
 |
 |
  Server

I hope do you understand what i want to do :) thanks for any information

---

### Post by amo-ej1 on 2008-01-12
What you're trying to do is called 'NAT' (network address translation), you basicly want to route traffic through PC1 from PC2 but it should go out with the public ip address of PC1.
[http://www.howtoforge.com/nat_iptables](http://www.howtoforge.com/nat_iptables)
Simply google (or search the forums) for ubuntu and nat and you'll end up seeing pages like this: 

[http://www.howtoforge.com/nat_iptables](http://www.howtoforge.com/nat_iptables)

But it comes to:
a) configuring the ethernet interfaces on PC1
b) enabling forwarding on PC1 
c) executing some iptables rules to define the NAT.

---

### Post by csat on 2008-01-12
Isn't it better replacing switch with a router?

---

### Post by csurlee on 2008-01-17
thanks  amo-ej1for the info :)

and csat i dont have the money for the moment to bay a router :)

---

