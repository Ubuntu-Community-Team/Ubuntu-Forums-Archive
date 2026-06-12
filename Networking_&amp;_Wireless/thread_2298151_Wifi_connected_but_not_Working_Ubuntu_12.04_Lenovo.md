---
title: "Wifi connected but not Working Ubuntu 12.04 Lenovo L440"
date: 2015-10-09
forum: Networking &amp; Wireless
---

### Post by amantrehan06 on 2015-10-09
Hi Guys,

I have a dual boot windows 7 and Ubuntu 12.04 machine.

Wifi works perfectly on windows but on Ubuntu sometimes it connects and sometimes not, and Internet does not work even if it is connected.
I followed many thread and did dome random modprobe commands to load realtek driver and now i am confused what has happened and how to fix this issue.
Please guide me to check if valid Driver is loaded, If not then how to install the compatible driver.

lspci 

```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 818b
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5227 (rev 01)



```

---

### Post by michi1983 on 2015-10-09
Hey,

doesn't look good to be honest:
[http://askubuntu.com/questions/376732/thinkpad-t440p-wireless-network-controller](http://askubuntu.com/questions/376732/thinkpad-t440p-wireless-network-controller)

You can put your Device 818b in the search box on the top right corner of the forum and you will find some similar threads.

Best advise is to get a USB dongle.

---

### Post by amantrehan06 on 2015-10-09
Please have more details of the Driver currently being used 

# sudo lshw -C network


  *-network               
      
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: d8:5d:e2:24:b3:79
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**rtl8192ee** driverversion=3.8.0-44-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 ioport:5000(size=256) memory:f2400000-f2403fff

 lspci -nnk | grep -A2 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:818b]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]
	Kernel driver in use: **rtl8192ee**

---

