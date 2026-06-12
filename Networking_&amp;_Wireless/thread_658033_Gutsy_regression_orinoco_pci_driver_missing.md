---
title: "Gutsy regression: orinoco_pci driver missing"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by Geir Smestad on 2008-01-04
I am aware that this topic has been discussed before (fx. [http://ubuntuforums.org/showthread.php?t=595098](http://ubuntuforums.org/showthread.php?t=595098)), but as far as I can see no proper solution has yet been found. The last thread on this topic was in October last year.

My ThinkPad A31 laptop apparently doesn't like the hostap wlan driver. Access points show up in the network manager, but I am unable to connect to any of them. On Feisty, the alternative driver orinoco_pci was included in the kernel, but for some inexplicable reason this module has now been removed:

```

geir@geir-laptop:~$ sudo modprobe orinoco_pci
FATAL: Module orinoco_pci not found.

geir@geir-laptop:~$ lsmod | grep pci
hostap_pci             56976  2 
hostap                114436  1 hostap_pci
pci_hotplug            32704  1 shpchp

```

 I used orinoco_pci on my Feisty install and never had a problem, so this causes a bit of pain for me. Happily, I still have a week to fix it before the semester starts.

Now, I am sort of a newbie when it comes to compiling custom kernels (I never seem to be able to compile *anything* before drowning in error messages) and I don't know how to install an older kernel if that is what's required to get this crucial module back.

The ideal solution would of course be to have someone with the necessary skills and contacts get this on the list of things to include in the next Gutsy kernel update, as I am sure there are still other ThinkPad owners struggling with the same problem.

Lacking that, how can I get a kernel that includes the orinoco_pci driver so I can modprobe it?

[Edit: Oh, and searching for orinoco_pci in Launchpad doesn't give any matching bug report.]

---

