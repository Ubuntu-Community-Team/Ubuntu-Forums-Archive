---
title: "wireless networking problems"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by ctdub on 2011-07-17
I can get on the internet with my PC & Vista with a wireless PCI card (Linksys Wireless-N-PCI Adapter, Model# WMP300N) that communicates with a Linksys router (WRT Wirelessm Model# WRT300Nv1).  I no internet connection with ubuntu 11.04.  No wireless connection shows up in the network tool in the preferences tab.  I have tried various suggestions from posts & from Ubuntu Unleashed, to no avail.  I am new to Ubuntu & would appreciate any help.

---

### Post by Cybie257 on 2011-07-17
Try going to:

System -> Administration -> Additional Drivers

Many times I have found that WIFI drivers exist here and get you online.

Let us know if that does anything for you as it is the simplest way to begin. :)

-Cybie

PS. Not too familiar with edubuntu, but the screen shot(s) I glanced at seem to have the same structure and you should be able to use this method to start with.

---

### Post by gandaran on 2011-07-18
> **ctdub said:**
> I can get on the internet with my PC & Vista with a wireless PCI card (Linksys Wireless-N-PCI Adapter, Model# WMP300N) that communicates with a Linksys router (WRT Wirelessm Model# WRT300Nv1).  I no internet connection with ubuntu 11.04.  No wireless connection shows up in the network tool in the preferences tab.  I have tried various suggestions from posts & from Ubuntu Unleashed, to no avail.  I am new to Ubuntu & would appreciate any help.
you may need wireless drivers, if additional drivers don't provide any post the output of
```
lspci
```
and
```
lsusb
```
this finds and shows the wireless chipset then we can check what driver you need to install.

---

### Post by amjjawad on 2011-07-18
> **ctdub said:**
> I can get on the internet with my PC & Vista with a wireless PCI card (Linksys Wireless-N-PCI Adapter, Model# WMP300N) that communicates with a Linksys router (WRT Wirelessm Model# WRT300Nv1).  I no internet connection with ubuntu 11.04.  No wireless connection shows up in the network tool in the preferences tab.  I have tried various suggestions from posts & from Ubuntu Unleashed, to no avail.  I am new to Ubuntu & would appreciate any help.

Hello and Welcome :)

Please post back the output of:

```
sudo lshw -C network

```

Please wrap up the text that you'll post here with "#" at the beginning and at the end.

Thank you :smile:

---

