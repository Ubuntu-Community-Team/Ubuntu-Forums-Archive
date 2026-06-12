---
title: "Bridging + Squid Transparent Caching"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by Schroedinger on 2008-06-02
G'day guys,

I've set up an old server with two NICs as a bridge running ubuntu server 8.04. I'm trying to get Squid up acting as a transparent cache between my current Router and the rest of the network, so we've got a bit of a buffer between us and the world as we've gone over our bandwidth cap the last few months. 

Thus far I've been using this fantastic guide:

[http://www.simpleguys.info/2008/01/ubuntu-710-bridge-transparent-proxy.html](http://www.simpleguys.info/2008/01/ubuntu-710-bridge-transparent-proxy.html)

It all goes great until I try the symlink and the ebtables rules, I get told I can't get a socket and there's no permissions.

Would any gurus be able to tell me what I've done wrong? The bridge is working an utter dream and I know I've got squid up and running, I just need to get my ebtables and iptables rules working so that the machine will work transparently.

If there's any other info you want don't hesitate to post, I really need to get this working asap

Cheers,

Schroe

---

### Post by Schroedinger on 2008-06-02
Quick update: Sudo'ing the ebtables rule above causes a kernel panic on my server. Going to do some more research.

EDIT: Because /etc/ethertypes doesn't exist... what's going on.

---

### Post by Schroedinger on 2008-06-02
Update: I've downloaded a new ethertypes doc and put it at /etc/ethertypes but I still get a kernel panic when I try to actually run the BROUTING.

I'll also note I didn't install LAMP initially, but I don't really see how that could be causing this issue. It just seems as if Ubuntu 8.04 really hates ebtables.

---

### Post by Schroedinger on 2008-06-02
Apparently it's a problem in the 2.6.24 kernel that causes this panic.

Any idea how I can downgrade to 2.6.22 or upgrade to a newer beta version?

---

### Post by Schroedinger on 2008-06-02
Installing Ubuntu 7.10 server and testing it there. Wish me luck!

EDIT: Someone else post here, I'm lonely!

---

### Post by Schroedinger on 2008-06-02
There's a simple solution to the problem and it's to not use the ebtable rule.

Everything else works fine if I just use the iptable rule.

---

### Post by kevdog on 2008-06-02
Sounds like you could write this up as a formal How-TO -- it would be very interesting.

---

