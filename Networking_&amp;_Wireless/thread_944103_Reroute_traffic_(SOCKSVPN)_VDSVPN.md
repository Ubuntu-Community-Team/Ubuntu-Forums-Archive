---
title: "Reroute traffic (SOCKS/VPN) VDS/VPN"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by omarmir on 2008-10-11
Hi guys,
I havent posted here in a while - have been going well w/ my Ubuntu installation but today I hit a new problem and I couldnt understand the man pages for pptpd and openvpn

I need to reroute traffic from my home/mobile connection to go through my VPS/VDS (virtual private server) so that It can look like Im accessing the website from my VPS rather than my mobile location. Lots of reasons, one being simply because I want to learn to do it.

Not sure how to go about it, VPN or SOCKS proxy and how exactly to go about setting it up?

Thanks!

---

### Post by superprash2003 on 2008-10-11
vpn would be a better choice as it would be more secure.. you could read more about setting up openvpn

---

### Post by omarmir on 2008-10-11
Any idea how to go about installing it so that the only authentication is by username/password
I don't really need something massively secure since ill be monitoring the server at most times.

I tried using openVPN but i could not make sense of the man pages and tutorials I got off of google.

Thanks.

---

### Post by kevdog on 2008-10-13
I dont know if you are using ddwrt on your router, but this blog I thought was very informative:
[http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html](http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html)

---

