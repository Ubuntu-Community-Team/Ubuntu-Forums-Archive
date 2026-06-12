---
title: "wireless network key problems"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by NickUhlig on 2007-07-25
Hi all;

I set up Ubuntu 7.04 on my laptop about a month ago, and everything worked fine until recently.  I was downloading some stuff using BitTornado, and I noticed that my download speed was unusually low.  I disconnected from my home wireless network and tried to reconnect, but it wouldn't.  It kept saying "waiting for wireless key" for the network, even though I had already put in the password for the keyring manager when I booted up.  

Previous to this, it had stopped prompting me for the keyring manager password when I brought the computer out of standby mode, and thus I could not connect to my wireless network (once, the icon even failed to appear).  

I thought that maybe there was a problem with the key itself, so I deleted it from keyring manager, but all that accomplished is that now I have to put in the password for my wireless network when i try to connect, and still it says "waiting for wireless key". 

Any ideas?

Nick

---

### Post by kevdog on 2007-07-25
You could try connection manually by making changes in the /etc/network/interfaces file.

Something like
```
auto *interface_name*
iface *interface_name* inet dhcp
  wireless-mode managed
  wireless-essid *ESSID_of_router*
  wireless-key XXXXXXX <----hex key here
```

---

