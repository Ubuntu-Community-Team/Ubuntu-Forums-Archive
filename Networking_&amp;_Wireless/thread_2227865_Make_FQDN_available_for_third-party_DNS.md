---
title: "Make FQDN available for third-party DNS"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by sebastiaopburnay on 2014-06-04
Hi!

Maybe my issue is not even an issue,

I have an Ubuntu Server 12.0.4 LTS VM.

I do not understand why does a non-Domain Windows Server 2008 host will have his FQDN name collected by the local DNS servers, but my ubuntu server wont....

Thank you in advance for your time and knowlege,
Sebastiaopburnay

---

### Post by TheFu on 2014-06-04
Uh ... because Microsoft doesn't follow internet standards?  I'm not certain I understand the question.

You can specify a domain search order, so that adding TLD isn't needed to location machines in DNS.  The setting goes into the /etc/network/interfaces file for servers. Sorry, I don't know how to do it for desktops.  Add a **dns-search example.com**  line to the interface stanza you want it added.  This will make the machine add example.com to any bare hostname DNS lookup.  So **ping foo** will look for foo, then foo.example.com automatically.

Normal DNS does not "collect" anything. It does what it is told so that only an Admin with a brain can setup easy access to systems. Allowing any system that happens to be connected to a network to be easily resolved can be a huge security issue. Huge.

---

