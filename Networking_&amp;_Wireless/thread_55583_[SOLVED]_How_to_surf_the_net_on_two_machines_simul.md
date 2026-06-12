---
title: "[SOLVED] How to surf the net on two machines simulteneously?"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by kagashe on 2005-08-09
Hi,

I have installed Ubuntu 5.04 on my Laptop and I connect to internet through CDMA Mobile phone using ppp0. I have an old desktop with Windows 98 Pentium 1 CPU. I have connected the Laptop and the Desktop through LAN card.

I would like to surf the net on the desktop also through the LAN connection to the Laptop. I don't know much about Networking. I was having a LAN internet connection before buying the mobile and I could individually configure eth0 interphase on the Laptop (in Linux) and the desktop (in Windows 98) but I don't know how to configure this type of connection (may be my Laptop is going to be a proxy for the desktop but how?).

kagashe

---

### Post by varunus on 2005-08-09
You need a router to split network connections.  Here's best buy's rather simple but still useful guide on home networking:
[http://www.bestbuy.com/site/olspage.jsp?guideID=1043363121208&categoryRep=cat01000&type=page&cmp=&id=cat12077](http://www.bestbuy.com/site/olspage.jsp?guideID=1043363121208&categoryRep=cat01000&type=page&cmp=&id=cat12077)

---

### Post by kagashe on 2005-08-09
[QUOTE=varunus]You need a router to split network connections.  Here's best buy's rather simple but still useful guide on home networking:
[http://www.bestbuy.com/site/olspage.jsp?guideID=1043363121208&categoryRep=cat01000&type=page&cmp=&id=cat12077](http://www.bestbuy.com/site/olspage.jsp?guideID=1043363121208&categoryRep=cat01000&type=page&cmp=&id=cat12077)[/QUOTE]
I am sorry. Why do I need additional hardware when the Laptop is already connected to the net through USB modem and the desktop is connected to the Laptop through LAN. My question is how can I use the Laptop as a proxy for the desktop?

kagashe

---

### Post by varunus on 2005-08-09
Ohh.  Sorry, I misunderstood your post.  Sorry, my bad.

To do this, you'll want to set your laptop up as a DHCP server.  I believe the linux software "firestarter" can do this graphically; you can get it through synaptic, just enable internet connection sharing in firestarter.

---

### Post by az on 2005-08-09
Internet connection sharing is called masquerading or NAT (network address translation) in technical terms.  Firestarter can do this for you.  Shorewall can do this too, but it does ot have a GUI interface.

Basically, route the connection from your internet to your ethernet card.  You can set up a dhcp server or just5 use a static network connection.  Be sure to set up both interface so they are on different networks so that your box can route from one to the other.

---

### Post by kagashe on 2005-08-09
Thank you very much. I found very nice guide on Firestarter web site:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

I have used ppp0 for internet (instead of eth0) and eth0 on my local network.

I have set up static I.P. addresses on both the machines as suggested and the job is done.

kagashe

---

