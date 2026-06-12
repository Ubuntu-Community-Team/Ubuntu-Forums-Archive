---
title: "can't connect to the internet"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by freakie on 2008-09-10
can anybody help me..
my server suddenly can't connect to the internet. when i ping to any web address it's got a reply. but when i try to browse using web browser connection refuse. 1st my suspect is firewall was blocking port 80 but when i ask my server admin they said they don't block my ip.
can anybody give me a suggestion on how to troubleshoot this problem.

---

### Post by rlzyoner on 2008-09-11
Can you telnet to a webpage on port 80 ?

---

### Post by freakie on 2008-09-11
thanks rlzyoner. I already had the solution. I just do telnet and port scanning using nmap just to prove to my network admin that their firewall had filter my server too. last time they said my ip does not involve, to problem might come from my config itself. I'm new, but I know there's something wrong with the firewall. Anyway thanks again. I really appreciate your help.

---

