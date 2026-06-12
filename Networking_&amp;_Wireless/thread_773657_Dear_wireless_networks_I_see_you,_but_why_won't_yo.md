---
title: "Dear wireless networks: I see you, but why won't you let me connect..."
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by mr_burns on 2008-04-29
Hi, I'm looking for some help getting my wireless to connect properly.  

First, my stuff:
xubuntu 8.04
Dell Latitude laptop from 2002
Linksys WPC54G v2 PC Card
Netgear WG112 v2 USB adapter (used as an alternate connection method)

My problem:
Can't connect to a secured (WPA2) wireless network.

More details:
My computer displays both the Linksys wireless card and the Netgear USB adapter in the GUI networking interface.  In the networking interface, both wireless devices display the local wireless networks available, so they seem to working, at least to some extent.  I was able to connect to an unsecured network twice with the Linksys card, but subsequent attempts strangely failed.  Neither device has connected successfully using WPA/WPA2 security.  In fact, only the Netgear device seems to support a WPA/WPA2 password option.

Any ideas on what to do?  Thanks.

---

### Post by ahoffme on 2008-07-17
Same problem, please help.

---

### Post by kevdog on 2008-07-17
Try making a manual connection: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

or updating to svn 0.7 network manager (thread in community cafe)

or trying latest wicd.

---

### Post by ahoffme on 2008-07-28
Manually configuring the connection via command line worked. THANKS.

---

