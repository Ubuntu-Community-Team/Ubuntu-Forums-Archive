---
title: "Remote Desktop via VPN tunnel"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by ale_login on 2011-01-14
Hi all,

I have an Ubuntu 10.04 server to which I would like to connect remotely via VPN network.
The VPN works fine (using PPTP), but I still have some problems configuring the Remote Desktop application:
simply using System->Preferences->Remote Desktop allows me to connect from a Windows XP machine with TightVNC but not the Windows Remote Desktop application which I would like to use.

But most importantly, I have now a situation where I could connect via Remote Desktop (so far with TightVNC only) either using the VPN or not. I would like the Remote Desktop server to allow incoming connections ONLY from the private LAN (i.e. VPN network) and NOT from the public internet.

How do I achieve that?

Thanks for any help you can offer!

---

### Post by natravis on 2011-01-14
I love googling! First result from "how to windows remote desktop into ubuntu" yielded this:
 
[http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/)

---

### Post by blind2314 on 2011-01-14
xrdp is a nice, lightweight package that allows you to natively use the RDP program that comes with Windows.
 
```
sudo apt-get install xrdp
```
 
That should find it for you, or you can look in the software center.

---

### Post by ale_login on 2011-01-14
> **natravis said:**
> I love googling! First result from "how to windows remote desktop into ubuntu" yielded this:
 
[http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/)

I had realized that I need xrdp, but I was wondering why... (which I eventually understood).

The big question still remain unanswered though: how can I restrict xrdp (or the underlying vnc server - i'm using tightvncserver) to ONLY grant access from the VPN?

---

### Post by maddog2050 on 2011-02-16
Have you looked if it's possible to firewall the LAN from being able to access the port that vnc is using?

---

