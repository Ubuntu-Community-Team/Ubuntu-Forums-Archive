---
title: "WiFi not working on Ubuntu 15.04"
date: 2015-06-03
forum: Networking &amp; Wireless
---

### Post by polaris90 on 2015-06-03
I cannot connect to my WiFi router. The network appears at the top but once I try to connect to it, it tries to connect but it doesn't finish. I am using Ubuntu 15.04 gnome. I tried the Unity version but got the same problem. I tried connecting to my phone hotspot but still nothing. I looked around and found threads with people having the same kind of problem but I couldn't find a solution.

These are the outputs that I got from my terminal

```

lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev cb)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8170]
    Kernel driver in use: iwlwifi
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Toshiba America Info Systems Device [1179:f900]
    Kernel driver in use: r8169



```

```

iwconfig 
eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

```

lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev cb)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Unassigned class [ff00]: Device 1aea:6601

```

```

sudo lshw -C network  
*-network 
description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: cb
       serial: d0:7e:35:e7:d9:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-15-generic firmware=25.15.12.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:53 memory:c1300000-c1301fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: 00:71:c2:33:9f:2d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:3000(size=256) memory:c1200000-c1200fff memory:c1000000-c1003fff

```


update:
I tried loading ubuntu 14.04 LTS and the WiFi seems to be working properly. Any ideas on what could be the issue?

---

### Post by simonn on 2015-06-10
I just purchased an HP Stream 11, immediately installed Xubuntu 15.04 on it and came across the same problem... well actually I installed it after failing to do a network debian installation because of this problem :).

It looks as if the newest two firmware versions are a bit broken.

Move iwlwifi-3160-10.ucode and iwlwifi-3160-12.ucode out of /lib/firmware and reload the driver (or reboot), e.g.

```

$ sudo mv /lib/firware/iwlwifi-3160-1{0,2}.ucode /root
$ sudo rmmod iwlmvm
$ sudo rmmod iwlwifi
$ sudo modprobe iwlwifi

```

This will force the driver to use the older, but apparently working/less broken (at least for me) iwlwifi-3160-9.ucode.

Some related notes:

A lot of posts on the web suggest using the iwlwifi module option 11n_disable. Setting 11n_disable=1 allowed me to connect, but only at 802.11g speeds (3MB/s, as opposed to 27MB/s for 802.11ac and 6MB/s for 802.11n from my router). The other possible values for 11n_disable (2,4 & 8) had no apparent effect.

If you are getting slow speeds, check /etc/modprobe.d/iwlwifi.conf for lines that include 11n_disable and try setting 11m_disable=0.

Anther thing to check on routers you own/have admin rights to is a parameter like "b/g protection". Unchecking this on my router increased the speed of 802.11n connections from 3MB/s to 6MB/s. This may affect 802.11b and 802.11g devices/connections though.

---

