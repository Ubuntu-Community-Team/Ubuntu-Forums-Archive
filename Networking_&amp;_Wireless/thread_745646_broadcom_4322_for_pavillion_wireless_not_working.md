---
title: "broadcom 4322 for pavillion wireless not working"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by kevross_33 on 2008-04-04
Hi I have a HP Pavilion dv6710ea Notebook PC using broadcom 4322ag card. I have fixed most issues with this help:
[http://aldeby.org/blog/?page_id=87#wireless](http://aldeby.org/blog/?page_id=87#wireless).

I have disabled bluetooth (was hanging the system boot) and blacklisted the uvcvideo module so USB would work properly. Now my final problem is with the wireless. At the above link I have used the guide for wireless using the ndiswrapper (which I installed from synaptic) method. nidiswrapper -l shows the driver is installed and have done modprobe and ndiswrapper appears in /etc/modprobe.d (I am not sure that means anything though).

Anyway when booted the wireless switch thing stays orange and iwconfig, ifup etc shows it does not seem to have been detected. Am I doing something wrong or is something different needed?

The system is Ubuntu gutsy gibbon 64bit AMD. the hardware works as I also have 64 bit vista installed and it works fine. Wireless isn't 100% important for me but I would like to get it working as I use Linux 90% of the time.

Thanks for any help provided.

---

### Post by kevross_33 on 2008-04-04
An update, I am making progress. I have used ndiswrapper to install the netathrx (atheros) and this driver says the hardware is there and it can see it. However even after reboot and so on the wireless interface is not there and the light on the wireless switch still stays orange rather than blue. 

output for ndiswrappers -l is:

lxuser@lx:~$ sudo ndiswrapper -l
bcmwl6 : driver installed
netathrx : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

The drivers for windows are here. I have been taking them from my vista on the latop.
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2100&lc=en&cc=uk&dlc=en&product=3664835&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2100&lc=en&cc=uk&dlc=en&product=3664835&lang=en)

Anyone able to help me please with ideas?

---

### Post by acrimotel on 2008-04-28
Same problem here :(

---

### Post by noobwifi on 2008-07-06
Same problem.  Same drivers, different computer... a Sony VAIO w/ Atheros wireless.  Have you found a solution?  I cannot get Madwifi or the NDISWrapper to work.

---

