---
title: "Network interfaces renamed after boot with Ubuntu Server 22.04.3"
date: 2023-10-04
forum: Networking &amp; Wireless
---

### Post by pook2022 on 2023-10-04
I installed Ubuntu Server 22.04.3 on an old Xeon thing I found that's been sitting on a shelf for 10 years.
I added 2.5gbps network and USB 3.1 cards to give it a little bit of love.

The problem I have is that each time it reboots the network interfaces have a different name.
enp5s0 and enp8s0 the first time I booted it.
enp6s0 and enp9s0 the second time.
I had a look around but all the similar discussions are from a decade ago.

I don't "think" it's necessarily a problem with the card because the onboard network interfaces gets a new name each reboot too.

Whats the recommended way to fix this problem now?

lspci
```
06:00.0 Ethernet controller: Intel Corporation Ethernet Controller I225-LM (rev 03)
09:00.0 Ethernet controller: Intel Corporation Ethernet Controller I225-LM (rev 03)

```

dmesg | grep enp
```
[    7.200616] e1000e 0000:0a:00.0 enp10s0: renamed from eth1
[    7.985246] e1000e 0000:00:19.0 enp0s25: renamed from eth0
[   10.102087] igc 0000:06:00.0 enp6s0: renamed from eth2
[   10.781017] igc 0000:09:00.0 enp9s0: renamed from eth0
```

dmesg | grep igc
```
[    6.685513] igc 0000:06:00.0: PCIe PTM not supported by PCIe bus/controller
[    7.005279] igc 0000:06:00.0 (unnamed net_device) (uninitialized): PHC added
[    7.158821] igc 0000:06:00.0: 4.000 Gb/s available PCIe bandwidth (5.0 GT/s PCIe x1 link)
[    7.262627] igc 0000:06:00.0 eth2: MAC: 24:5e:be:84:32:99
[    7.456380] igc 0000:09:00.0: PCIe PTM not supported by PCIe bus/controller
[    7.985387] igc 0000:09:00.0 (unnamed net_device) (uninitialized): PHC added
[    9.741208] igc 0000:09:00.0: 4.000 Gb/s available PCIe bandwidth (5.0 GT/s PCIe x1 link)
[    9.883868] igc 0000:09:00.0 eth0: MAC: 24:5e:be:84:32:98
[   10.102087] igc 0000:06:00.0 enp6s0: renamed from eth2
[   10.781017] igc 0000:09:00.0 enp9s0: renamed from eth0

```
-Pook

---

