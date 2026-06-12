---
title: "Broadcom 14e4:4727 (rev 01) fades in/out in hotspots"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2013-11-16
I recently installed kubuntu 13.10 on my netbook.  From what I've read I was under the impression that the open source driver (brcmsmac) for the BCM 4313/4727 works properly now.

Apparently that isn't true.  When I'm connected to wifi hotspots ... which is generally what I use this machine for ... it's constantly cutting in and out.

The firewall is disabled because ufw isn't working properly in 13.10 either.  That worked fine in 12.04.

I had far worse problems with the wireless in 12.04, and installing bcmwl-kernel-source in 13.04 worked, but apparently that's broken in 13.10 so I haven't installed it.

To be quite honest I'm starting to believe 13.10 is broken, period.

Anyway, here's some info:

```
lspci -nnk | grep -iA2 net
```

```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Acer Incorporated [ALI] Device [1025:061f]
        Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
        Subsystem: Foxconn International, Inc. Device [105b:e042]
        Kernel driver in use: bcma-pci-bridge
```

```
sudo lshw -C network
```

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 04:7d:7b:50:97:53
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:40004000-40004fff memory:40000000-40003fff
  *-network
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:44000000-44003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:18:85:0e:f5:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.11.0-13-generic firmware=610.812 ip=192.168.65.138 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by Rob Sayer on 2013-11-18
No replies here ... I can't find anything that indicates that brcmsmac isn't the correct driver ... 

Maybe it isn't installed correctly?  This may help ...

```
~$ lsmod | grep brcm
```

gives me:

```
brcmsmac              529624  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              513247  2 b43,brcmsmac
cfg80211              401436  3 b43,brcmsmac,mac80211
bcma                   40966  3 b43,brcmsmac
```

I am getting very sick of fiddling with this netbook at this point.  Any ideas?

---

### Post by Rob Sayer on 2013-11-18
Here's a bit more ... from some searching on the fedora forum I'm wondering if this card even supports all modes ...

```
iw list
```

```
rob@d270:~$ iw list Wiphy phy0         Band 1:                 Capabilities: 0x70                         HT20                         Static SM Power Save                         RX Greenfield                         RX HT20 SGI                         RX HT40 SGI                         No RX STBC                         Max AMSDU length: 3839 bytes                         No DSSS/CCK HT40                 Maximum RX AMPDU length 65535 bytes (exponent: 0x003)                 Minimum RX AMPDU time spacing: 8 usec (0x06)                 HT TX/RX MCS rate indexes supported: 0-7                 Frequencies:                         * 2412 MHz [1] (19.0 dBm)                         * 2417 MHz [2] (19.0 dBm)                         * 2422 MHz [3] (19.0 dBm)                         * 2427 MHz [4] (19.0 dBm)                         * 2432 MHz [5] (19.0 dBm)                         * 2437 MHz [6] (19.0 dBm)                         * 2442 MHz [7] (19.0 dBm)                         * 2447 MHz [8] (19.0 dBm)                         * 2452 MHz [9] (19.0 dBm)                         * 2457 MHz [10] (19.0 dBm)                         * 2462 MHz [11] (19.0 dBm)                         * 2467 MHz [12] (19.0 dBm) (passive scanning, no IBSS)                         * 2472 MHz [13] (19.0 dBm) (passive scanning, no IBSS)                         * 2484 MHz [14] (disabled)                 Bitrates (non-HT):                         * 1.0 Mbps                         * 2.0 Mbps (short preamble supported)                         * 5.5 Mbps (short preamble supported)                         * 11.0 Mbps (short preamble supported)                         * 6.0 Mbps                         * 9.0 Mbps                         * 12.0 Mbps                         * 18.0 Mbps                         * 24.0 Mbps                         * 36.0 Mbps                         * 48.0 Mbps                         * 54.0 Mbps         max # scan SSIDs: 4         max scan IEs length: 2257 bytes         Coverage class: 0 (up to 0m)         Supported Ciphers:                 * WEP40 (00-0f-ac:1)                 * WEP104 (00-0f-ac:5)                 * TKIP (00-0f-ac:2)                 * CCMP (00-0f-ac:4)         Available Antennas: TX 0 RX 0         Supported interface modes:                  * IBSS                  * managed                  * AP                  * AP/VLAN                  * monitor         software interface modes (can always be added):                  * AP/VLAN                  * monitor         interface combinations are not supported         Supported commands:                  * new_interface                  * set_interface                  * new_key                  * new_beacon                  * new_station                  * new_mpath                  * set_mesh_params                  * set_bss                  * authenticate                  * associate                  * deauthenticate                  * disassociate                  * join_ibss                  * join_mesh                  * set_tx_bitrate_mask                  * action                  * frame_wait_cancel                  * set_wiphy_netns                  * set_channel                  * set_wds_peer                  * Unknown command (84)                  * Unknown command (87)                  * Unknown command (85)                  * Unknown command (89)                  * Unknown command (92)                  * testmode                  * connect                  * disconnect         Supported TX frame types:                  * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0                  * Unknown mode (10): 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0         Supported RX frame types:                  * IBSS: 0x40 0xb0 0xc0 0xd0                  * managed: 0x40 0xd0                  * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0                  * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0                  * mesh point: 0xb0 0xc0 0xd0                  * P2P-client: 0x40 0xd0                  * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0                  * Unknown mode (10): 0x40 0xd0         Device supports RSN-IBSS.         HT Capability overrides:                  * MCS: ff ff ff ff ff ff ff ff ff ff                  * maximum A-MSDU length                  * supported channel width                  * short GI for 40 MHz                  * max A-MPDU length exponent                  * min MPDU start spacing         Device supports TX status socket option.         Device supports HT-IBSS. rob@d270:~$  

```

---

### Post by Rob Sayer on 2013-11-19
Nothing?

---

