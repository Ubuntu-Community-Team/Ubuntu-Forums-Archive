---
title: "Help req to uninstall Google Earth"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Peterfc on 2009-03-26
Hi

I have tried to uninstall Google Earth using Synaptic Package Manager. I have reinstall and uninstalling  a number of times. In Applications/ Internet Google Earth is still listed and installs but does nothing when an address is put in. I have gone to the Places/ Home folder and deleted the Google Earth folder. I found nothing in the Application/Add/remove  

I would like to remove all traces from my machine and start again if it's possible to get running if not Just use Google maps.



Dell dimension 2400 Dvd Rw 1gb ram 200gb h/drive everything else onboard.

Thanks

---

### Post by billgoldberg on 2009-03-26
> **Peterfc said:**
> Hi

I have tried to uninstall Google Earth using Synaptic Package Manager. I have reinstall and uninstalling  a number of times. In Applications/ Internet Google Earth is still listed and installs but does nothing when an address is put in. I have gone to the Places/ Home folder and deleted the Google Earth folder. I found nothing in the Application/Add/remove  

I would like to remove all traces from my machine and start again if it's possible to get running if not Just use Google maps.



Dell dimension 2400 Dvd Rw 1gb ram 200gb h/drive everything else onboard.

Thanks

open up a terminal and enter:

```
sudo apt-get autoremove googleearth --purge
```

That should do the trick

In your home folder, press "ctrl+h" and make sure there is no hidden folder for googleearth remaining.

---

