---
title: "Problems with Edgy Wireless solved..."
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by dlane on 2006-12-14
After agonising for weeks and scouring the Ubuntu forums for solutions to my problems connecting to my wireless network after upgrading from Dapper to Edgy, I've finally found the solution.  Turns out it was my wireless access point's firmware!!  I upgraded my 3Com OfficeConnect AP's firmware to the latest release, and everything is suddenly sweet again.  So, if you're having problems with WPA encryption (I use WPA personal, by the way, with a passphrase) with Network Manager (with the security credentials stored and handled by the Gnome Keyring manager) and connecting to your network check to see if your AP has any firmware updates available!!   It's possible that Edgy's network infrastructure is more discerning/correct about interpreting network credentials than that in Dapper, which is why things broke - not because Edgy was a regression.

For the record, my wireless chipset is an Intel ipw2200 installed in an ASUS M3N laptop.    The symptoms I was experiencing following the upgrade to Edgy: attempts to join the WPA encrypted wireless network did not properly apply the stored WPA passphrase - the Network Manager would try to join the network as though it was unencrypted (the log info in /var/log/syslog indicated that it though the network was unencrypted - this was due to a bug, as far as I can tell, in the AP's firmware and its reporting).   The worst thing: it would *occasionally* join, like every few days or so... That really freaked me out.  Dodgy embedded proprietary software ;P

Hope this helps someone!

Dave

---

