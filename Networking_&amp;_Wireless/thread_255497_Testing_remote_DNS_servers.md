---
title: "Testing remote DNS servers"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by Tortanick on 2006-09-11
Is there a commandline application that lets me type in an IP address, it then uses that IP as a DNS server and says if the server is working.

Prefrably it will have the ability to give it a whole batch then get the results.

---

### Post by NetworkGuy on 2006-09-11
Look into a program called dig.

From a terminal type man dig to get the directions on how to run it.

You can point it to a DNS server and then have it reply with an IP address.

---

### Post by tbonius on 2006-09-11
nslookup or dig will do the trick.

nslookup

server 192.169.0.1 (or whatever IP you wish to try)

Now simply type a FQDN to see if it resolves

---

### Post by Tortanick on 2006-09-12
Thanks both of you.

---

### Post by jelevin on 2007-01-03
I've managed to uninstall dig.  Could someone point me to the package necessary to reinstall it?  I've only been able to find "host", but I'm using webmin, and it is looking for either dig or nslookup to be installed.

Thanks!

---

