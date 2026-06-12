---
title: "port forwarding lo to eth0"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by kingtiger01 on 2008-11-06
Hello all. Ive got a Some What 'Unique' Problem.

I have a Some what large network. consisting of 35+ i686 boxes that are part of a Beowulf Cluster.(ethernet 1000Mbps, Copper. Software router. Edge)

20 or so X86_64 boxes that do dist_cc work all day..(ethernet 1000Mbps, Copper. Software Router. HQ)

and 5 client machines - mixed/i386/X86_64/PPC/Xbox.(ethernet 10/100/1000 + 802.11pre-N*Linksys WRVS4400N*. Hardware Router - home-office)
---

This network is very secure, im not worried about issues that may arise. as only 3 people have access internally, and no access externally.

--

Now the issue. I need to access certian Local Services. hdtemp, Etc. but i dont want to go the configuration route. becuase i need to keep the systems as close to there recent backups as possible.

so i need a way of routing packets internally, from Localhost(lo) to there network adapters(eth0). and vice versa. for i can gain access to those service remotely with other clients.

not sure where to start. there all running 8.10 Intrepid - Server 2.6.27-7.

Thank you

---

### Post by Petrock6 on 2008-11-06
Shouldn't it do that automatically? Change the firewall's settings [if any].

---

