---
title: "Internet Access doubts!!!"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by kapmsd on 2009-03-22
Hi guys!!
I am using BSNL broadband.
I observed in certain times, i cant access internet in xp but i can access internet during the same session in ubuntu.
I noticed this several times.
Whether OS has a major role for internet access rather than Ethernet card or NIC?

---

### Post by Hobgoblin on 2009-03-22
A little troubleshooting is required.

Can you ping a website by IP address from the XP system when it has it's issues?

i.e. Open a terminal on the Ubuntu machine and **ping google.com**, this will give you an IP address in the form 209.85.171.100, press CTRL+C to stop.
Then on the XP system open a command prompt and **ping 209.85.171.100** (or the IP address returned from the above)
Do you get a on the XP system?
If you get a response by IP address but cannot get to the site using your web browser then you probably have a DNS problem.  Are both systems using the same DNS servers?

---

