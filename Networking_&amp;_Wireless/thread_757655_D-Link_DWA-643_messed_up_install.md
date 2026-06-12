---
title: "D-Link DWA-643 messed up install"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by uado on 2008-04-17
Hi everybody,
I'm very new to Linux and have managed to mess up the install of the aformentioned NIC on my XPS M1330.
I put it in and set it up successfully with ndiswrapper and the drivers off the installation CD, but then realised it doesn't allow for monitor mode, which was the reason I bought this card. (BTW, I'm a fledgling network admin and found I could learn a tonne more than Windows could ever teach me about networking by going the Linux route.)
So, I got hold of madwifi tar, attempted to remove the ndiswrapper, and attempted to install madwifi. 
Badly. 
Now, iwconfig only shows my onboard wireless NIC, lspci shows the PCI Express slot, but no card.
I now know (hindsight is great isn't it?) that the card is recognised and works fine from within Linux because when it's plugged in and run the boot CD it works great.
So, plain and simple, I screwed the install and have no idea where to go to uninstall/amend anything I've done so far.
Any help will be gratefully received.

---

### Post by uado on 2008-04-17
Woo hoo! Nailed it! Used the information in the following link:

[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

---

