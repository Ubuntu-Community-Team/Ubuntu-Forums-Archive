---
title: "After change to TCP/IP settings, WinXP connects to the net but no pages load in Ubunt"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by Milind on 2009-09-28
I have a dual boot Win XP and Ubuntu Jaunty Jackaloupe system connected to the internet by an Ethernet wired broadband connection. Recently, due to some server-side problems at the ISP's end, my connection slowed down. After repeated complaints the service personnel changed my connection settings. Earlier, in the TCP/IP properties (Windows) the 'Obtain an IP address automatically', and 'Obtain DNS server address automatically' were selected. They have now changed them to 'Use the following IP address', and 'Use the following DNS server addresses', and fed in some numbers in the appropriate fields. Since then, while Win XP connects to the internet without problems, Ubuntu cannot load any web pages. It shows the auth0 connection as connected, I can ping the router, but web pages do not load. Any help would be appreciated.

---

### Post by Arup on 2009-09-28
Change the name of auth 0 to any, use your ISP if you want and then in IPV4 section, add the necessary settings like IP, netmask and router Gateway IP. Also enter the DNS servers and then save. If you know the MTU from your ISP, enter that in MTU section or set it to 1492 for ADSL.

---

### Post by Milind on 2009-09-28
> **Arup said:**
> Change the name of auth 0 to any, use your ISP if you want and then in IPV4 section, add the necessary settings like IP, netmask and router Gateway IP. Also enter the DNS servers and then save. If you know the MTU from your ISP, enter that in MTU section or set it to 1492 for ADSL.
Thanks a lot, Arup. That seems to have solved the problem. I am posting this reply from Ubuntu now. :)

---

