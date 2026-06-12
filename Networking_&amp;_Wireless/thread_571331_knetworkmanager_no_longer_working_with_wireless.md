---
title: "knetworkmanager no longer working with wireless"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by elusivespoon on 2007-10-09
The short version:
Recently I haven't been able to use knetworkmanager to connect to my wireless network, using an Open System with a WEP key. It could however connect to another network with no key. Now the little kde system tray icon doesn't even display wireless networks, so I can't even attempt to connect with it. However  wlassistant has been able to connect to any network this entire time.  Any ideas for getting knetworkmanager working again?

The long version:
We had a power outage, and for some reason my wireless router crapped out for a little bit. So I connected to a neighbors system that has no WEP key. After being unplugged for a while, my router was good to go, and I connected to it with knetworkmanager. However it kept connecting to my neighbors network by default, so I had to keep switching it back. At some point my network ended up in the "untrusted" list, even though I never did anything intentionally to cause this. Not too long after this I couldn't  even connect to my own network anymore. Though wlassistant could still make the connection, so I know it's not a hardware problem, or my router ( I would just stick with wlassistant, but it doesn't automatically reconnect when the connection is lost). At one point I tried manually configuring my wireless with knetworkmanager, which didn't work either. I deleted my personal rc files for it, and purged and reinstalled the package. And it still didn't work. Sometime after this knetworkmanager just stopped listing any wireless networks. All this time wlassistant can still connect to any network, and list all available networks, but I'd still rather use knetworkmanager. Also, it seems, wlassistant is also using my neighbors network as the default, so knetworkmanager may have affected more config files than I realize.

Hopefully some of that info is useful for finding a solution.

---

### Post by speedkreature on 2007-10-11
I may be having a similar situation.  Which release are you on?  I'm on Gutsy (beta).
KNetworkManager worked while using the live CD, however, I now have kubuntu installed to the harddrive and KNetworkManager no longer reports wireless networks.

Furthermore, I can connect to wireless networks if I manually configure them through KNetworkManager.  KNetworkManager has a RJ45 icon...it's been a LONG time since I've used KDE so I don't remember if there should be a different icon for wireless connections.  

As a side note, the only reason I'm using Kubuntu is because Ubuntu won't boot on my Thinkpad T61.  But that's another issue for another post.

Can you manually configure your networks using KNetworkManager?  Don't forget to enter the default gateway.

---

### Post by elusivespoon on 2007-10-15
I'm running Feisty. And I am able to connect manually with KNetworkManager. I don't think KNetworkManager has a different icon for wireless. Though when it is working right it displays the signal strength, rather than the RJ45 icon.

Hopefully we'll figure this out soon.

---

