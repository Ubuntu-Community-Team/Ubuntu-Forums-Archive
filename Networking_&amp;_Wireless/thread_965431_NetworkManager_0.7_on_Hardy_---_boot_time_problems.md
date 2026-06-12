---
title: "NetworkManager 0.7 on Hardy --- boot time problems"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by mitya on 2008-10-31
Goodday, everyone.

I have just installed NetworkManager 0.7 on Kubuntu Hardy (from PPA Launchpad).

So I see several problems:

1) NM won't connect to wireless automatically at boot.
2) In knetworkmanager there is no checkbox for making wireless connection a "system" one. I haven't seen Gnome NM applet, but a have read that gnome applet has this checkbox.

I really need my wireless network being brought up at boot time as I check credentials against LDAP server and I don't want to configure wifi through /etc/network/interfaces.

So my quiestions are:

1) Is there any way to tell NM to connect to wireless automatically?
2) IF YES -- Is there any version of network-manager-kde which is correct and is fully compatible with NM?
3) Is there any way to do this in CLI (write a config file etc.)?
4) Is it a problem of using NM 0.7 on Hardy (I really want to use LTS release)?


Thanks.

---

### Post by mitya on 2008-10-31
NM is able to start wifi at boot time.

I removed 'network-manager-kde' (knetworkmanager) and installed network-manager-gnome.

Using nm-gnome I set up my wifi and made it "system".

And everything works.

Is it a bug in kde applet?

---

