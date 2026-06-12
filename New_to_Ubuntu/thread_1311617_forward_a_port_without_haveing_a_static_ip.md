---
title: "forward a port without haveing a static ip"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Kedster on 2009-11-02
I would like to open a few ports for remote desktop and also for bittorrent but the problem that I am fore seeing and I could be wrong is that if I want to always have those ports open I would need a static IP. My question is this, is there a way to open a port for everyone so when I get handed a new IP i still have that port open aswell as the 2 others doing the same as my self.

---

### Post by ericab on 2009-11-02
port forwarding to a specific ip acquired via DHCP will only work for as long as the lease is active. so yes it *will* work, but for a time.
maybe your router has the ability to set fixed leases ?

why cant/wont you set static ips ?

[http://www.portfoward.com/](http://www.portfoward.com/)
has a wealth of information that may help you set your network the way you like

---

### Post by sandyd on 2009-11-02
> **Kedster said:**
> I would like to open a few ports for remote desktop and also for bittorrent but the problem that I am fore seeing and I could be wrong is that if I want to always have those ports open I would need a static IP. My question is this, is there a way to open a port for everyone so when I get handed a new IP i still have that port open aswell as the 2 others doing the same as my self.
yes. 
if your router supports it, you can use upnp port mapping

some routers also support mapping to a MAC address, instead of mapping to an IP address.
you can try that too.

---

### Post by Kedster on 2009-11-02
arnt there many disadvantages to using a static ip 
that is just what I have herd if there is not then how would I go about it

---

### Post by bodhi.zazen on 2009-11-02
> **Kedster said:**
> arnt there many disadvantages to using a static ip 
that is just what I have herd if there is not then how would I go about it

The major disadvantage of a static IP is that you need to set one manually. Other then that there is not disadvantage in terms of performance.

---

