---
title: "[Latitude 5420] NIC I219-LM slow traffic issues (e1000e driver)"
date: 2021-04-08
forum: Networking &amp; Wireless
---

### Post by gforgas on 2021-04-08
Hello, 

I'm having issues with this new laptop from Dell and its NIC under Ubuntu and/or Debian. The traffic goes terribly slow, I have tried different cables in different networks and the result is always the same, approximately 1/10 of the speed is achieved and there are lots of RX and RX_CRC errors. I've tried different kernels, updating driver, different OS... always with the same result, the only time the NIC has worked as it should it was under Windows 10 (of course, Intel...). 

See below outputs from different tools for the NIC. 

```
$ ethtool -S enp0s31f6
NIC statistics:
     rx_packets: 29563
     tx_packets: 42223
     rx_bytes: 8077172
     tx_bytes: 52490426
     rx_broadcast: 5
     tx_broadcast: 13
     rx_multicast: 35
     tx_multicast: 192
     rx_errors: 266
     tx_errors: 0
     tx_dropped: 0
     multicast: 35
     collisions: 0
     rx_length_errors: 0
     rx_over_errors: 0
     rx_crc_errors: 133
     rx_frame_errors: 0
     rx_no_buffer_count: 0
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
     tx_window_errors: 0
     tx_abort_late_coll: 0
     tx_deferred_ok: 0
     tx_single_coll_ok: 0
     tx_multi_coll_ok: 0
     tx_timeout_count: 0
     tx_restart_queue: 0
     rx_long_length_errors: 0
     rx_short_length_errors: 0
     rx_align_errors: 0
     tx_tcp_seg_good: 13861
     tx_tcp_seg_failed: 0
     rx_flow_control_xon: 0
     rx_flow_control_xoff: 0
     tx_flow_control_xon: 0
     tx_flow_control_xoff: 0
     rx_csum_offload_good: 29504
     rx_csum_offload_errors: 0
     rx_header_split: 0
     alloc_rx_buff_failed: 0
     tx_smbus: 0
     rx_smbus: 0
     dropped_smbus: 0
     rx_dma_failed: 0
     tx_dma_failed: 0
     rx_hwtstamp_cleared: 0
     uncorr_ecc_errors: 0
     corr_ecc_errors: 0
     tx_hwtstamp_timeouts: 0
     tx_hwtstamp_skipped: 0

$ sudo ethtool -i enp0s31f6
driver: e1000e
version: 3.2.6-k
firmware-version: 0.8-4
expansion-rom-version: 
bus-info: 0000:00:1f.6
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: yes


$ sudo modinfo e1000e
filename:       /lib/modules/5.8.0-48-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        3.2.6-k
license:        GPL v2
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     5726DDD18033D5B33BE5693
alias:          pci:v00008086d00001A1Dsv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Csv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Esv*sd*bc*sc*i*
alias:          pci:v00008086d000015F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000015F4sv*sd*bc*sc*i*
alias:          pci:v00008086d000015FAsv*sd*bc*sc*i*
alias:          pci:v00008086d000015F9sv*sd*bc*sc*i*
alias:          pci:v00008086d000015FCsv*sd*bc*sc*i*
alias:          pci:v00008086d000015FBsv*sd*bc*sc*i*
alias:          pci:v00008086d00000D55sv*sd*bc*sc*i*
alias:          pci:v00008086d00000D53sv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Dsv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Csv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Esv*sd*bc*sc*i*
alias:          pci:v00008086d000015E2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015E1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015E0sv*sd*bc*sc*i*
alias:          pci:v00008086d000015DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BBsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BEsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000015D6sv*sd*bc*sc*i*
alias:          pci:v00008086d000015E3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015D8sv*sd*bc*sc*i*
alias:          pci:v00008086d000015D7sv*sd*bc*sc*i*
alias:          pci:v00008086d000015B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000015B8sv*sd*bc*sc*i*
alias:          pci:v00008086d000015B7sv*sd*bc*sc*i*
alias:          pci:v00008086d00001570sv*sd*bc*sc*i*
alias:          pci:v00008086d0000156Fsv*sd*bc*sc*i*
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        
retpoline:      Y
intree:         Y
name:           e1000e
vermagic:       5.8.0-48-generic SMP mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        7D:53:30:D0:18:D9:2D:B9:CC:E1:AB:FB:83:7F:05:5A:4E:74:37:7E
sig_hashalgo:   sha512
signature:      A6:19:87:EA:35:36:89:F8:DE:6E:BF:80:F9:36:89:5D:32:20:E3:87:
        F3:A3:DD:86:34:41:07:A7:B1:F0:6F:B2:5B:96:9F:93:BB:0B:5D:18:
        A5:DF:26:1D:82:BE:3A:D7:E1:8F:F0:A4:8E:72:39:E7:92:0E:D4:C0:
        C1:C9:13:82:BD:12:39:01:4D:60:CE:6D:90:2F:D1:77:A0:E3:D2:85:
        9B:88:B9:33:DC:00:ED:95:30:CE:DA:76:68:6B:E5:1F:B3:7F:DB:90:
        19:BA:E0:11:01:9D:68:7D:10:8E:35:4C:37:70:4C:1B:72:70:E5:91:
        3A:15:3C:21:6F:22:8A:8D:A9:D3:70:6F:53:4F:9D:46:5E:0D:0B:A1:
        09:2A:B7:CA:32:43:40:E5:FA:0C:19:30:CC:FC:40:75:0B:62:3E:A4:
        0F:3E:9B:69:97:DB:75:6E:A1:F1:1A:EC:73:1C:1C:19:36:82:10:9F:
        9F:FB:E3:22:8E:F8:59:AA:A5:CD:AF:4F:4A:2C:D9:58:4A:3A:8E:E8:
        6E:88:F9:42:20:6B:A7:A0:28:7A:A7:81:AA:11:03:0E:FA:C4:DA:5A:
        9D:3F:AA:1C:7F:7E:C3:25:62:CB:36:49:70:E3:A7:73:A1:29:E9:E7:
        62:97:F1:83:07:B2:A6:13:F3:4C:28:43:8C:C4:49:2C:72:92:1C:2D:
        50:DE:AF:DB:1D:47:52:EA:B6:FD:21:41:13:8F:26:46:EB:2B:29:C6:
        A0:40:4E:CF:95:B3:CB:B0:5B:9A:AF:8A:6F:15:F7:89:31:F6:C5:BE:
        C9:9D:44:73:11:28:3E:84:8F:57:57:97:B9:28:D3:97:4B:BE:D0:48:
        25:2F:29:71:89:EB:B0:AD:A5:FB:67:67:4F:2E:AF:D9:F6:64:CB:22:
        42:54:10:87:61:61:D8:40:1C:BC:FB:C2:56:91:3F:54:D5:84:11:0A:
        10:96:17:2B:4C:17:6F:32:CB:2F:EE:C8:DE:FB:32:2C:72:32:1A:27:
        69:19:62:F4:8F:73:4D:02:97:1E:00:94:5F:1F:F6:01:15:29:5A:B4:
        F8:51:A3:F3:D8:DB:DF:D1:FD:15:D3:61:C2:46:AC:50:75:4F:56:E0:
        26:D6:E1:9C:58:AA:28:5F:60:09:67:E1:F9:97:62:76:80:AB:1A:67:
        2F:9B:97:51:E4:6E:69:CA:F0:58:2F:45:D1:85:6A:05:0D:9B:C9:14:
        7F:2F:EE:44:64:A2:4C:BD:60:0F:1D:D7:39:21:F6:27:9C:A9:CF:5F:
        0E:5A:E6:B3:8D:E9:F5:EB:22:76:55:02:E6:02:D4:95:A0:E1:EE:D9:
        EB:4E:8F:91:4F:CA:2B:5D:01:D9:E3:94
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           WriteProtectNVM:Write-protect NVM [WARNING: disabling this can lead to corrupted NVM] (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)

$ lspci | grep -i ethernet
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (13) I219-LM (rev 20)

System:    Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.7 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Dell product: Latitude 5420 v: N/A serial: <filter> 
           Mobo: Dell model: 054CCV v: A00 serial: <filter> UEFI: Dell v: 1.4.9 date: 03/08/2021 
Battery:   ID-1: BAT0 charge: 62.4 Wh condition: 62.4/62.4 Wh (100%) model: SWD-ATL4.175 DELL 1K2CF13 status: Full 
Memory:    RAM: total: 15.37 GiB used: 1.44 GiB (9.4%) 
           RAM Report: permissions: Unable to run dmidecode. Root privileges required. 
CPU:       Topology: Quad Core model: 11th Gen Intel Core i7-1185G7 bits: 64 type: MT MCP arch: Tiger Lake rev: 1 
           L2 cache: 12.0 MiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 28876 
           Speed: 1699 MHz min/max: 400/4800 MHz Core speeds (MHz): 1: 1688 2: 1700 3: 1700 4: 1695 5: 1636 6: 1633 7: 1700 
           8: 1700 
Graphics:  Device-1: Intel vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel Xe Graphics (TGL GT2) v: 4.6 Mesa 20.2.6 direct render: Yes 
Audio:     Device-1: Intel vendor: Dell driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.8.0-48-generic 
Network:   Device-1: Intel driver: iwlwifi v: kernel port: 3000 bus ID: 00:14.3 
           IF: wlp0s20f3 state: up mac: <filter> 
           Device-2: Intel Ethernet I219-LM vendor: Dell driver: e1000e v: 3.2.6-k port: efa0 bus ID: 00:1f.6 
           IF: enp0s31f6 state: down mac: <filter> 
Drives:    Local Storage: total: 476.94 GiB used: 8.10 GiB (1.7%) 
           ID-1: /dev/nvme0n1 model: PC SN530 NVMe WDC 512GB size: 476.94 GiB 
Partition: ID-1: / size: 467.96 GiB used: 8.09 GiB (1.7%) fs: ext4 dev: /dev/nvme0n1p2 
           ID-2: /boot/efi size: 511.0 MiB used: 7.8 MiB (1.5%) fs: vfat dev: /dev/nvme0n1p1 
           ID-3: /snap/core18/1988 raw size: 55.5 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop0 
           ID-4: /snap/gnome-3-34-1804/66 raw size: 219.0 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop2 
           ID-5: /snap/gtk-common-themes/1514 raw size: 64.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop4 
           ID-6: /snap/snap-store/518 raw size: 51.0 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop3 
           ID-7: /snap/snapd/11036 raw size: 31.1 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop1 
Sensors:   System Temperatures: cpu: 33.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Repos:     Active apt repos in: /etc/apt/sources.list 
           1: deb http://be.archive.ubuntu.com/ubuntu/ focal main restricted
           2: deb http://be.archive.ubuntu.com/ubuntu/ focal-updates main restricted
           3: deb http://be.archive.ubuntu.com/ubuntu/ focal universe
           4: deb http://be.archive.ubuntu.com/ubuntu/ focal-updates universe
           5: deb http://be.archive.ubuntu.com/ubuntu/ focal multiverse
           6: deb http://be.archive.ubuntu.com/ubuntu/ focal-updates multiverse
           7: deb http://be.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
           8: deb http://security.ubuntu.com/ubuntu focal-security main restricted
           9: deb http://security.ubuntu.com/ubuntu focal-security universe
           10: deb http://security.ubuntu.com/ubuntu focal-security multiverse
Info:      Processes: 287 Uptime: 1h 27m Init: systemd runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 inxi: 3.0.38 
  *-network:0
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 20
       serial: f8:5e:a0:11:02:8d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-48-generic firmware=55.d9698065.0 QuZ-a0-hr-b0-55.u ip=192.168.131.129 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: iomemory:600-5ff irq:16 memory:605319c000-605319ffff
  *-network:1
       description: Ethernet interface
       product: Ethernet Connection (13) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 20
       serial: 74:78:27:82:0e:9f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:146 memory:a2300000-a231ffff

```

I have tried the 'ethtool tso off gso off' workaround suggested some months ago for these interfaces but it doesn't make any difference. ( [https://docs.hetzner.com/robot/dedicated-server/troubleshooting/performance-intel-i218-nic/](https://docs.hetzner.com/robot/dedicated-server/troubleshooting/performance-intel-i218-nic/) ).

---

