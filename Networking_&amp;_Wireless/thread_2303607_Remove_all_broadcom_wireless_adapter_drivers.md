---
title: "Remove all broadcom wireless adapter drivers"
date: 2015-11-20
forum: Networking &amp; Wireless
---

### Post by roma24ster on 2015-11-20
I've been playing around trying to get my broadcom 4352 to work as per [this]("http://ubuntuforums.org/showthread.php?t=2303543") thread (still no luck), but I think i've made a mistake somewhere and now I would like to completely remove all all the broadcom drivers and try again.

In the additional drivers application, i've selected no driver for the broadcom 4352, and it tells me the device isn't working, I've also gone into synaptic and removed anything I can see related to broadcom (such as bcmwl-kernal-source). 

However it seems my wireless device is still active, I can still see wireless networks.

I've redone the wireless script info, my results are [here]("http://paste.ubuntu.com/13362591/").

Could someone help me just remove all my broadcom drivers so I can start again from scratch?

---

### Post by Hadaka on 2015-11-20
Hi, you have the correct driver loaded...wl but you also have
some b43 files. open a terminal and do,,
```
sudo apt-get remove --purge firmware-b43-installer
```
then do..
```
sudo modprobe wl
```
you should have working wireless.

*If you want to remove the current and correct broadcom-kernel-source driver
then do.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
thanks.

---

