---
title: "Transparent Cisco VPN"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by Tlon on 2007-10-12
I'm having problems getting VPN to work properly on my 7.10 gutsy setup (it didn't work right on feisty either).  On my win boxes, when I connect with VPN the DNS from that point forward Just Works, meaning that I can type in a given network address, e.g., [http://internal_site.myworkdomain.com](http://internal_site.myworkdomain.com), and the browser has no problem resolving the address.  On my gutsy box, I seem to be able to connect to the VPN alright, but when I try to browse as per above, I get the standard 'google search for URL' response.

I'm using VPNC.

---

### Post by bobo on 2007-10-13
I also need to use a Cisco VPN connection and was looking for a good app to use.  VPNC, from your post, intrigued me so I installed it via Synaptic.  I did a "man vpnc" and I saw this toward the end that might help you.

```
 /etc/resolv.conf update
              If the package resolvconf is installed and the VPN gateway sends
              some  DNS  server  data, the script will use resolution to inte&#8208;
              grate the received data into /etc/resolv.conf.  To disable  this
              behaviour, set the config directive DNSUpdate to the no value.

```

Can I take an existing Cisco pcf file and rename it to a conf file and vpnc will recognize it?

bobo

---

