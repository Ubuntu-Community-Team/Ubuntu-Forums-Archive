---
title: "Firestarter doesn't recognise wireless connection"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Alexd2010 on 2010-07-08
Ubuntu 10.04

I've been reading Keir Thomas' Ubuntu pocket guide and have decided that I should install a firewall, even though I don't think I'm particularly at risk from anything - not on a network, don't fileshare etc - but better be safe than sorry.

Anyway, I installed Firestarter and tried to set it up but it doesn' recognise my wirless connection - in Preferences > Network Settings, under Internet Connected Network Device the only options are two Ethernet connections (eth0 and eth1) and one unknown connection (pan0) - no wlan.  So I can't get the firewall to work.

I'd really welcome help on this and also if anyone has any thoughts on if I need a firewall - I only use the machine for general internet stuff, photos, checking my bank account, BBC Iplayer, music etc so would appreciate comments.

Many thanks,

Alex

---

### Post by Paqman on 2010-07-08
> **Alexd2010 said:**
> have decided that I should install a firewall

Good news, you already have one!

First of all, Firestarter is not a firewall. It's a tool for configuring the firewall your system already has. Secondly, Firestarter is really old and no longer maintained, so best not to use it.

If you want a tool to configure the firewall, install [gufw](apt:gufw). You should only need it if you've installed some kind of server software though. The default install on Ubuntu is totally safe, as there are no services listening on any ports.

---

### Post by Alexd2010 on 2010-07-09
Thanks - very helpful.

Alex

---

