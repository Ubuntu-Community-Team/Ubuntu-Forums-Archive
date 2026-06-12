---
title: "HostAP with BCM"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2008-04-15
Hey, I have a notebook running a BCM43xx card. I want to run HostAP on it but don't know if it will work with that card? Does anyone know? If it won't, can you tell me what will? Thanks.

---

### Post by chili555 on 2008-04-15
[http://en.wikipedia.org/wiki/HostAP](http://en.wikipedia.org/wiki/HostAP)

Your Broadcom chipset is not the same thing as Prism2/2.5/3. Sorry.

> If it won't, can you tell me what will?Make it an access point? Sorry, I don't know. Make is work just to get on the web? ndiswrapper seems to be the preferred method. [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Edit: Synaptic says *hostapd*:> hostapd works with the following drivers:

 * Host AP driver for Prism2/2.5/3,
 * Prism54 driver for Intersil/Conexant Prism GT/Duette/Indigo,
 * madwifi driver for cards based on Atheros chip set (ar521x),
 * Any wired Ethernet driver for wired IEEE 802.1X authentication.However, it looks like *hostap-utils*, which says it works with Prism 2/2.5/3, is the access point package. In any event, your Broadcom is none of these.

---

### Post by TorchlightJay on 2008-04-16
Cool. I have a Belkin PCMCIA Card somewhere and I know for a fact it uses madwifi. Looks like I can still have my wireless access point. Thanks for your help.

---

