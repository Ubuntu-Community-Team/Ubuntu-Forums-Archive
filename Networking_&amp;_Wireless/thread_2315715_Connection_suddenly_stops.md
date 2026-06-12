---
title: "Connection suddenly stops"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by teddmartingeek on 2016-03-01
I've been using Ubuntu for years, I recently reinstalled on my laptop, and for some reason after sometime the connection on the system to the Internet goes away, it does not disconnect, it just simple stop accessing the web, if I'm in a irc chat, or in firefox, at some moment I can't access anything anymore.

My computer has been running ubuntu in the latest LTS version with no problems, this time I used 15.10 and the installation us fresh, less than 2 days.

Anyone can help me?
Thanks.

---

### Post by houstonbofh on 2016-03-02
You have to narrow down what app is failing.  When it is happening, in a cli try;

ping 8.8.8.8

If that works, you have connectivity.  Next try;

ping [www.google.com](www.google.com)

If that works you have DNS.  With those two resolved, you have a problem with your applications.

---

