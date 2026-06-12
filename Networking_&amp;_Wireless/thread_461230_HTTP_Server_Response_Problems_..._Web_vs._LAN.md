---
title: "HTTP Server Response Problems ... Web vs. LAN"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by DarkHorizon on 2007-06-01
Hi all,

Before I added a wireless router (D-Link WBR-1310) to my network, my home LAN setup was configured as such:

[FONT="Courier New"](internet) <--> DSL modem <--> Ubuntu 6.04 webserver/gateway/router <--> LAN PCs[/FONT]

After the addition of the wireless router, I removed the Ubuntu server's routing capabilities, and added port-forwarding in the router to the webserver's IP address. The network is currently configured as such:

[FONT="Courier New"](internet) <--> DSL modem <--> wireless router ---> LAN PCs and  Ubuntu 6.04 webserver[/FONT]

The problem that arose since this change, is that LAN PCs can no longer access the webserver by registered domain name or ISP-assigned IP address ( 66.11.160.188 ), only by the webserver's LAN IP address. I have multiple domains hosted off the webserver, and accessing any of them from a LAN PC results in a timeout error in the web client browser.

After some digging around, I installed WireShark on the webserver, and captured packet data coming from a LAN PC. The first image below is a 'success' hit on the webserver's IP address. The second image is a 'failure' timeout on one of the registered domain names/ISP-assigned IP address.

[Success]("http://kingsbury.cjb.net/images/success.png")
[Fail]("http://kingsbury.cjb.net/images/fail.png")

My iptables ruleset isn't actively blocking syn/ack/rst flags in packets, so I am unsure what I can do to resolve this problem. I guess I should note too that if I accept all incoming traffic in iptables, the problems listed above are not resolved.

Any ideas?

Best regards,

---

### Post by netztier on 2007-06-01
> **DarkHorizon said:**
> Hi all,
Any ideas?


Probably this: [http://ubuntuforums.org/showthread.php?t=439036](http://ubuntuforums.org/showthread.php?t=439036)

You can't connect to your external IP address with most NAT routers, which Is good (IMHO).

best regards

Marc

---

