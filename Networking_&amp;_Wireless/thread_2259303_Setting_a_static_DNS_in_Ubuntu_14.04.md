---
title: "Setting a static DNS in Ubuntu 14.04"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by kidzstang on 2015-01-03
I have been trying to connect my Ubuntu machines to my Windows 2000 Server Domain using Likewise without much luck (although I have learned a lot). I have some oddities in my network setup for specific reasons and wonder if I will ever be able to connect the Ubuntu machines to the Windows network.

Background of Network Setup:
I have a Comcast Business ISP account and have set the Comcast wired router up as the DHCP server (this is because I have other PCs that I just need to send out to the internet without interfacing the Windows 2000 Server). Also because the W2000 server is an old machine I don't want to forward all internet traffic through it.
I have the W2000 Server on the same subnet mask as the Comcast wired router.
I have the Comcast wired router (DHCP server) set to use the Comcast DNS Server instead of the W2000 DNS Server (again, because I have a few machines that I do not want to connect to the W2000 Domain).
I can connect my Windows machines to the W2000 server to share files without problems.
I have set the W2000 DNS Server to forward to the Comcast DNS Server IPs.
I can see the W2000 domain on the Ubuntu machines when I do a browse within the Ubuntu Files Manager.

I am resolving to the main Comcast IP on the Ubuntu machines (in /etc/resolv.conf), not the same DNS servers that the Windows machines are using and I have good internet connections on them.

When trying to connect to the W2000 Domain with the Ubuntu machines using Likewise I get the all too common DNS_ERROR_BAD_PACKET message. I assume that this is because it cannot find my local W2000 Domain using the Comcast DNS Server (this makes sense that it wouldn't).

When I open the /etc/resolv.conf it says that any changes will be overwritten.

The question is: Is there a way to statically point to a specific DNS Server in Ubuntu 14.04? ):P

Many thanks for any help that y'all could provide.
Cheers,
jack

---

### Post by kerry_s on 2015-01-03
click on the internet icon-> edit connections-> ipv4
change automatic to manual & do your thing

---

### Post by kidzstang on 2015-01-03
> **kerry_s said:**
> click on the internet icon-> edit connections-> ipv4
change automatic to manual & do your thing

Holy crap! Thank you very very much! It worked like a charm.

---

### Post by kerry_s on 2015-01-03
your welcome!

---

