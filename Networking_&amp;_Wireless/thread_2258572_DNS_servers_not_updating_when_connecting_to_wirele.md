---
title: "DNS servers not updating when connecting to wireless"
date: 2014-12-28
forum: Networking &amp; Wireless
---

### Post by ketrel2 on 2014-12-28
When I connect to a wifi network the dns servers in /etc/resolv.conf are not updating.

The only way is to get it to update is to do
'sudo dhclient <interface>'

Is there anything I can do to correct this?

---

### Post by walth2 on 2014-12-28
I'm having a similar problem. I can ping IP addresses outside my LAN, but the DNS names don't resolve and the PING hangs until I kill it.

I checekd on the file system and the nameservers are defined correctly. However, I don't see them in the System Tools->Network Settings ->DNS Tab. When I switch back to a wired connection, everything works normally.

I'm running Lubuntu and not Kubuntu.

---

### Post by ketrel2 on 2014-12-29
I had assumed it was some quirk of Kubuntu, but I just found this which looks as if it may be the issue for me

[http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf](http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf)

---

