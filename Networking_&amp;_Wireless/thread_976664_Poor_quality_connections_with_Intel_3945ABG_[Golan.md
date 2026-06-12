---
title: "Poor quality connections with Intel 3945ABG [Golan] wireless"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by jsmmster on 2008-11-09
Hi. I'm having a rather poor quality network wireless connection in my Thinkpad X60s with Ubuntu 8.10 Intrepid. I copy some info, in case you are able to help. Thanks,

**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Tele2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:03:6F:4E:1A:9C   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=92/100  Signal level:-38 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

**$ dmesg | grep -i iwl**
[   16.048177] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   16.048182] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   16.048295] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.048311] iwl3945 0000:03:00.0: setting latency timer to 64
[   16.048334] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   16.233693] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.263672] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.804930] iwl3945 0000:03:00.0: PCI INT A disabled
[   44.653476] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   44.653626] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   44.653953] firmware: requesting iwlwifi-3945-1.ucode
[   44.783519] Registered led device: iwl-phy0:radio
[   44.783574] Registered led device: iwl-phy0:assoc
[   44.783609] Registered led device: iwl-phy0:RX
[   44.783642] Registered led device: iwl-phy0:TX

**$ lshw -C Network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:29:dc:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:4c:1f:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.193 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:e3:fc:90:ff:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**$ modprobe -l "iwl*"**
/lib/modules/2.6.27-7-generic/updates/iwlcore.ko
/lib/modules/2.6.27-7-generic/updates/iwlagn.ko
/lib/modules/2.6.27-7-generic/updates/iwl3945.ko

**$ dmesg | grep -i iwl**
[   16.048177] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   16.048182] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   16.048295] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.048311] iwl3945 0000:03:00.0: setting latency timer to 64
[   16.048334] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   16.233693] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.263672] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.804930] iwl3945 0000:03:00.0: PCI INT A disabled
[   44.653476] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   44.653626] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   44.653953] firmware: requesting iwlwifi-3945-1.ucode
[   44.783519] Registered led device: iwl-phy0:radio
[   44.783574] Registered led device: iwl-phy0:assoc
[   44.783609] Registered led device: iwl-phy0:RX
[   44.783642] Registered led device: iwl-phy0:TX

---

