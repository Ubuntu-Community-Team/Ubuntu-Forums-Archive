---
title: "Wireless Networks on Toshiba Satellite C55D-A"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by rte4 on 2013-10-03
Hello. Finally got ubuntu 12.04 up and running on my Toshiba Satellite C55D-A thanks to the advice on here. However I cannot view any wireless networks. Internet works fine plugged into an ethernet cable.I get a little wireless icon at the top of the screen, but no networks appear. I've tried checking for additional drivers under system settings, but it did not have anything for my wireless card. From what I've read already; the output of these commands may help figure out what's wrong:

```
nm -tool
```

yields:nm: 'a.out': No such file
(I suspect this is related to the issue...)


```
sudo lshw -v

```

yields:

Hardware Lister (lshw) - B.02.15
usage: lshw [-format] [-options ...]
       lshw -version


	-version        print program version (B.02.15)


format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information


options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)


Thanks,
rte4

---

### Post by steve57 on 2013-10-04
Please look here [http://ubuntuforums.org/showthread.php?t=1968317](http://ubuntuforums.org/showthread.php?t=1968317), or here [http://ubuntuforums.org/showthread.php?t=1970781](http://ubuntuforums.org/showthread.php?t=1970781). Hope you`ll manage with it. Good luck!

---

### Post by rte4 on 2013-10-04
also if it helps the output of 

```
lspci | grep Network

```
 Realtek Semiconductor Co., Ltd. Device 8179 (rev 01)

---

