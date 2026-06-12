---
title: "Networking issue"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by s.kijijiseller.p on 2014-01-03
need a solution to my issue 

here is situation got cable modem come in house go to netgear router wired connections are my home pc XXX.XXX.0.5,and my sat box XXX.XXX.0.3,it needs net port 80, then got my server box going wireless to router in DMZ zone in config XXX.XXX.0.4 has server using ports 9327,9338,80 webserver

issue is as soon as web server is on all trafic to sat boxs stops and it stops working
can someone explain why ??please help soon going to change to cable in to server to router to home pc and sat box see if solves i hope??

---

### Post by r3dd on 2014-01-03
Have you tried just specifying the ports in port forwarding instead of using the DMZ? I don't think that would stop it, but it wouldn't hurt versus just exposing the whole server to the internet. Or perhaps set the sat box in the DMZ rather than the server since that isn't your hardware being compromised.

---

### Post by s.kijijiseller.p on 2014-01-03
trying that now will edit with results

---

### Post by s.kijijiseller.p on 2014-01-03
no luck starting to think sat boxes is toast errr

---

### Post by r3dd on 2014-01-03
Maybe set your web server to listen on port 8080 instead? It would require several changes to your configurations but it would at least separate the two ports and potentially fix it.

---

