---
title: "Wireless AC"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by gabriel-6 on 2014-04-03
I purchased a new wireless AC card which is compatible with ubuntu (according to Intel). I installed the firmware, iwlwifi-7260-7.ucode, by moving it to the /lib/firmware directory.

 *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan1
                version: 73
                serial: ac:7b:a1:1d:ef:89
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-19-generic firmware=22.1.7.0 ip=172.16.222.67 latency=0 link=yes multicast=yes wireless=IEEE **802.11abgn**
As you can see, the only 802.11 standards are A B G and N. There is no AC here. 

Is there any way to enable it?

---

### Post by tomearp on 2014-04-03
What version of Ubuntu are you running? Can you please paste the output of
```
uname -r
```
[Post #14 here]("http://www.linux.org/threads/wireless-speed-capped.4324/") shows a response from Intel saying that ac speeds are achievable with a kernel version of 3.13 or greater.

The [Intel site]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm") has two firmware listings for the card, one for 3.10+, one for 3.13+

---

### Post by gabriel-6 on 2014-04-03
3.11.0-19-generic

---

### Post by chili555 on 2014-04-03
Have you read this interesting thread? [http://ubuntuforums.org/showthread.php?t=2178873&highlight=7260](http://ubuntuforums.org/showthread.php?t=2178873&highlight=7260)

---

