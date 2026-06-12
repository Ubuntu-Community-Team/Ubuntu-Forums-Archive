---
title: "You can turn your Ubuntu computer into a WiFi HotSpot.  I can't get it to work."
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2016-01-13
Ubuntu 15.10 X64
All updates applied as of Wednesday Jan 13, 2016.
System76 Wild Dog Pro bought in early December 2015 with Intel wireless option.

I tried the howto here, the one with the pictures.  It failed.  It looks like it's starting up, animated WiFi icon, but then stops and goes back to Ethernet icon.  Verizon Samsung Galaxy S6 Edge does not see any HotSpot.
[http://askubuntu.com/questions/490950/create-wifi-hotspot-on-ubuntu](http://askubuntu.com/questions/490950/create-wifi-hotspot-on-ubuntu)

Outputs of iw list and lshw.

```
nate@frontier:~$ iw list
Wiphy phy0
    max # scan SSIDs: 20
    max scan IEs length: 425 bytes
    Retry short limit: 7
    Retry long limit: 4
    Coverage class: 0 (up to 0m)
    Device supports RSN-IBSS.
    Device supports AP-side u-APSD.
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
        * CMAC (00-0f-ac:6)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * P2P-client
         * P2P-GO
         * P2P-device
    Band 1:
        Capabilities: 0x11e2
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT TX/RX MCS rate indexes supported: 0-15
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 2412 MHz [1] (22.0 dBm)
            * 2417 MHz [2] (22.0 dBm)
            * 2422 MHz [3] (22.0 dBm)
            * 2427 MHz [4] (22.0 dBm)
            * 2432 MHz [5] (22.0 dBm)
            * 2437 MHz [6] (22.0 dBm)
            * 2442 MHz [7] (22.0 dBm)
            * 2447 MHz [8] (22.0 dBm)
            * 2452 MHz [9] (22.0 dBm)
            * 2457 MHz [10] (22.0 dBm)
            * 2462 MHz [11] (22.0 dBm)
            * 2467 MHz [12] (22.0 dBm) (no IR)
            * 2472 MHz [13] (22.0 dBm) (no IR)
    Band 2:
        Capabilities: 0x11e2
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT TX/RX MCS rate indexes supported: 0-15
        VHT Capabilities (0x038071a0):
            Max MPDU length: 3895
            Supported Channel Width: neither 160 nor 80+80
            short GI (80 MHz)
            TX STBC
            SU Beamformee
        VHT RX MCS set:
            1 streams: MCS 0-9
            2 streams: MCS 0-9
            3 streams: not supported
            4 streams: not supported
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT RX highest supported: 0 Mbps
        VHT TX MCS set:
            1 streams: MCS 0-9
            2 streams: MCS 0-9
            3 streams: not supported
            4 streams: not supported
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT TX highest supported: 0 Mbps
        Bitrates (non-HT):
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 5180 MHz [36] (22.0 dBm) (no IR)
            * 5200 MHz [40] (22.0 dBm) (no IR)
            * 5220 MHz [44] (22.0 dBm) (no IR)
            * 5240 MHz [48] (22.0 dBm) (no IR)
            * 5260 MHz [52] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5280 MHz [56] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5300 MHz [60] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5320 MHz [64] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5720 MHz [144] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 188924 sec)
              DFS CAC time: 0 ms
            * 5745 MHz [149] (22.0 dBm) (no IR)
            * 5765 MHz [153] (22.0 dBm) (no IR)
            * 5785 MHz [157] (22.0 dBm) (no IR)
            * 5805 MHz [161] (22.0 dBm) (no IR)
            * 5825 MHz [165] (22.0 dBm) (no IR)
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * start_ap
         * new_station
         * new_mpath
         * set_mesh_config
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * remain_on_channel
         * set_tx_bitrate_mask
         * frame
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * start_sched_scan
         * probe_client
         * set_noack_map
         * register_beacons
         * start_p2p_device
         * set_mcast_rate
         * channel_switch
         * Unknown command (104)
         * Unknown command (105)
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-device: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
    Supported RX frame types:
         * IBSS: 0x40 0xb0 0xc0 0xd0
         * managed: 0x40 0xd0
         * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * mesh point: 0xb0 0xc0 0xd0
         * P2P-client: 0x40 0xd0
         * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * P2P-device: 0x40 0xd0
    WoWLAN support:
         * wake up on disconnect
         * wake up on magic packet
         * wake up on pattern match, up to 20 patterns of 16-128 bytes,
           maximum packet offset 0 bytes
         * can do GTK rekeying
         * wake up on GTK rekey failure
         * wake up on EAP identity request
         * wake up on 4-way handshake
         * wake up on rfkill release
         * wake up on TCP connection
    software interface modes (can always be added):
         * AP/VLAN
         * monitor
    valid interface combinations:
         * #{ managed } <= 1, #{ AP, P2P-client, P2P-GO } <= 1, #{ P2P-device } <= 1,
           total <= 3, #channels <= 2
    HT Capability overrides:
         * MCS: ff ff ff ff ff ff ff ff ff ff
         * maximum A-MSDU length
         * supported channel width
         * short GI for 40 MHz
         * max A-MPDU length exponent
         * min MPDU start spacing
    Device supports TX status socket option.
    Device supports HT-IBSS.
    Device supports SAE with AUTHENTICATE command
    Device supports low priority scan.
    Device supports scan flush.
    Device supports per-vif TX power setting
    P2P GO supports CT window setting
    P2P GO supports opportunistic powersave setting
    Driver supports a userspace MPM
    Device supports static SMPS
    Device supports dynamic SMPS
```

```
frontier
    description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3528MHz
          capacity: 3600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch ida arat pln pts dtherm hwp hwp_noitfy hwp_act_window hwp_epp intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 cpufreq
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Sky Lake Integrated Graphics
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:137 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)
        *-usb
             description: USB controller
             product: Sunrise Point-H USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:133 memory:df230000-df23ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.2.0-23-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
              *-usb
                   description: Mass storage device
                   product: USB3.0 Card Reader
                   vendor: Realtek
                   physical id: 1
                   bus info: usb@2:1
                   logical name: scsi6
                   version: 1.27
                   serial: 201006010301
                   capabilities: usb-3.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=800mA speed=5000Mbit/s
                 *-disk:0
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdb
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:1
                      description: SCSI Disk
                      physical id: 0.0.1
                      bus info: scsi@6:0.0.1
                      logical name: /dev/sdc
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:2
                      description: SCSI Disk
                      physical id: 0.0.2
                      bus info: scsi@6:0.0.2
                      logical name: /dev/sdd
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:3
                      description: SCSI Disk
                      product: USB3.0 CRW-MS
                      vendor: Generic-
                      physical id: 0.0.3
                      bus info: scsi@6:0.0.3
                      logical name: /dev/sde
                      version: 1.00
                      capabilities: removable
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sde
                 *-disk:4
                      description: SCSI Disk
                      physical id: 0.0.4
                      bus info: scsi@6:0.0.4
                      logical name: /dev/sdf
                      configuration: logicalsectorsize=512 sectorsize=512
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.2.0-23-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Ext HDD 1021
                   vendor: Western Digital
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi7
                   version: 20.21
                   serial: 5743415A4135323434303537
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Ext HDD 1021
                      vendor: WD
                      physical id: 0.0.0
                      bus info: scsi@7:0.0.0
                      logical name: /dev/sdg
                      version: 2021
                      serial: WCAZA5244057
                      size: 1863GiB (2TB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512 signature=000a51ae
                    *-volume
                         description: Windows NTFS volume
                         physical id: 1
                         bus info: scsi@7:0.0.0,1
                         logical name: /dev/sdg1
                         logical name: /media/nate/NATE-BACKUP
                         version: 3.1
                         serial: 5e3e10d5-7484-3b47-b9a5-a972daaf6b8e
                         size: 1863GiB
                         capacity: 1863GiB
                         capabilities: primary ntfs initialized
                         configuration: clustersize=4096 created=2013-03-13 13:58:59 filesystem=ntfs label=NATE-BACKUP mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-usb:1
                   description: Video
                   product: Webcam Pro 9000
                   vendor: Logitech, Inc.
                   physical id: 6
                   bus info: usb@1:6
                   version: 0.10
                   serial: 262A0E61
                   capabilities: usb-2.00
                   configuration: driver=snd-usb-audio maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 7
                   bus info: usb@1:7
                   version: 12.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:3
                   description: Audio device
                   product: AK5370
                   vendor: AKM
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.01
                   capabilities: usb-1.10 audio-control
                   configuration: driver=snd-usb-audio maxpower=90mA speed=12Mbit/s
              *-usb:4
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 9
                   bus info: usb@1:9
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:5
                   description: Human interface device
                   product: Back-UPS RS 1500 FW:8.g8 .D USB FW:g8
                   vendor: American Power Conversion
                   physical id: d
                   bus info: usb@1:d
                   version: 1.06
                   serial: JB0336019769
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=24mA speed=2Mbit/s
        *-generic UNCLAIMED
             description: Signal processing controller
             product: Sunrise Point-H Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:df24e000-df24efff
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:138 memory:df24d000-df24dfff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:135 memory:df248000-df249fff memory:df24c000-df24c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:df24b000-df24b7ff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-H PCI Root Port #19
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:2000(size=8192) memory:df100000-df1fffff ioport:8d000000(size=4194304)
           *-pci
                description: PCI bridge
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:128 ioport:2000(size=8192) memory:df100000-df1fffff ioport:8d000000(size=4194304)
              *-pci:0
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:02:00.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:129
              *-pci:1
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 1
                   bus info: pci@0000:02:01.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:130 ioport:2000(size=4096) ioport:8d000000(size=2097152)
              *-pci:2
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 2
                   bus info: pci@0000:02:02.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:131 memory:df100000-df1fffff
                 *-usb
                      description: USB controller
                      product: Intel Corporation
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:05:00.0
                      version: 00
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress xhci bus_master cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:134 memory:df100000-df10ffff
                    *-usbhost:0
                         product: xHCI Host Controller
                         vendor: Linux 4.2.0-23-generic xhci-hcd
                         physical id: 0
                         bus info: usb@4
                         logical name: usb4
                         version: 4.02
                         capabilities: usb-3.00
                         configuration: driver=hub slots=2 speed=5000Mbit/s
                    *-usbhost:1
                         product: xHCI Host Controller
                         vendor: Linux 4.2.0-23-generic xhci-hcd
                         physical id: 1
                         bus info: usb@3
                         logical name: usb3
                         version: 4.02
                         capabilities: usb-2.00
                         configuration: driver=hub slots=2 speed=480Mbit/s
              *-pci:3
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 4
                   bus info: pci@0000:02:04.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:132 ioport:3000(size=4096) ioport:8d200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 ioport:4000(size=4096) memory:8d400000-8d5fffff ioport:8d600000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 memory:df000000-df0fffff
           *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: wlp10s0
                version: 73
                serial: 7c:5c:f8:19:fb:e0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-23-generic firmware=25.30.13.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:139 memory:df000000-df001fff
        *-pci:4
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:126
        *-pci:5
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #13
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:127
        *-isa
             description: ISA bridge
             product: Sunrise Point-H LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-H PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:df244000-df247fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-H HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:140 memory:df240000-df243fff memory:df220000-df22ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-H SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df24a000-df24a0ff ioport:f040(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 31
             serial: 40:8d:5c:57:b1:71
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=0.8-4 ip=98.127.57.218 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:136 memory:df200000-df21ffff
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1B6Q
             serial: S24ANXAG703415L
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=d483f985-252e-471c-a445-91d9ffbf841f logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: BIOS Boot partition
                vendor: EFI
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                serial: 2b16c561-69f5-4fad-b4c4-29a455a86f73
                capacity: 1023KiB
                capabilities: nofs
                configuration: name=primary
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: ddc1c8f3-8bfa-4284-830b-89bd0ade9a64
                size: 107GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-12-01 15:51:42 filesystem=ext4 label=Ubuntu lastmountpoint=/ modified=2016-01-11 09:26:13 mount.fstype=ext4 mount.options=rw,noatime,errors=remount-ro,data=ordered mounted=2016-01-11 09:26:14 name=primary state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: e35c0a0b-8673-4a75-bbc0-e77e0a23f2db
                size: 4095MiB
                capacity: 4095MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap name=primary pagesize=4095
     *-scsi:1
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: iHAS124   F
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: CL07
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by MechaMechanism on 2016-01-15
Bump.  Does the HotSpot mode even work out of the box for anybody.

---

### Post by sammiev on 2016-01-15
Hi,

I connected to the internet with my wired connection and then turn on my wireless and select Wi-Fi settings, turn on HotSpot and enjoy.

Turned on my Tablet and set it to connect to my HotSpot and it's now updating from over the HotSpot connection.

Never needed to add any other software or anything.

---

### Post by ian-weisser on 2016-01-15
> **MechaMechanism said:**
> Does the HotSpot mode even work out of the box for anybody.
Yes, works great.

---

### Post by Edward_Fish on 2016-01-15
It took a little trial and error for me, to get it working, but I figured it out:
- Open Settings > Network
- Use as Hotspot...
- If you get a popup, pick Turn On

And you did it! You can see the network name, security type and password from this screen.

---

### Post by MechaMechanism on 2016-01-17
> **ian-weisser said:**
> Yes, works great.Ok.  I see in Settings/Network/Wireless it shows as working.  But My Verizon Samsung Galaxy S6 Edge does not see the network.  I got Internet now and a wireless router so I guess I won't debug it any further.  I'll try my laptop and see if it picks up the network.  Be great if there was a CLI command for this, then I could see the output in the terminal.

---

### Post by ian-weisser on 2016-01-17
> **MechaMechanism said:**
> Ok.  I see in Settings/Network/Wireless it shows as working.  But My Verizon Samsung Galaxy S6 Edge does not see the network.
There are several kinds of wireless networks, including ad-hoc (between machines) and infrastructure (machine to gateway).
Thanks to decisions by wireless hardware manufacturers, most wireless hardware drivers in Linux do not support infrastructure connections. They will only do ad-hoc.
Android, thanks to a decision by Google, cannot usually see ad-hoc networks.

---

### Post by jeremy31 on 2016-01-17
> **ian-weisser said:**
> There are several kinds of wireless networks, including ad-hoc (between machines) and infrastructure (machine to gateway).
Thanks to decisions by wireless hardware manufacturers, most wireless hardware drivers in Linux do not support infrastructure connections. They will only do ad-hoc.
Android, thanks to a decision by Google, cannot usually see ad-hoc networks.

There are some hacks to get it working if you search google for "android ad-hoc" but I have no idea how safe they are

---

### Post by MechaMechanism on 2016-01-17
Oh well.  I don't need to concern myself with it as I have Internet and a wireless router.  Just not worth the hassle, too much work for too little gain for me, so I'll forget about it.

---

