---
title: "Firewall questions, also transmission webui https"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Hospadar on 2008-12-18
I'm soon going to be setting up a small server for myself.  It also happens to by my mythtv machine.

Here's what I want to do:
Block all traffic to my machine except:
Allow ssh (port 22)
Allow my webserver to function(ports 80 and 443)
Allow bittorrent (transmission via web client) to function properly

I plan on using ufw to manage my firewall, and I understand the basics of denying all traffic, then allowing traffic on certain ports, etc.

What I don't know how to do is make sure that transmission is able to run properly.  Is there just one port I need to open? How should I set rules so that transmission won't get denied connections it needs?

Also, in previous versions of transmission, the webui (clutch) was not bultin, but ran as some scripts in a webserver and I could therefore protect it with ssl (http).  Now the webui is built into transmission, is it still possible to protect it with ssl?

---

### Post by ibuclaw on 2008-12-18
Best way to do that would be to use the application **firestarter**.

```
sudo apt-get install firestarter
```

It is fully configurable, and you can set both inbound and outbound ports to whitelist, so only what you say can be sent out and in to the network.

For Documentation read these links:
[http://www.fs-security.com/](http://www.fs-security.com/)
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

Regards
Iain

---

