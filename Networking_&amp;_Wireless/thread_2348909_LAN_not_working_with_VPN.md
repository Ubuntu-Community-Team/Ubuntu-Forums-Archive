---
title: "LAN not working with VPN"
date: 2017-01-09
forum: Networking &amp; Wireless
---

### Post by dr.nukular on 2017-01-09
Hi,

I hope that someone can help me out here.

My computer is connected to a router, which is connected to the ISP.
I'm accessing the internet through a openVPN connection.

As soon as I activate my VPN, I'm unable to access my LAN with another router attached to it.

Thanks!

---

### Post by Fire_Chief on 2017-01-10
This is a normal result from using an OpenVPN connection. What you are wanting is called split-tunnel vpn. The tricky part here that normally split-tunnel vpns only send traffic for the VPN remote subnet over that VPN tunnel (to a remote office for example). Using OpenVPN to reach the Internet doesn't have the same setup. I did some quick searching and found an article that describes a work around for this although it's a few years old (and may therefore be out of date). It's focused on RedHat/CentOS so some tweaking is likely necessary.
[http://www.gigahype.com/setup-split-tunneling-when-using-openvpn/]("http://www.gigahype.com/setup-split-tunneling-when-using-openvpn/")

Cheers!

---

