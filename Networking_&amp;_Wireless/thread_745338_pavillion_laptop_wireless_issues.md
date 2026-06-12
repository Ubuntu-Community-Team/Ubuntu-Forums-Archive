---
title: "pavillion laptop wireless issues"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by kevross_33 on 2008-04-04
Hi I have a HP Pavilion dv6710ea Notebook PC. I have fixed most issues with this help:
[http://aldeby.org/blog/?page_id=87#wireless](http://aldeby.org/blog/?page_id=87#wireless).

I have disabled bluetooth (was hanging the system boot) and blacklisted the uvcvideo module so USB would work properly. Now my final problem is with the wireless. At the above link I have used the guide for wireless using the ndiswrapper method. nidiswrapper -l shows the driver is installed and have done modprobe and ndiswrapper appears in /etc/modprobe.d (I am not sure that means anything though).

Anyway when booted the wireless switch thing stays orange and iwconfig, ifup etc shows it does not seem to have been detected. Am I doing something wrong or is something different needed?

The system is Ubuntu 64bit for AMD. the hardware works as I also have 64 bit vista installed and it works fine. Wireless isn't 100% important for me but I would like to get it working as I use Linux 90% of the time.

Thanks for any help provided.

---

