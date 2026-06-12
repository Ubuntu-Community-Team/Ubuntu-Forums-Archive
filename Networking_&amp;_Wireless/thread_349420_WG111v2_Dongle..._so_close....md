---
title: "WG111v2 Dongle... so close..."
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by damokay on 2007-01-30
Hi, I apologise if this has been covered before (I am sure I have seen it mentioned on this forum but don't remember seeing a solution).

I have a Netgear WG111v2 and, having followed various "how to"'s on this site, I have managed to get it configured and working with my wireless router :D  

However, there is one unresolved issue - If I leave the dongle in and start my pc it won't work and the iwconfig commands I issue give me "Operation not allowed" (or similar) responses. If I start the pc without the dongle connected and then plug it in once I have logged in the iwconfig commands work fine and, Hey Presto, I have a network!

I would be grateful if anyone got any ideas?

BTW, I am an absolute novice with Linux but so far I'm very impressed with Ubuntu... I just don't want to have to remember to unplug my dongle every time I boot up :( 

Thanks in advance,
Damo.

---

### Post by damokay on 2007-01-30
OK - I got it sorted!

I had to add more drivers to the blacklist file. For those who may encounter the same problem here is the complete list (this may be overkill, but better safe than sorry):

blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist rtl818x
blacklist r8187b
blacklist r818x
blacklist r8187

After this I just had to modify the /etc/network/interfaces file and everything starts up automatically :D

---

