---
title: "route certain domain to certain port"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-10-06
Hi,
so I got three teamspeak-servers which are accessable via domains like:
srv1.domain.com
srv2.domain.com
srv3.domain.com
Right now these domains are forwarded to ts3dns.com - a DNS-server exactly for this matter and which does all the work for me.
Sadly it is offline today and I realized how dependent I'm on it.
That's why I want to move everything to my server.
I have only one IP adress but 3 subdomains and 3 ports.
All requests are made trough the standard teamspeak-port 9987
This is how it should look like (made up domain and IP ofc):
srv1.domain.com:9987 to 12.345.678.90:1234
srv2.domain.com:9987 to 12.345.678.90:2345
srv3.domain.com:9987 to 12.345.678.90:3456

I learned this is not possible using iptables since it can't know which domain is used to connect.

What other options do I have to do this?

---

### Post by chris137 on 2014-10-09
No idea on that?
Please ask if I described it not very clearly!

---

### Post by chris137 on 2014-12-13
Sorry for grabbing this old thread but I feel like I should close all my threads eventually.
As far as I learned this is not possible as I want to do it.
Since this was for teamspeak-dns purposes I finally looked into the built-in teamspeak-dns which I learned of later.
It is already included in the server-files and very easy to configure.
If you have problems there are good guides on google.

---

