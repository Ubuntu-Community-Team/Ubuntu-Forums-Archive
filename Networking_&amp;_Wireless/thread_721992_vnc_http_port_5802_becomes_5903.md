---
title: "vnc http port 5802 becomes 5903?"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by maulakai on 2008-03-11
I'm no stranger to setting up a vncserver.  I've done it on just about every distrobution of linux using half a dozen different router/firewalls.

But now I need to use the java webapplet to access it via port 80.  I configure my router to direct port 80 to 5802, then run the command:

vncserver -httpport 5802

It works fine if I connect to 5802 on the internal network.  But when I access it through the web, it throws an error AFTER I enter the password, saying it can't access port 5903.

Anybody know why it would change ports, or how i could get it to stop from changing ports?  

I need it all to run on one port since the firewall I'm going through only allows outbound port 80 traffic

---

