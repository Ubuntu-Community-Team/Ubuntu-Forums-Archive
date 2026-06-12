---
title: "Unload previous driver in order to use ndiswrapper"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by diminuto on 2007-08-11
Hi,
After being unable to have my wpn311 working with madwifi drivers, I have uninstalled it using apt-get remove. I want to try with ndiswrapper, but it will not work until I remove the previous driver.

After correct installation of the Windows driver, I obtain:

```
ndiswrapper -l
 bcmwl5 : driver installed
       device (0505:4320) present (alternate driver:ath_pci)
```

I have tried with "rmmod ath_pci" and adding "blacklist ath_pci" to etc/modprobe.conf. After rebooting, the same output for ndiswrapper. 

Any idea? Thanks!

---

### Post by spd106 on 2007-08-13
The recommended way is to add ath_hal to the /etc/default/linux-restricted-modules-common file, this will prevent the madwifi driver loading, but will allow you to use other drivers in the restricted modules package. I think the same can be achieved through the System -> Admin -> Restricted Drivers Manager.

Also make sure that you have added ndiswrapper to the /etc/modules file.
I think the command is
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

---

