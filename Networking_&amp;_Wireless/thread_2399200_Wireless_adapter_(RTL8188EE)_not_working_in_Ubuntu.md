---
title: "Wireless adapter (RTL8188EE) not working in Ubuntu 16.04 after recent software update"
date: 2018-08-22
forum: Networking &amp; Wireless
---

### Post by rhat2 on 2018-08-22
Here is my iwconfig output:
lo        no wireless extensions.

eno1      no wireless extensions.

Here are the network interfaces that I have (from lspci -knn | grep Net -A2):
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c821]
    DeviceName: Realtek RTL8188EE 802.11bgn Wi-Fi Adapter
    Subsystem: Hewlett-Packard Company Device [103c:831a]

Here is lshw -C Network output:
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:b1100000-b110ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eno1
       version: 15
       serial: b4:b6:86:dd:06:37
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.144.31.152 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:3000(size=256) memory:b1004000-b1004fff memory:b1000000-b1003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

I have the wl module from this output:
lsmod | grep wl
wl                   6447104  0
cfg80211              622592  1 wl

I had tried to install the rtl8188ee driver from git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git).  But it didn't work.  When I loaded the rtl8188ee module, it wasn't registering to a device.

My WiFi works when I boot up my Windows partition.  Before my Ubuntu 16.04 software update, I was able to get WiFi to work by following the instructions in this link: [https://askubuntu.com/questions/868075/how-to-get-intel-dual-band-wireless-ac-3168-work-on-ubuntu-16-04](https://askubuntu.com/questions/868075/how-to-get-intel-dual-band-wireless-ac-3168-work-on-ubuntu-16-04).  But when I try doing it now, it doesn't work.

I have attached my wireless-info.txt.  I would really appreciate it if someone could help me out with this.

---

### Post by rhat2 on 2018-08-22
The issue was with the software update to Linux kernel linux-headers-4.15.0-32-generic.  After downgrading to linux-headers-4.15.0-30-generic, the WiFi worked.

---

