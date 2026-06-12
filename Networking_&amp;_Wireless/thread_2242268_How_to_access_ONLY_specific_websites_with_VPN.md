---
title: "How to access ONLY specific websites with VPN?"
date: 2014-08-31
forum: Networking &amp; Wireless
---

### Post by countercharge on 2014-08-31
I have a VPN connection set up.  Currently, when it is connected, ALL of my traffic goes through the VPN.  How can I make it so that ONLY certain websites go through the VPN and everything else is routed normally?

---

### Post by TheFu on 2014-09-01
Compare the routing table with and without the VPN active - that is where I'd start.
Many/most corporate VPNs don't allow "split tunnels" for security reasons. If that is the situation for your system, then there probably isn't anything you can do. It is controlled by the VPN server administrator.

---

### Post by SeijiSensei on 2014-09-01
You would need to add routes for those specific sites that use the VPN's upstream gateway for those subnets.

Let's take Google for an example.  Using "host www.google.com" I get 
```

www.google.com has address 74.125.225.80
www.google.com has address 74.125.225.81
www.google.com has address 74.125.225.82
www.google.com has address 74.125.225.83
www.google.com has address 74.125.225.84

```
Suppose the VPN's upstream gateway is 10.10.10.10.  You would then add a route like this
```
sudo ip route add 74.125.225.0/24 via 10.10.10.10
```
For simplicity I included the entire "class-C" subnet rather than just those specific IP addresses.

---

