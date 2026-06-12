---
title: "Wireless Networking Disabled"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by JKobyP on 2013-12-09
Sometimes, all of a sudden my wireless will stop working. It requires a system reboot to get going again. I've checked out this thread: [http://ubuntuforums.org/showthread.php?t=1490833](http://ubuntuforums.org/showthread.php?t=1490833) and looked at the results of some commands but they mean nothing to me. I'm running Ubuntu 13.10 on a Thinkpad Edge 531.
Here are some commands i've run:

```

lshw:
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: c4
       serial: 68:17:29:49:b3:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-14-generic 
firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 memory:f2500000-f2501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: 28:d2:44:15:35:d7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet 
physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 
driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 
link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1404000-f1404fff 
memory:f1400000-f1403fff

```
```

iwconfig:
wlan0 IEEE 802.11bgn ESSID:off/any
          Mode:Managed Access Point: Not-Associated Tx-Power=16 dBm
          Retry long limit:7 RTS thr:off Fragment thr:off
          Power Management:on

```
```

dmesg:
[ 3653.619689] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3653.807007] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3653.882146] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3653.957221] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.032239] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.107248] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.182250] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.257261] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.332317] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.407335] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.482319] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.557301] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.632275] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.707251] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.782231] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.857218] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3654.932350] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3655.007431] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3655.082430] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3655.157437] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3655.232423] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3671.552985] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3671.628089] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3671.703184] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3671.778274] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3671.853359] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3671.928462] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.003551] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.078636] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.153720] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.228813] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.303894] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.378977] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.454057] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.529143] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.604236] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.679331] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.754413] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.829500] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.904718] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm] [ 
3672.979891] [<ffffffffa09796c0>] iwlagn_mac_flush+0xa0/0x1a0 [iwldvm]

```

I tried to run sudo ifconfig wlan0 up but the connection timed out.

---

### Post by codenine75a on 2013-12-09
Did your laptop have vPro on it?  It may have been remotely disabled through Intel's vPro or maybe your internal nic is damaged.

---

### Post by JKobyP on 2013-12-10
If my laptop has vpro, i'm not aware of it. I don't think my hardware is damaged because as far as I know, this doesn't happen in my windows partition.

It'll be fine one moment, and then all of a sudden it will stop working until the laptop is restarted. If I click on the icon it says 'device not ready'. There's a wifi toggle on my f8 that doesn't make a difference when I push it.

---

