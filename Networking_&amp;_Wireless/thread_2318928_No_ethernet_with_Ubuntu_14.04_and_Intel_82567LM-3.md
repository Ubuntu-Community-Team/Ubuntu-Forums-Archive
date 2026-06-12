---
title: "No ethernet with Ubuntu 14.04 and Intel 82567LM-3"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by Kevin_Morisette on 2016-03-30
I installed Ubuntu 14.04 and during the install it couldn't find the network driver. I finished the install without it and now I can't seem to get it working. Doing lspci shows the Intel 82567LM-3 listed, and I've done 'modprobe e1000e' and it will show in dmesg (although sometimes it takes a while to finish the command). However, in /sys/class/net only the loopback interface is there. The module seems loaded if I do a 'lsmod | grep e1000e'. Any ideas what I could try next? Should I download the module from Intel's website?

---

### Post by Kevin_Morisette on 2016-03-30
Also, doing 'lshw -C network' says the device is UNCLAIMED, so I'm guessing the e1000e driver/module isn't the correct one for this?

---

