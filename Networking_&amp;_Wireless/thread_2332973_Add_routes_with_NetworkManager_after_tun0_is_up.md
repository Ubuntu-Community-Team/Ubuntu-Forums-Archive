---
title: "Add routes with NetworkManager after tun0 is up"
date: 2016-08-05
forum: Networking &amp; Wireless
---

### Post by phi1ipp02 on 2016-08-05
Hi All,

I have a cisco VPN setup in NetworkManager (vpnc). I'm able to connect to it, but I don't like having tun0 as my default route. So I ignore routes obtained with a connection and have to run 2 commands after I connect

```
ip r add 10.1.0.0/16 dev tun0
ip r add 10.2.0.0/16 dev tun0
```

i don't know the remote gateway address to use NetworkManager UI to setup these routes. So my question is:- is it able to achieve the same with other means? Maybe some if-up scripts instead?

Thank you in advance!

---

### Post by phi1ipp02 on 2016-08-06
Found an answer on another forum: you need to add 0.0.0.0 as a gateway for these routes

---

