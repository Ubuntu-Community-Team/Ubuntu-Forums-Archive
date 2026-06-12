---
title: "ubuntu 14.04 LTS wifi"
date: 2016-02-08
forum: Networking &amp; Wireless
---

### Post by jakka_kiranraju on 2016-02-08
Hi  ):P,

     I am using HP laptop with i3 processor and dual OS(Win10 & ubuntu) inside. In windows 10 no problem with internet either wireless or wired, But where as in ubuntu(14.04 LTS) with wired no problem again but whenever i try to use wifi instead of wired after 3 to 5 min it will disconnected, sometimes immediate lost happens.

anyone has fix try to share...!

---

### Post by cariboo on 2016-02-08
We need a lot more information, such as make, model and chipset of your wireless device.

---

### Post by jakka_kiranraju on 2016-02-09
Thank you, for your interest on my probe.... Here is my wireless chip info
description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 00
       serial: ac:d1:b8:a1:44:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.19.0-49-generic firmware=N/A ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:b2500000-b2503fff



Regards.

---

### Post by Hadaka on 2016-02-09
Hi please post the output of,,
```
iwconfig wlan0 | grep -i --color signal
grep '' /sys/module/rtl8723be*/parameters/*
```
Then: go here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
run the wireless command and it will create a file in your home directory
named:**wireless-info.txt** copy and past that file here.
thanks

---

