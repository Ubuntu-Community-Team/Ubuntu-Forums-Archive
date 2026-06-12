---
title: "Using https over squid"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by amgat on 2008-09-18
I have a webserver at home set up with squid3 (from repositories). The proxy server is working perfectly when I am at home - I am able start http and https sessions. I have defined router forwarding from 443 to port 22 on the server.

We have a corporate network at work (DOH!). I use putty to create an SSH session to my webserver at home. I have defined the http corporate proxy (bluecoat) at work as putty proxyserver and created a tunnel to my server at home (using port 443).
The proxy is working when using http sessions, but I am not able to use https sessions.

Yesterday I was visiting a buddy. I tested the proxy from his computer and configured putty the same way as when I am at work - except the corporate proxy setting. The strange thing is that both http and https sessions work from his ISP.

Why am I not able to use https from work? Is it because I have to pass the traffic through the corporate proxy server first? :confused:

I really need your help here guys. Thanx.

---

### Post by amgat on 2008-09-22
As it turns out, there never was any problems :). I had only set the http proxy but forgot to set the SSL proxy too. Works great now, and I am able to surf the web, download all my emails and use MSN messenger from work. How perfect! :)

---

