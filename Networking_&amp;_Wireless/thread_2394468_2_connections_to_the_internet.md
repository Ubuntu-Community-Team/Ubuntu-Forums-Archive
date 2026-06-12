---
title: "2 connections to the internet"
date: 2018-06-16
forum: Networking &amp; Wireless
---

### Post by me-mitch on 2018-06-16
I would like to have 2 connections to the internet 1 with a VPN and another without is this even possible and if so how do i do it? I have a standard Ubuntu 18.04 setup with a internet connection without a vpn.

---

### Post by SeijiSensei on 2018-06-17
Running simultaneously?  Probably not.  What matters is the "default gateway" used by your machine.  Typically that will be your router.  You could make the VPN be the default, though that is a bit trickier.  But every Internet host has just one default gateway, the connection that handles all traffic for which specific routes have not been define.

If the list of connections to which you want one or the other gateway used is relatively small, you could add a bunch of routing commands with specific destinations.  For instance, to send all requests to Google's DNS server at 8.8.8.8 over a VPN that uses the "tun" module, you could add

```
sudo ip route add 8.8.8.8/32 dev tun0
```

to send connections to 8.8.8.8 out the tun0 device.

---

### Post by oldos2er on 2018-06-17
Thread moved to *Networking & Wireless*

---

### Post by me-mitch on 2018-06-18
No what I'm looking to do is make a vpn connection and have my other connection where i can pick the one i want to use from the drop down menu but I've only have one internet connection going to my pc.
My first time with setting up a vpn on Ubuntu and don't know anything about it but I'd like to save the connection i have just in case. I'm going to be using Protonvpn 

[https://protonvpn.com/](https://protonvpn.com/)

---

