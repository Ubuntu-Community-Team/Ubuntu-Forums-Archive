---
title: "DNS problem?"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2008-06-19
Can you tell why I have all the time restart networking to get internet working? It comes and goes? (Hardy Heron, Xubuntu).

---

### Post by pytheas22 on 2008-06-19
There could be lots of different reasons; please provide some more information so we can make a better assessment.  Information like this would be useful:

-does networking crash at fixed intervals or does it seem random?
-does it crash when the machine is idle or only when you're using the Internet?
-do you notice it crashing only when you visit certain websites?
-you mention DNS in the title so I'm wondering why you think it's DNS...do you sometimes have issues resolving domain names?
-when networking seems to break, have you tried connecting directly to an IP address (i.e. avoiding DNS) to see if that still works?  72.14.207.99 should bring you to google.com for instance.
-can you ping when the network crashes?
-what is the output of dmesg right after the connection crashes?
-what hardware and drivers are you using?  If you don't know, please post the output of the command "lshw -C Network"
-how are you restarting networking (/etc/init.d/network restart or something else)?

When you get a chance, please provide this information so that you can be helped better.

---

