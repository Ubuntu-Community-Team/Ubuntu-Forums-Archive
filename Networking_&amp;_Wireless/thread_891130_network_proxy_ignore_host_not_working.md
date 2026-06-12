---
title: "network proxy ignore host not working"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by marcw on 2008-08-15
I've got several Ubuntu machines that use a proxy for internet access.  They all use the Gnome Network Proxy settings to point to the proxy.  Their respective Firefoxs are configured to use the system proxy settings.  It all works well.

Except for accessing other local machines.  If I use the Network Proxy -> Advanced Configuration to make specific address exclusions it works but if I use cidr notation it doesn't.

For example, if I want to access another local machine's web server from my workstation, I would need to make a proxy exclusion in Network Proxy.  Here's the results:

192.168.0.6    = works
192.168.0.0/16 = doesn't work

Why do individual addresses work for proxy exclusions but not ranges?

---

