---
title: "Having problems accessing webserver, inside the network, using public domain name."
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2015-02-06
I've got an ubuntu server that's running apache and has Zurmo, which is a crm software.  The crm software likes to redirect every page to my public domain name, which is controlled by a dynamic dns server.  I have a dhcp server and a dns server active on the network also.  What do I have to do, to be able to use my public domain name from within my lan?  I want to be able to do this will all of the computers on my lan.

thanks in advance

---

### Post by Doug S on 2015-02-10
It sounds as though you are already almost setup for what you want to do. I have my bind9 DNS setup for resolving my public domain name to internal IP addresses, and my DHCP server setup to deliver the internal DNS address with the IP address lease. Use the [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/dns.html") for DNS setup and just make your zones inernal (and the example in the serverguide, is for an internal situation).

Note that I do not have any externally facing DNS, and that is taken care of by my ISP. If a computer (such as a laptop) is taken outside of my LAN, it would get the "real" external IP address for my domain from whatever nameserver the external DHCP tells it to use.

---

### Post by pepsifx357 on 2015-02-14
I'm going to have to come back to this.  I've sorta got it working by telling my dns server that the ip address to the webserver was the internet domain name, but it's one of those things where sometimes it works and sometimes it doesn't.  I think that this AT&T modem/router I've got is the issue.  I don't think the dhcp server is actually turned off.  It's not clear if I turned it off or not.  I'm going to see if I've got an old modem laying around and try that.

Thanks for the help though!

---

