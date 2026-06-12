---
title: "network manager dns problem"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by radicaledward on 2007-09-29
The network manager is automatically adding my router as a DNS server, which is a problem. I have to manually edit the DNS servers every time I boot my computer. I looked through dhclient.conf, but there does not seem to be any problem. I know I can supersede the sent dns servers, but I'm often on the go, so this is less than ideal.

So my DNS servers look like this when I first connect:
192.168.0.1
192.60.22.2

Instead of:
198.60.22.2
198.60.22.22

I don't think my DHCP server is sending 192.168.0.1 as a DNS server, as its only this one comp on the network with this problem.

---

### Post by MobiusNZ on 2007-09-29
I'd double-check that the dhcp server isn't sending incorrect dns, routers often send their own info.

---

### Post by radicaledward on 2007-10-01
I am almost 100% sure its not the router, as its only on this computer and no others. Is there a way to edit the dhclient.conf to reject a specific dns server?

---

### Post by noob12 on 2007-10-01
Yes, using a **prepend domain-name-servers** or **supersede domain-name-servers** line in **/etc/dhcp3/dhclient.conf**.  Run **man dhclient.conf** for details.

The first section of this HOWTO provides an example of how to do that.  Don't mind the title.  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

