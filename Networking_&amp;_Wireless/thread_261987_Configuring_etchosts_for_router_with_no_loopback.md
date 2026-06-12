---
title: "Configuring /etc/hosts for router with no loopback"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by zazery on 2006-09-21
Recently I switch to a newer Belkin router and after emailing the company it appears that it does not have a loopback feature. I run a webserver and whenever I want to link someone to a page I now need to convert it to my external IP. I tried adding a line to my /etc/hosts file but it's not working. Is there any hope in making this happen?

Thanks.

---

### Post by mssever on 2006-09-21
Loopback (127.0.0.1) ONLY works for the local machine. As far as I know, no routers have a loopback feature. I'm assuming that you mean that you want port forwarding, so that your external IP address is mapped to your internal IP. This is something you'll need to configure through your router. If your router doesn't allow this, you're pretty much up a creek. Editing /etc/hosts is pointless as it only affects your local machine.

Or are you looking to use a domain name? In that case, if you want to use /etc/hosts, you have to set the hosts file of **every** machine that will connect to your server. Setting the hosts file on your server doesn't accomplish anything. If you're trying to serve sites externally, you need to register a domain name and configure the DNS servers to point to your external IP. If you're in an intranet and only want to serve files locally, you can set up your own DNS server instead of using /etc/hosts, if you want. Google "DNS HOWTO."

---

