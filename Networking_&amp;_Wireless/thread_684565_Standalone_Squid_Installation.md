---
title: "Standalone Squid Installation"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by ol1v3r on 2008-02-01
Hello everyone,

I'm trying to think of how I could go about a Squid content filtering solution on my network. At the moment, my setup is just a couple of PCs that go through a firewall router, which is working fine and im very happy with it. 

I'm looking to add the Squid server as a content filtering / cache based solution to help solve some issues but I would like it to be standalone and pass all of the web queries over to the firewall router, so it would be like the following:

Workstation --> Squid Box --> Firewall --> INTERNET

The issue im having is trying to make the Squid box transparent and get onto the internet via the firewall. I'm not particularly advanced on iptables or routing, but I will try my best to try and get to grips with it if someone could help me out with this problem.

Thanks a lot in advance!
Oli

---

### Post by ssuehr on 2008-02-01
Hello,

Check out [http://tldp.org/HOWTO/TransparentProxy.html](http://tldp.org/HOWTO/TransparentProxy.html) to see if that's any help.

Steve

---

