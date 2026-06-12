---
title: "Allow internet access only to whitelisted domains"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by smshUA on 2008-02-26
We have a remote POS (point-of-sales) working with GPRS-phone having not-cheap cost of Megabyte.

They need to be allowed only ICQ, POP/SMTP mail (gmail.com) and two web sites.

How to implement a whitelist for only allowed domains for this connection ?

---

### Post by john.belcher on 2008-02-26
I hope you have a firewall on your network.  You should be able to setup firewall rules to only allow a few domains/IPs/ports.

---

### Post by smshUA on 2008-02-26
No firewall in network, no even network there :)
Just a PC with attached GPRS-phone via USB

---

### Post by john.belcher on 2008-02-26
I see.  Maybe a NetNanny type of software would work for your application.

Are you actually running ubuntu on the desktop you are trying to restrict?

If you are you might be able to setup the PC to act like a firewall and set local filtering rules.

HOSTS file might be an option.  Not sure if there is a convention to using wild cards in a host file.  If there is you could use the HOSTS as a white list by redirecting everythng else to a specific ip.  Maybe localhost.  Im sure someone out there that knows more about HOSTS files then I do can better answer this.

---

