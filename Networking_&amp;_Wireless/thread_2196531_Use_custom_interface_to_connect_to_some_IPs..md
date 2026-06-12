---
title: "Use custom interface to connect to some IPs."
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by beniamin-kalinowski on 2013-12-30
I have two interfaces: wlan0 and eth0 connected to a different networks. I would like to use one interface (eth0) to work as a default most of the time (it is used all of the time right now) and sometimes (to some IPs, some webpages, and mostly to irc channels) I want to use the other interface wlan0.

How can I achieve it? Is it possible? I was looking for a setting in irssi, which iface to use, but I have found nothing.

---

### Post by ian-weisser on 2013-12-30
You can use the *route* command to map specific IP addresses to an interface.
All applications that contact that IP address will use the specified interface. No exceptions.

Since systems can have any kind of interfaces, and since routing packets across interfaces is a system-level task, applications generally won't have an interface setting.

---

### Post by beniamin-kalinowski on 2013-12-31
*route* works great, I wasn't aware of this command. It works with webpages etc. But it doesn't work with IRC.
With IRC servers like freenode unfortunately it doesn't work.

---

### Post by ian-weisser on 2013-12-31
The *route* command does indeed work with IRC.
Perhaps your IRC client is connecting to a different server than you expect.
Freenode, for example, uses a globally-distributed network of servers. When your IRC client connects to chat.freenode.net, it can connect to *any* of those servers (looking right now, I see 12 online). You either must define a route for all of those servers, or you must specify the server to connect to (like cameron.freenode.net).

---

