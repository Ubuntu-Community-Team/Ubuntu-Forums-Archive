---
title: "share internet connexion for 2 PC"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by jrev on 2005-06-19
Hi all,

I cannot see in the unofficial guide for Ubuntu Hoary 5.04 the way to share an internet connection ...

I connected my 2 PC through a R45 câble and the ping transmission test is good both ways I have no firewall or anything special ...

now a couple of  questions :

1)   which application must be installed for a super-mini sharing ?
2)  Is the type of sharing independent of the type of connection ? (dialup or ADSL)
3)  Could we get an example on Ubuntu ?

Thanks to share your experience & suggestions  O:)

---

### Post by defkewl on 2005-06-19
I use iptables for sharing my internet connection here. 

apt-get iptables first

when it is installed use this command:
$ iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

---

### Post by jrev on 2005-06-19
Thanks for your answer Defkewl,

I have done it on the gateway PC 
what shall I do on the client PC now ?

I noted that when the ethernet connection and the modem connection are on at the same time, I cannot read the web pages on the PC server

I need to find a proper tuto on this matter ... O:)

---

