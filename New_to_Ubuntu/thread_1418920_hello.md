---
title: "hello"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Quizzer2093 on 2010-03-01
i am currently IT Administrator / Tech Support (Volunteer) for a small non-profit organisation; we currently run a Community Access Program (CAP).  Which is we provide computers, internet access to the general public for free.  Our current system comprises of 

5 computers (running Ubuntu)
5 computers (running Windows XP)

i am currently looking for a cheap, but effective solution to monitor all workstations so that our clients (members) and the general public dont surf inappropiate (and in this i mean anything illegal) 

any ideas of programs, or ways to limit what they can surf or do .

---

### Post by blazemore on 2010-03-01
Your best bet is to use a proxy server.
All requests to the Internet would be routed through this, the proxy server wuld fetch the Internet content (or not, if it's blocked), and then send it to the user that requested it.
You can view the logs if you need to.
IMO the best proxy server is Squid, mainly because it has full Webmin integration, so you don't need anything complicated, just a web-based interface.

---

