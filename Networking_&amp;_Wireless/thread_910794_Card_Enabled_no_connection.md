---
title: "Card Enabled no connection"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by acmariner99 on 2008-09-04
Hey all. I finally got wireless last night using a good guide posted on this forum. But after downloading the latest updates and rebooting (provided the updates had anything to do with it) I can enable my card, but I cannot get internet. I went back through the b43 guide, mods were loaded properly, conflicting modules were blacklisted (ndiswrapper and bcm43xx). I know wireless works because I had a connection until shutdown yesterday. but my lspci -nn is posted anyway. To my knowledge my network settings are correct. I have kernel versions 6.24-16 through 19.

06:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

If someone suggests ndiswrapper, tell me where to get the proper drivers.

Any suggestions would be helpful.

---

### Post by Ayuthia on 2008-09-05
> **acmariner99 said:**
> Hey all. I finally got wireless last night using a good guide posted on this forum. But after downloading the latest updates and rebooting (provided the updates had anything to do with it) I can enable my card, but I cannot get internet. I went back through the b43 guide, mods were loaded properly, conflicting modules were blacklisted (ndiswrapper and bcm43xx). I know wireless works because I had a connection until shutdown yesterday. but my lspci -nn is posted anyway. To my knowledge my network settings are correct. I have kernel versions 6.24-16 through 19.

06:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

If someone suggests ndiswrapper, tell me where to get the proper drivers.

Any suggestions would be helpful.
To start things off, you can try the following:
```
sudo modprobe -r bcm43xx ndiswrapper wl b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

If it does not work, can you post the results of:
```
lshw -C network
```

You should not need to use ndiswrapper.  The 4311 rev 01 card works pretty well with the b43 module.

---

