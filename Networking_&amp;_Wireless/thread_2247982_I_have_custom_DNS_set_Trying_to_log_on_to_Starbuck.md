---
title: "I have custom DNS set Trying to log on to Starbucks fails unless u use their DNS"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2014-10-11
I have Bind9 as my caching server.  In interfaces I have set 127.0.0.1 as the nameserver.  This setting applies globally.  So when I go to Starbucks, my laptop connects to the wifi, but DNS queries fail since Starbucks blocks all traffic until you use their DNS to connect to their website so you can click on the accept the terms button.

Very sneaky and wrong, but then again owners of wifi networks can do what they want, the law lets them.  I wonder if their data mining the DNS?  Anyway to solve I comment out the nameserver in interfaces and restart networking and use Starbucks DNS to connect to website and click accept button.  Then I change back to 127.0.0.1 in interfaces and restart networking and now I can use the DNS server that I want.

Folks, this is why I proxy Firefox and all my other programs through socks5 and SSH and I proxy my DNS queries too.

I guess if you own a wifi network you have a legal right to do what you want with it.  But why not leave the data mining to the government and be nice to your users and respect their choice of DNS servers and whatever else they choose to transmit.  Respect their privacy.

What are your guys thoughts on this kind of networking.  Please post workarounds for this kind of thing.  Ideally this would be handled with a script.  I'm not sure about posting things like how to bypass accept buttons, so check with a mod before doing that.

---

### Post by TheFu on 2014-10-11
Always use a full VPN when on someone else's network. Period. It the VPN connection isn't possible, wait until you get to a safer network. NOTHING is that important.

---

### Post by MechaMechanism on 2014-10-11
> **TheFu said:**
> Always use a full VPN when on someone else's network. Period. It the VPN connection isn't possible, wait until you get to a safer network. NOTHING is that important.

Well put.

---

### Post by CharlesA on 2014-10-12
Their network, their rules. Do not try to circumvent the policies set in place by the owners.

---

