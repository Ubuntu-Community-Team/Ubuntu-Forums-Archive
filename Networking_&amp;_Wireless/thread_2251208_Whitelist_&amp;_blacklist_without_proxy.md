---
title: "Whitelist &amp; blacklist without proxy"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by rackit on 2014-11-02
I'm looking for a way to whitelist/blacklist websites on ubuntu systems. I don't want to use browser extensions as those are easy to bypass. I'm thinking hosts file but haven't been able to come up with the correct syntax. Any ideas as to how to make this work? DNS is not an option at this point. I'm not married to hosts. Any method that accomplishes what I'm looking to do is welcomed.

---

### Post by TheFu on 2014-11-03
A proxy is the best answer, provided it is required to use it. The desktops should NOT be able to use DNS or have any route to the internet.  If they try to ping 8.8.8.8 ( a well-know public UP), it should never return.  Only the proxy server should have internet access. So ... with that service, you can blacklist OR whitelist - but not both.  

Internet DNS should not be possible from any client either - nslookup google.com should fail from any workstation.  If DNS works from a desktop - it is possible to use that to transmit traffic even if every other method (udp/tcp/icmp) are blocked.

If you want to use hosts files ... which can be used for this, but are trivial for people on the network to get around, [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security) should help.

---

### Post by chili555 on 2014-11-03
You may also want to take a look at:```
less /etc/hosts.allow
less /etc/hosts.deny
```

---

### Post by TheFu on 2014-11-03
> **chili555 said:**
> You may also want to take a look at:```
less /etc/hosts.allow
less /etc/hosts.deny
```

Chilli - are those for outbound countrols?  I thought they only worked for inbound stuff. Please teach me.

BTW - the proxy for Linux systems most used is squid.  It can do some amazing things, provided the network is setup properly.

---

### Post by rackit on 2014-11-03
I have an EdgeRouter Lite (which runs Debian) with 1 WAN and 2 LAN interfaces + vlan. I was going to whitelist "staff" and blacklist "admins" - one on each physical LAN. Problem is, there is a wireless link between remote parts of the location so probably vlan - then there is routing, etc. None of the users will have root so hosts is looking like the least complicated solution.

---

### Post by TheFu on 2014-11-03
Not sure how /etc/hosts on 1 box helps for other machines unless you do something extremely unusual. Maintaining /etc/hosts files on 10 workstations is not really a good solution, IMHO.

---

