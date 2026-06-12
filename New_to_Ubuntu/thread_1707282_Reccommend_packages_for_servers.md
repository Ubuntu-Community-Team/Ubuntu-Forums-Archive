---
title: "Reccommend packages for servers"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by arthurki on 2011-03-15
We are a small organization (20 users max). I need to install a suitable package to handle the following:
1) Web access - PROXY Server
2) Firewall
3) Felamimail
4) egroupware or similar
5) Print Services
6) VPN

We have suitable hardware, and have CISCO Routers connecting us to the ADSL

What is recommended to load with the Ubuntu Server ver 10 to use for 1, 2, 5 & 6?

relative ubuntu and linux newbie needs advice

---

### Post by HermanAB on 2011-03-15
Howdy,

Actually, the best way to do all that, is with multiple virtual machines, one for each major function.  Otherwise, you update Egroupware for example and break something else.

Also, if and when you find that your computing needs exceeds the capability of the server (or if the server would fail and needs to be replaced with new, different hardware), then you can easily move a VM to a new machine.

---

