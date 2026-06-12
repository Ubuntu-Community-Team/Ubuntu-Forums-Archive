---
title: "Intel PRO/Wireless 3945 driver"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by mevets on 2007-07-14
I recently tried installing Debian Etch and it rose some questions for me. I tried to resize my Ubuntu partition but it wouldnt due to some error, thats another problem though. Debian wasnt able to establish an IP via DHCP so obviously it couldnt work with my wireless card. Now, under Ubuntu, the Intel(R) PRO/Wireless 3945 Network Connections driver for Linux has to be loaded. It appears in the restricted-manager. I thought Intel was mostly open with their hardware  drivers. Does this mean the driver I'm using is closed source?

Also, if anyone would be kind enough to fill me in on a few other things, since I wasnt able to completly install Debian... does anyone know if Debian will load this driver for me? Will Debian load any proprietary drivers at all? Most search for Debian's stance on proprietary drivers by default return results on Ubuntu's stance, though I have a feeling Debian will not load anything closed.

Thanks

---

### Post by 5-HT on 2007-07-15
> **mevets said:**
>  I thought Intel was mostly open with their hardware  drivers. Does this mean the driver I'm using is closed source?

The ipw3945 driver requires a binary microcode image and a binary regulatory deamon, which is why it requires Ubuntu's restricted modules.
Intel's iwlwifi driver, currently in development, takes advantage of the new mac80211 wireless stack in 2.6.22 does away with the need for the regulatory daemon.

> **mevets said:**
> ...does anyone know if Debian will load this driver for me?
Absolutely! You need to install the microcode, regulatory daemon, and driver separately though:
```

firmware-ipw3945
ipw3945d
ipw3945-modules-2.6-686
```The module itself is available compiled against many different kernels under ipw3945-modules-<kernel_flavour>. A quick apt search or visit to packages.debian.org can clear up which one you need. 
cheers,

---

