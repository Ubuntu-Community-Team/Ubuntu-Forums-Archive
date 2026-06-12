---
title: "firewalls, firewalls, firewalls... but which?"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by frankdn on 2008-09-16
Here's my home network:


Comcast --> Motorola SBG900 cable modem + wireless router -->

         --> desktop --> windows XP pro --> Symantec
and
         --> laptop --> windows XP pro --> Macafee
         or         --> ubuntu


The Motorola router, windows, Ubuntu, Macafee and Symantec ALL offer a firewall.  So my question is, which should I use?  Obviously it'd be most efficient to use the one at the cable access point, i.e. the wireless router, and disable the others.  Should I trust it?

How do you test a firewall?

---

### Post by hey_ram on 2008-09-20
hey!

even i have been looking for a firewall and anti-virus for my ubuntu system...
any suggestions would be most welcome

---

### Post by PocketDog on 2008-09-20
Use the Shield's Up! port scanner at [www.grc.com](http://www.grc.com) to test your machine's vulnerability to the outside world. For an anti-virus get ClamAV, though it's only really necessary to check either your own Windows partitions or files you'll be sending on to Windows users. Linux doesn't have that problem

---

### Post by mikewhatever on 2008-09-20
No firewall (or AV) is needed for Ubuntu, let along the monsters like Symantec and Macafee. By default, Ubuntu has no open ports, so firewalls are useless, unless you run a server. Check out the link below for more:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by blastus on 2008-09-21
> **frankdn said:**
> The Motorola router, windows, Ubuntu, Macafee and Symantec ALL offer a firewall. So my question is, which should I use?  Obviously it'd be most efficient to use the one at the cable access point, i.e. the wireless router, and disable the others. Should I trust it?

I would go with the router firewall. However, some router manufacturers do not release firmware updates for their routers. Even so I wouldn't go with McAfee or Symantec because they are resource pigs (CPU and memory), only work in Windows, and you have to configure each machine.

I guess the answer depends on what you do with your Windows machines. Do you download and install untrusted software from the Internet? Are the browser(s) you use loaded with extensions and plugins? Have you locked down Internet Explorer and prevented ActiveX controls from executing? Are you careful when you use the Internet...do you click on advertisments or things you don't know about? Do you keep Windows up-to-date etc...?

---

### Post by warchief_ryan on 2008-09-21
I wouldn't say a firewall isn't needed for Ubuntu, it depends on what you have Ubuntu doing.  I think the above statement is wrong Ubuntu by default has all ports open, because the default polices iptables have on a fresh install, is ACCEPT on all three default chains, meaning that its allowing everything from everywhere.  

EDIT: Unless you mean by not having that service installed the port would be closed because there's nothing installed to use it.

By far the best firewall ive used is netfilter/iptables.

But for a desktop using ubuntu you probably wont have to worry about a firewall. Unless your paranoid like me...

---

