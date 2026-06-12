---
title: "wpa-psk on ipw2100 auto deassociating problem"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Goshawk on 2007-05-06
Hi,
i'm trying to connect to a wpa-psk AP, and using networkmanager or wpa_supplicant i can connect to it.
But after a while that i'm connected, my ubuntu feisty system disconnects from the network. Using wpa_supplicant i can see:
```

[...]
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
BSSID 00:X:X:X:X:X blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
[...]

```
i've changed the mac address of the ap with X. I'm using a :
01:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
with ipw2100 driver.
Does anybody know how to solve it? Why my card recognizes 00:00:00:00:00:00 as an AP?

Thanks

---

### Post by soloslinger on 2007-05-12
This isn't just a ubuntu issue.  I am having the same problem on gentoo, same card, same drivers.  I'm going to keep looking but if I find something Ill come back here and post what I got so perhaps it helps someone here.

[http://forums.gentoo.org/viewtopic-t-558812.html](http://forums.gentoo.org/viewtopic-t-558812.html)


soloslinger

---

### Post by soloslinger on 2007-05-12
Well I found out how to do this. :)   The link to the forums above has lots of snippets of configs if its easier to look at those.  The heart of the problem was that the wireless encryptions that I was using weren't compiled into the kernel directly, they only existed as modules.  Compiling them in directly, not using a timeout seemed to do the trick.

(I know its not ubuntu but I was looking here for answers and saw people with the same problem)
soloslinger

---

