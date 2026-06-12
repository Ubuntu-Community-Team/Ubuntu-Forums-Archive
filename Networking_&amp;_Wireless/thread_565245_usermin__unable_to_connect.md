---
title: "usermin / unable to connect"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by Badbunny on 2007-10-02
I use webmin and usermin with a hostname provided by dyndns and updated with ddclient. I have opened the ports from my firewall with guarddog. My system is kubuntu 7.10 beta.
I am unable to connect to usermin from a remote computer. I can use it from my own computer, but it is unaccessible form any other. I get a connection timeout error every time I try. 
I had the exact same problem with webmin, but then I added "allow=0.0.0.0" to miniserv.conf. That fixed it, now I can connect to webmin. I tried to do the same to usermin's miniserv.conf, but I found out that the row was already there. 
So, where to go from here?

---

