---
title: "Proxy with DHCP?"
date: 2015-05-18
forum: Networking &amp; Wireless
---

### Post by zoomiest2 on 2015-05-18
Just a quick question that I couldn't resolve by googling it...

I just set up a squid/squidguard poxy server (Ubuntu server 14.04) with two NIC cards, to do content filtering for my teenage boys, for our home.
The squid proxy box will sit in between the Internet modem and the Linksys wireless router (with its own dhcp server).

Do I need to install a dhcp server on my proxy/squid box, to generate an IP for the Linksys router, or am I okay to just configure a static IP on the NIC facing the Linksys router? 

I just have a vanilla Ubuntu 14.04 installation, and have not installed anything else. Anything I am missing?

---

### Post by SeijiSensei on 2015-05-18
if the Squid proxy is between the local network and the router, then it needs to run a DHCP server.  Machines on the local network won't be able to see the router in this configuration.

What about other services like HTTPS?  Any other things people behind the Squid box might need to do besides browse the web?  If so, the box will need to have "masquerading" and packet forwarding enabled as well.  See:  [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

You'll also want to look into "[transparent]("http://ubuntuserverguide.com/2012/06/how-to-setup-squid3-as-transparent-proxy-on-ubuntu-server-12-04.html")" proxying.  Otherwise you'll need to configure the browsers on the client machines to use the proxy.  Intelligent kids will learn right away to disable that and avoid the proxy entirely.

---

### Post by zoomiest2 on 2015-05-18
Thank you!!!

---

