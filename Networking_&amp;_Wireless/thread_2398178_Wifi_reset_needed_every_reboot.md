---
title: "Wifi reset needed every reboot"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by jolindbe on 2018-08-08
Hi,

I've had this problem for quite a while now - actually since a software update back in April. Since it is only a problem after reboot and can easily be bypassed I haven't got around to trying to solve it until now...

Every time I boot my laptop it refuses to see any wireless networks. Ethernet is fine. "Enable Wi-Fi" is selected in the menu bar, but it doesn't find any networks at all. Rebooting does not help. Running "sudo service network-manager restart" solves the problem until the next reboot.

I have a Lenovo Thinkpad T430s running Ubuntu 16.04 LTS, and here is some info from lshw (taken when wifi is working) which might be useful to you:

>        description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a4:4e:31:c6:f0:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-131-generic firmware=18.168.6.1 ip=192.168.0.116 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:f1c00000-f1c01fff

Coincidentally, at the same time this bug started, another bug also started. [I have posted about that one in a more relevant sub-forum]("https://ubuntuforums.org/showthread.php?t=2398180&p=13790421#post13790421"), but in case it would be related (which sounds unlikely): At every reboot I would get a "Your system is running in low-graphics mode" message, and after selecting "Try running with default graphics mode" the bootup completes normally, and I don't see this until the next reboot.

Please let me know if you need more info, outputs, etc. Many thanks!!

---

### Post by jolindbe on 2018-08-17
Upgrading to 18.04 seems to have fixed both issues.

---

### Post by uncielser456 on 2018-08-17
Glad you resolved this one. One of my Lenovo ideapad's been acting the same way. Don't know yet if it would work, but I'm gonna try anyway. Thanks

---

