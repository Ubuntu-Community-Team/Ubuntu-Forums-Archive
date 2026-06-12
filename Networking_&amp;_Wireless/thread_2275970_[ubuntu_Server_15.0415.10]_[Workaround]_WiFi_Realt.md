---
title: "[ubuntu Server 15.04/15.10] [Workaround] WiFi Realtek RTL8723AE Connection Issue"
date: 2015-04-29
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2015-04-29
Hello guys,

I've just installed **Ubuntu Server 15.04** on a MSI GE60 laptop with gnome. It works fine, except for **a weird shutdown freeze** ([**same as with Ubuntu desktop 14.10**]("http://ubuntuforums.org/showthread.php?t=2250017")) **worked around with the same trick (removing [COLOR=#000000]xserver-xorg-video-nouveau[/COLOR]) **and the **wireless network remains down** while the ethernet NIC can connect successfully to my router.

```
**lspci**00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
03:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
05:00.0 **Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter**


root@MSI-GE60-Ubuntu:/home/actionmystique#** lshw -C network**
  *-network               
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: p3p1
       version: 13
       serial: 8c:89:a5:0e:4e:89
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.160 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:33 memory:f7a00000-f7a3ffff ioport:d000(size=128)
  *-network
       description: Wireless interface
**       product: RTL8723AE PCIe Wireless Network Adapter**
**       vendor: Realtek Semiconductor Co., Ltd.**
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 24:0a:64:dd:b1:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723ae driverversion=3.19.0-15-generic firmware=N/A ip=192.168.43.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:c000(size=256) memory:f7800000-f7803fff

```

Any suggestion would be much appreciated.

One answer is [**here**]("http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized").

The compilation leads to an error:
```
root@MSI-GE60-Ubuntu:/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# makemake -C /lib/modules/3.19.0-15-generic/build M=/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-15-generic'
  CC [M]  /home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
In file included from /home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:39:0:
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/pci.h:245:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
 int __devinit rtl_pci_probe(struct pci_dev *pdev,
               ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:7: error: invalid preprocessing directive #IEEE80211_HW_BEACON_FILTER
  #    IEEE80211_HW_BEACON_FILTER |
       ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:351:4: error: ‘struct ieee80211_hw’ has no member named ‘channel_change_time’
  hw->channel_change_time = 100;
    ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_action_proc’:
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:867:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:868:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.band = hw->conf.channel->band;
                                ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:870:25: error: ‘RX_FLAG_MACTIME_MPDU’ undeclared (first use in this function)
       rx_status.flag |= RX_FLAG_MACTIME_MPDU;
                         ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:870:25: note: each undeclared identifier is reported only once for each function it appears in
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_beacon_statistic’:
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1141:2: error: implicit declaration of function ‘compare_ether_addr’ [-Werror=implicit-function-declaration]
  if (compare_ether_addr(hdr->addr3, rtlpriv->mac80211.bssid))
  ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_send_smps_action’:
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1432:16: error: ‘struct <anonymous>’ has no member named ‘sta’
   info->control.sta = sta;
                ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1433:24: error: ‘struct ieee80211_conf’ has no member named ‘channel’
   info->band = hw->conf.channel->band;
                        ^
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_store_debug_level’:
/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1657:2: error: implicit declaration of function ‘strict_strtoul’ [-Werror=implicit-function-declaration]
  ret = strict_strtoul(buf, 0, &val);
  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o' failed
make[2]: *** [/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
Makefile:1394: recipe for target '_module_/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012' failed
make[1]: *** [_module_/home/actionmystique/Program-Files/Ubuntu/Drivers/Realtek/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-15-generic'
Makefile:27: recipe for target 'all' failed
make: *** [all] Error 2



```

The real solution is [**here**]("https://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/"): big thanks to **Zach Adams** :)

---

### Post by actionmystique on 2015-05-01
Unfortunately, the WiFi connection must be manually started at each system restart.
The automatic connection is unstable.

---

### Post by actionmystique on 2015-05-09
I **removed** the entry "**auto p3p1**" (it may be "**auto eth0**" on your system) in **/etc/network/interfaces** and now the **WiFi interface comes up automatically**.

---

### Post by actionmystique on 2015-10-28
I have discovered that this issue does not happen with Ubuntu **Desktop** 15.04/15.10, only with **Server on my system.**

---

