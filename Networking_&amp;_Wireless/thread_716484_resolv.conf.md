---
title: "resolv.conf"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-03-06
Exactly where does resolv.conf get its values from.

I would like to set up ubuntu with a static IP but I want it to pull the dns dynamically from the router.

In windows you can set both dns and IP to dynamic OR IP to dynamic and dns static thru that network settings applet.  When the dns is set to automatic it takes the values from the router/dhcp

Can I do the same thing in ubnutu..ie. have a static IP but pull in dynamically the dns.

---

### Post by SpaceTeddy on 2008-03-06
It makes no sense to just pull the DNS servers from a DHCP without wanting an IP address - it kind of defeats the purpose of the DHCP server.

Or do you mean have a static resolv.conf and get the IP dynamicially ? that is possible. yes it is, just add the static nameserver to the /etc/resolv.conf and they should always be there... if i am not mistaken (i have only done full DHCP or full static so far...)

---

