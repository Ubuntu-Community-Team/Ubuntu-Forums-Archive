---
title: "Ubuntu 13.10 - RTL8101E/RTL8102E PCI Express Fast Ethernet does not work"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by Gujume3333 on 2013-10-21
I upgraded from my machine from 13.04 to 13.10 I use to be able to download the latest driver from Realtek: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3) and install them. Now when I try to install them it fails with errors I haven't seen before.


```
sudo sh ./autorun.sh 
```

Check old driver and unload it.
Build the module and install
/home/np/Important/r8101-1.024.00/src/r8101_n.c: In function ‘rtl8101_rx_vlan_skb’:
/home/np/Important/r8101-1.024.00/src/r8101_n.c:1909:9: error: too few arguments to function ‘__vlan_hwaccel_put_tag’
         __vlan_hwaccel_put_tag(skb, swab16(opts2 & 0xffff));
         ^
In file included from /home/npatel/Important/r8101-1.024.00/src/r8101_n.c:46:0:
include/linux/if_vlan.h:236:31: note: declared here
 static inline struct sk_buff *__vlan_hwaccel_put_tag(struct sk_buff *skb,
                               ^
/home/np/Important/r8101-1.024.00/src/r8101_n.c: In function ‘rtl8101_hw_set_features’:
/home/np/Important/r8101-1.024.00/src/r8101_n.c:1970:25: error: ‘NETIF_F_HW_VLAN_RX’ undeclared (first use in this function)
     if (dev->features & NETIF_F_HW_VLAN_RX)
                         ^
/home/np/Important/r8101-1.024.00/src/r8101_n.c:1970:25: note: each undeclared identifier is reported only once for each function it appears in
/home/np/Important/r8101-1.024.00/src/r8101_n.c: In function ‘rtl8101_init_one’:
/home/np/Important/r8101-1.024.00/src/r8101_n.c:7295:22: error: ‘NETIF_F_HW_VLAN_TX’ undeclared (first use in this function)
     dev->features |= NETIF_F_HW_VLAN_TX | NETIF_F_HW_VLAN_RX;
                      ^
/home/np/Important/r8101-1.024.00/src/r8101_n.c:7295:43: error: ‘NETIF_F_HW_VLAN_RX’ undeclared (first use in this function)
     dev->features |= NETIF_F_HW_VLAN_TX | NETIF_F_HW_VLAN_RX;
                                           ^
make[3]: *** [/home/np/Important/r8101-1.024.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/np/Important/r8101-1.024.00/src] Error 2
make[1]: *** [modules] Error


I can provide more details if necessary but I need instructions on what details you need and how to grab them.

```
lspci
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```
uname -a
```
Linux nemo-laptop 3.11.1-031101-generic #201309141102 SMP Sat Sep 14 15:02:49 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Gujume3333 on 2013-10-22
After looking at this patch: [http://code.google.com/p/r8168/issues/attachmentText?id=13&aid=130003000&name=r8168-8.036.00-kernel-3.10.10.patch&token=YbfjJVIwbQiRiYICyJcfiHSflbM%3A1382466224505](http://code.google.com/p/r8168/issues/attachmentText?id=13&aid=130003000&name=r8168-8.036.00-kernel-3.10.10.patch&token=YbfjJVIwbQiRiYICyJcfiHSflbM%3A1382466224505)

from this issue: [http://code.google.com/p/r8168/issues/detail?id=13](http://code.google.com/p/r8168/issues/detail?id=13), I was able to identify the changes and get the realtek driver installed. I created a patch for the r8101_n.c file in the src directory that needs to be updated for the driver to compile. The patch should work for anyone running kernel 3.10 or newer. *I am not an expert so use at your own risk*

RealTek Driver: r8101-1.024.00 for Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) from: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I am using Dell Inspiron 17R. 

I wasn't able to attach a patch so I created a gist for it here: [https://gist.github.com/NeMO84/7106119](https://gist.github.com/NeMO84/7106119)

---

### Post by Lars_Blumberg on 2014-02-22
Thank you, your patch worked for me, too. System: HP 3200 Ubuntu 13.10, Realtek 8101E

---

### Post by vinoth4 on 2014-03-01
How to apply this patch?.

---

