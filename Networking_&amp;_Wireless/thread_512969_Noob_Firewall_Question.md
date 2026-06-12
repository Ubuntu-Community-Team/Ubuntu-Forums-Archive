---
title: "Noob Firewall Question"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by nomaam on 2007-07-29
Hello:

I am very new to the Ubuntu world and am trying to get a network connection working between two computers in my home (working through a wired router). One computer is running windows and the other Ubuntu. Both computers have a MySQL Server running. From the windows computer I would like to make a remote connection to the MySQL Server on the Ubuntu system. 

I am using SQLyog to make the connection. I receive an error telling me I am unable to make a connection on the given IP address. 

My question is what kind of Firewall rules should I have to allow a remote access?

I am using Shorewall and have added the following rule to allow me to connect:

MySQL/ACCEPT  Source: Firewall   Zone: loc   Source ports: Any  Destination ports:  3306

Could someone give me some tips on what I am doing wrong and what would be the correct firewall rule to allow me to connect?

Thanks.

Note: I have no intention of connecting to either computer from the web. Just within my own home network.

---

### Post by scrooge_74 on 2007-07-30
Never got the hang of Shorewall, Firestarter seemed to be easier for me.  Try telling it to acept conections from a given address

---

