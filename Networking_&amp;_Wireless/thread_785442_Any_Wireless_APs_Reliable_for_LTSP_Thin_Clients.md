---
title: "Any Wireless APs Reliable for LTSP Thin Clients?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by haz2a on 2008-05-07
I have been struggling with Linksys WAP54G's (problems described here: 
[http://ubuntuforums.org/showthread.php?p=4897647#post4897647](http://ubuntuforums.org/showthread.php?p=4897647#post4897647)) and I wondered if anyone has had success with wireless thin clients, and if so exactly what models, and what tweaks if any?

---

### Post by sjude on 2008-06-15
I would also like to know how to configure a thin client over wireless link.  Usually PXE boot works only when Ethernet is connected (wired).

---

### Post by jpaulb on 2008-06-27
> **sjude said:**
> I would also like to know how to configure a thin client over wireless link.  Usually PXE boot works only when Ethernet is connected (wired).
I use an ASUS Wireless AP WL-330g to connect between a IBM think pad A30 and the server.
The built in wireless on a laptop or a wireless card require the installation of a driver before they will function, that kind of leaves out thin client wireless booting.

The ASUS is a wireless internet adaptor which plugs into the network of the thin client, so when you boot anything that your network card does is transmitted by the adaptor

I wrote a how to a few years ago which you can find at this location
[http://www.linuxagora.com/vbforum/showthread.php?t=355](http://www.linuxagora.com/vbforum/showthread.php?t=355)

---

### Post by haz2a on 2008-07-22
Since there have been no recommendations for currently available wireless devices, and having heard about Devolo HomePlug powerline being used, I have now started using Zyxel PLA-401 HomePlug devices.
These are proving to be very reliable in our light industrial environment.

One negative is that Windows XP+ must be used to setup encryption - they are insecure as supplied. Perhaps any of the HomePlug-compatible devices would work as well, and maybe some of them have web interfaces so they can be configured from any browser.

---

