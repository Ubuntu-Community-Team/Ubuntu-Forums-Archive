---
title: "[SOLVED] Asus WL-138 v2 and Dlink DIR-451"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Phoenixzeus on 2008-10-07
Hello,

I am currently having troubles associating an Asus WL-138G V2 wireless PCI card to a D-Link DIR-451 3G router. The drivers for the wireless card are installed correctly using NDISWrapper, as I can connect to any other wi-fi AP in the area, and also to my other test AP's. The Asus WL-138G V2 wireless card in question uses a BCM43xx chipset and our test machine is running Ubuntu Desktop 8.04 32bit.

Windows XP boxes can connect to this new D-Link router without problems, and my laptop which has an Intel wireless chipset and Ubuntu 8.04 can connect flawlessly to the new Dlink Router. I was wondering if anyone has run into any issues between the Asus WL-138 V2 and the Dlink DIR-451 before and managed to get them resolved?

Thanks for any help,
Phoenixzeus

P.S. We've tried without encryption AND using WEP with no luck.

---

### Post by Phoenixzeus on 2008-10-07
**Update:**

We've now tried the Asus WL-138G V2 card with the native BCM43xx drivers and bcm43xx-fwcutter instead of NDISWrapper and the Asus drivers off the CD, with the same result - we can see the ESSID of the D-Link router, but every time we try to associate with it, it thinks for a minute and then drops back to the authentication screen asking for a key again. 

We've just tried a Netgear WG311 PCI card using NDISWrapper and it works fine, so we're really confused now - we're about to retry the Asus card with a different version of NDISwrapper and the latest drivers for the card from Asus's website ...

Will keep you posted.

---

### Post by Phoenixzeus on 2008-10-15
To anyone that is looking at this, I have marked this thread as solved, as we have given up on the project.

---

### Post by jungletek on 2010-02-03
I know this is marked solved...

But did you consider the fact that for most broadcom based cards, WPA2 apparently isn't fully supported? I had the exact same issue as you, and was annoyed, until I remembered I'd read that fact somewhere the first time I tried to get the card recognized on an older distro.

Solution was to change the wireless encryption on the router from WPA2 to WPA.

---

