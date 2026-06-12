---
title: "DHCP Supplied hostname is not set at boot"
date: 2014-06-16
forum: Networking &amp; Wireless
---

### Post by Adam_CLark on 2014-06-16
I am migrating some server images from precise to trusty and I have noticed a change is behaviour.

In precise, if I was to delete all lines out of /etc/hostname the hostname that was supplied as part of a DHCP reply would be set at bootup.

In trusty this is not the case.  If I kill the dhcp client process and manually start it, the hostname is set correctly.

Does anyone know why this would be the case and how I can get the behaviour I am after?

Cheers

Adam

---

