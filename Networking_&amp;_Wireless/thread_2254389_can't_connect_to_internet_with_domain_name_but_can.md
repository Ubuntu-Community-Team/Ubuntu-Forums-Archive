---
title: "can't connect to internet with domain name but can by ip address!"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by JohninFrance on 2014-11-26
My desktop (amd64) has no wireless card and after days spent trying to get USB mobile broadband key to work in ubuntu 14.04 I gave up and connected by ethernet to an old dell laptop on windows xp with working wifi which worked well until today when the dell died (terminal power supply failure).  So connected by ethernet to a newer HP notebook running ubuntun12.04 the connection works but despite doing everything I can find on the forums the desktop won't connect to the internet when I put the web address into firefox but if I put in an ip address it connects!  What am I not understanding/doing wrong?

---

### Post by SeijiSensei on 2014-11-27
You don't have name resolution configured correctly.  If you're using static IP addresses, add a "dns-nameservers" line to /etc/network/interfaces in the eth0 stanza as described here: [https://help.ubuntu.com/14.04/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/14.04/serverguide/network-configuration.html#name-resolution).

You can use Google's nameservers if you don't have others you'd prefer.  They have the addresses 8.8.8.8 and 8.8.4.4.

---

### Post by JohninFrance on 2014-11-27
Thanks very much - just put 8.8.8.8 into DNS servers field of the "Edit wired connection" tab IPv4 Settings. Eurica all now works. Again thanks.

---

