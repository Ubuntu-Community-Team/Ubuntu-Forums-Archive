---
title: "pptp connections"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by smccarthy945 on 2007-02-28
I have installed pptp and pptpconfig. I run sudo pptpconfig and add a PPTP connection. I VPN in and I am able to connect and ping the VPN server. However, I am unable to ping anything else on the network. I know it works because I can VPN on a Windows machine and have no problems.

I have tried adding a manual route and messed with the settings but had no luck. Can someone please point me in the right direction?

---

### Post by crashtest on 2007-03-30
Have you had any luck with this?  I'm at the same point myself, trying to connect to a pptp server running on Windows 2003 server.  The vpn connection works - I get connected, get assigned an an address on the network, get assigned the DNS servers, but then nothing more works.  Can't connect to email, can't ping, etc.

---

### Post by smccarthy945 on 2007-04-03
Yes, I figured it out. You have to use a different PPTP GUI management utility. I dont have Ubuntu installed right now but its in ADD REMOVE programs and it starts with a "K". I think its KPE VPN Mananger or something like that. Install that and it will work.

---

