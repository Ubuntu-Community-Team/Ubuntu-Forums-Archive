---
title: "Remove Wicd, install network manager..."
date: 2009-11-21
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-11-21
Hi

I want to remove wicd and reinstall network manager in Karmic.

When I did this the other way round (NM - Wicd) I had to download the wicd package before uninstalling network manager, otherwise I would have had no network connection to fetch wicd with (as I understand it uninstallations happen before installations).

In synaptic, when I select network manager, I no longer have the option to download package only.  Am I missing something?  Synaptic knows it has to remove wicd, will it download the package before uninstalling?

---

### Post by nothingspecial on 2009-11-21
```
sudo apt-get install network-manager
```

should do it.

---

