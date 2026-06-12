---
title: "Performance Issse of Qualcomm Atheros QCA9377"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by Kittipat_Apichartt on 2016-05-06
Hi,

I am using LENOVO Ideapad 300S with Qualcomm Atheros QCA9377 wifi adapter and I fixed connection problem using this thread

[http://ubuntuforums.org/showthread.php?t=2300861&page=3](http://ubuntuforums.org/showthread.php?t=2300861&page=3)

It worked out fine until I need to run iperf3 to test performance of wifi and it got only 7 Mbps throughput while the same machine using Windows 10 gets around 40-50 Mbps. I am quite sure it is the driver issue of the adapter because all the environments are invariant (wifi network and iperf server) but unsure how to solve it. I look forward to seeing response from Ubuntu and Linux experts here soon.

Regards,
Patrick

---

### Post by jeremy31 on 2016-05-06
Welcome to the forums.  Those instructions are somewhat deprecated now.  Please post the results of ```
uname -a; modinfo ath10k_pci
```

I am thinking a much newer version of backports may fix this

---

