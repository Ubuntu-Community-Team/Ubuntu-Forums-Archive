---
title: "dhclient Causing Delay During Wake Up"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by pgn674 on 2008-09-28
I have a Lenovo 3000 C200 (8922-A4U) laptop, with the "wl" proprietary device driver. It has a BCM4311 802.11b/g WLAN Network Controller from Broadcom Corporation. I'm running Ubuntu 8.04 with the latest updates, and Gnome.

When I put the laptop to sleep, it goes to sleep fast and easy. But, when I try to wake it up, it stays on a powered but black screen, with a single blinking cursor in the upper left corner for 45 seconds, before finally loading the desktop, at which time it's fully responsive.

I took a look at some logs, and found that dhclient seems to be taking up a lot of time.

In the logs below, the following is the times of events I actioned and saw, according to my synchronized watch:
Sep 28 18:03:00 - I selected suspend from the upper right power icon.
03:05 - Computer went to sleep, with the moon light on the front turning on.
04:00 - I hit the space bar, the the moon light turned off.
04:49 - A responsive desktop appeared on my screen.

Here is the syslog, with dhclient taking its time at 04:07 and beyond:
```
Sep 28 18:00:52 paul-laptop dhclient: No working leases in persistent database - sleeping.
Sep 28 18:03:02 paul-laptop NetworkManager: <info>  Going to sleep. 
Sep 28 18:03:02 paul-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 22041
Sep 28 18:03:02 paul-laptop dhclient: killed old client process, removed PID file
Sep 28 18:03:02 paul-laptop avahi-autoipd(eth0)[21693]: if_indextoname() failed: No such device or address
Sep 28 18:03:02 paul-laptop dhclient: receive_packet failed on eth0: Network is down
Sep 28 18:03:02 paul-laptop avahi-autoipd(eth0)[21693]: Callout STOP, address 169.254.6.35 on interface (null)
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.6.35.
Sep 28 18:03:02 paul-laptop avahi-autoipd(eth0)[21694]: if_indextoname() failed: No such device or address
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Withdrawing address record for 169.254.6.35 on eth0.
Sep 28 18:03:02 paul-laptop kernel: [25380.796907] ACPI: PCI interrupt for device 0000:05:01.0 disabled
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Interface eth1.IPv4 no longer relevant for mDNS.
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Withdrawing address record for fe80::219:7eff:fe69:11d1 on eth1.
Sep 28 18:03:02 paul-laptop avahi-daemon[5302]: Withdrawing address record for 192.168.2.4 on eth1.
Sep 28 18:03:02 paul-laptop kernel: [25380.893081] ndiswrapper: device eth1 removed
Sep 28 18:03:02 paul-laptop kernel: [25380.893114] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Sep 28 18:03:02 paul-laptop kernel: [25380.893244] usbcore: deregistering interface driver ndiswrapper
Sep 28 18:03:02 paul-laptop NetworkManager: <debug> [1222639382.652035] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_0f_b0_d6_72_15'). 
Sep 28 18:03:02 paul-laptop NetworkManager: <debug> [1222639382.652127] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_19_7e_69_11_d1'). 
Sep 28 18:03:02 paul-laptop NetworkManager: <info>  Deactivating device eth1. 
Sep 28 18:03:02 paul-laptop dhclient: Bind socket to interface: No such device
Sep 28 18:03:02 paul-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: No such device 
Sep 28 18:04:03 paul-laptop kernel: [25381.822218] Syncing filesystems ... done.
Sep 28 18:04:03 paul-laptop kernel: [25381.822253] PM: Preparing system for mem sleep
Sep 28 18:04:03 paul-laptop kernel: [25381.822257] Freezing user space processes ... (elapsed 0.00 seconds) done.
Sep 28 18:04:03 paul-laptop kernel: [25381.823142] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Sep 28 18:04:03 paul-laptop kernel: [25381.920835] PM: Entering mem sleep
Sep 28 18:04:03 paul-laptop kernel: [25381.920837] Suspending console(s)
Sep 28 18:04:03 paul-laptop kernel: [25381.936336] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25381.951851] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Sep 28 18:04:03 paul-laptop kernel: [25382.149378] sd 0:0:0:0: [sda] Stopping disk
Sep 28 18:04:03 paul-laptop kernel: [25383.111777] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.111953] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.111974] ACPI: PCI interrupt for device 0000:05:06.1 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.111980] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.131749] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.147231] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.162820] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178718] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178756] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178793] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178829] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.194665] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.227517] Disabling non-boot CPUs ...
Sep 28 18:04:03 paul-laptop kernel: [25383.227543] CPU0 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [25383.227545] CPU1 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [25383.342497] CPU 1 is now offline
Sep 28 18:04:03 paul-laptop kernel: [25383.342501] SMP alternatives: switching to UP code
Sep 28 18:04:03 paul-laptop kernel: [25383.344156] CPU0 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [25383.344159]  domain 0: span 01
Sep 28 18:04:03 paul-laptop kernel: [25383.344161]   groups: 01
Sep 28 18:04:03 paul-laptop kernel: [25383.344399] CPU1 is down
Sep 28 18:04:03 paul-laptop kernel: [    0.207623] Back to C!
Sep 28 18:04:03 paul-laptop kernel: [    0.208141] Enabling non-boot CPUs ...
Sep 28 18:04:03 paul-laptop kernel: [    0.208251] CPU0 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [    0.217950] SMP alternatives: switching to SMP code
Sep 28 18:04:03 paul-laptop kernel: [    0.219275] Booting processor 1/1 eip 3000
Sep 28 18:04:03 paul-laptop kernel: [    0.229379] Initializing CPU#1
Sep 28 18:04:03 paul-laptop kernel: [    0.309754] Calibrating delay using timer specific routine.. 3192.14 BogoMIPS (lpj=6384290)
Sep 28 18:04:03 paul-laptop kernel: [    0.309762] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Sep 28 18:04:03 paul-laptop kernel: [    0.309769] monitor/mwait feature present.
Sep 28 18:04:03 paul-laptop kernel: [    0.309772] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 18:04:03 paul-laptop kernel: [    0.309775] CPU: L2 cache: 1024K
Sep 28 18:04:03 paul-laptop kernel: [    0.309777] CPU: Physical Processor ID: 0
Sep 28 18:04:03 paul-laptop kernel: [    0.309778] CPU: Processor Core ID: 1
Sep 28 18:04:03 paul-laptop kernel: [    0.309780] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00042940 0000c189 00000000 00000000 00000000
Sep 28 18:04:03 paul-laptop kernel: [    0.310207] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
Sep 28 18:04:03 paul-laptop kernel: [    0.310268] CPU0 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [    0.310271]  domain 0: span 03
Sep 28 18:04:03 paul-laptop kernel: [    0.310273]   groups: 01 02
Sep 28 18:04:03 paul-laptop kernel: [    0.310276] CPU1 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [    0.310278]  domain 0: span 03
Sep 28 18:04:03 paul-laptop kernel: [    0.310279]   groups: 02 01
Sep 28 18:04:03 paul-laptop kernel: [    0.310652] CPU1 is up
Sep 28 18:04:03 paul-laptop kernel: [    0.311167] APIC error on CPU0: 00(40)
Sep 28 18:04:03 paul-laptop kernel: [    0.314250] Switched to high resolution mode on CPU 1
Sep 28 18:04:03 paul-laptop kernel: [    0.754967] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
Sep 28 18:04:03 paul-laptop kernel: [    0.785368] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Sep 28 18:04:03 paul-laptop kernel: [    0.785397] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Sep 28 18:04:03 paul-laptop kernel: [    0.785406] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785444] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
Sep 28 18:04:03 paul-laptop kernel: [    0.785455] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100107, writing 100507)
Sep 28 18:04:03 paul-laptop kernel: [    0.785498] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785531] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100107, writing 100507)
Sep 28 18:04:03 paul-laptop kernel: [    0.785573] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785582] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.785588] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785642] usb usb1: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785677] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Sep 28 18:04:03 paul-laptop kernel: [    0.785683] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785735] usb usb2: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785755] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Sep 28 18:04:03 paul-laptop kernel: [    0.785761] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785813] usb usb3: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785832] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Sep 28 18:04:03 paul-laptop kernel: [    0.785838] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785890] usb usb4: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.801310] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.801316] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.801388] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050500, writing 20090500)
Sep 28 18:04:03 paul-laptop kernel: [    0.801400] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
Sep 28 18:04:03 paul-laptop kernel: [    0.801422] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.817322] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
Sep 28 18:04:03 paul-laptop kernel: [    0.817341] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Sep 28 18:04:03 paul-laptop kernel: [    0.817347] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.817452] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
Sep 28 18:04:03 paul-laptop kernel: [    0.817536] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing d0000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817552] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
Sep 28 18:04:03 paul-laptop kernel: [    0.817575] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100103)
Sep 28 18:04:03 paul-laptop kernel: [    0.817685] PM: Writing back config space on device 0000:05:01.0 at offset 3 (was 0, writing 4000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817693] PM: Writing back config space on device 0000:05:01.0 at offset 1 (was 2900007, writing 2900003)
Sep 28 18:04:03 paul-laptop kernel: [    0.817726] PM: Writing back config space on device 0000:05:04.0 at offset f (was 74001ff, writing 5c001ff)
Sep 28 18:04:03 paul-laptop kernel: [    0.817735] PM: Writing back config space on device 0000:05:04.0 at offset e (was 0, writing 28fc)
Sep 28 18:04:03 paul-laptop kernel: [    0.817742] PM: Writing back config space on device 0000:05:04.0 at offset d (was 0, writing 2800)
Sep 28 18:04:03 paul-laptop kernel: [    0.817749] PM: Writing back config space on device 0000:05:04.0 at offset c (was 0, writing 24fc)
Sep 28 18:04:03 paul-laptop kernel: [    0.817758] PM: Writing back config space on device 0000:05:04.0 at offset b (was 0, writing 2400)
Sep 28 18:04:03 paul-laptop kernel: [    0.817764] PM: Writing back config space on device 0000:05:04.0 at offset a (was 0, writing 57fff000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817771] PM: Writing back config space on device 0000:05:04.0 at offset 9 (was 0, writing 54000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817778] PM: Writing back config space on device 0000:05:04.0 at offset 8 (was 0, writing 53fff000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817785] PM: Writing back config space on device 0000:05:04.0 at offset 7 (was 0, writing 50000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817792] PM: Writing back config space on device 0000:05:04.0 at offset 6 (was 20000000, writing b0090605)
Sep 28 18:04:03 paul-laptop kernel: [    0.817800] PM: Writing back config space on device 0000:05:04.0 at offset 4 (was 0, writing d0102000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817807] PM: Writing back config space on device 0000:05:04.0 at offset 3 (was 24008, writing 2a820)
Sep 28 18:04:03 paul-laptop kernel: [    0.833305] PM: Writing back config space on device 0000:05:06.0 at offset 3 (was 800000, writing 804000)
Sep 28 18:04:03 paul-laptop kernel: [    0.833313] PM: Writing back config space on device 0000:05:06.0 at offset 1 (was 2100000, writing 2100006)
Sep 28 18:04:03 paul-laptop kernel: [    0.885968] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 28 18:04:03 paul-laptop kernel: [    0.905241] PM: Writing back config space on device 0000:05:06.1 at offset 3 (was 800000, writing 804000)
Sep 28 18:04:03 paul-laptop kernel: [    0.905249] PM: Writing back config space on device 0000:05:06.1 at offset 1 (was 2100000, writing 2100006)
Sep 28 18:04:03 paul-laptop kernel: [    0.905270] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.905310] PM: Writing back config space on device 0000:05:06.2 at offset 4 (was d0101000, writing d0101400)
Sep 28 18:04:03 paul-laptop kernel: [    0.905355] PM: Writing back config space on device 0000:05:06.3 at offset 4 (was d0101400, writing d0101800)
Sep 28 18:04:03 paul-laptop kernel: [    0.905382] PM: Writing back config space on device 0000:05:06.4 at offset f (was 205, writing 2ff)
Sep 28 18:04:03 paul-laptop kernel: [    0.905405] PM: Writing back config space on device 0000:05:06.4 at offset 4 (was d0101800, writing ffffff00)
Sep 28 18:04:03 paul-laptop kernel: [    0.905415] PM: Writing back config space on device 0000:05:06.4 at offset 1 (was 2100000, writing 2100542)
Sep 28 18:04:03 paul-laptop kernel: [    1.137492] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    1.137496] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    1.309272] ata2.00: configured for UDMA/33
Sep 28 18:04:03 paul-laptop kernel: [    2.311920] sd 0:0:0:0: [sda] Starting disk
Sep 28 18:04:03 paul-laptop kernel: [    2.776818] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    2.776822] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    2.797064] ata1.00: configured for UDMA/100
Sep 28 18:04:03 paul-laptop kernel: [    2.815805] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Sep 28 18:04:03 paul-laptop kernel: [    2.815826] sd 0:0:0:0: [sda] Write Protect is off
Sep 28 18:04:03 paul-laptop kernel: [    2.815829] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 28 18:04:03 paul-laptop kernel: [    2.815848] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 18:04:03 paul-laptop kernel: [    2.831469] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Sep 28 18:04:03 paul-laptop kernel: [    2.832854] PM: Finishing wakeup.
Sep 28 18:04:03 paul-laptop kernel: [    2.832855] Restarting tasks ... <6>usb 1-1: USB disconnect, address 3
Sep 28 18:04:03 paul-laptop kernel: [    2.838409] done.
Sep 28 18:04:03 paul-laptop anacron[25027]: Anacron 2.3 started on 2008-09-28
Sep 28 18:04:03 paul-laptop anacron[25027]: Normal exit (0 jobs run)
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.822785] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0_logicaldev_input'). 
Sep 28 18:04:03 paul-laptop gnome-power-manager: (paul) Resuming computer
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.835617] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0'). 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.841181] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial'). 
Sep 28 18:04:03 paul-laptop kernel: [    2.991321] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Sep 28 18:04:03 paul-laptop kernel: [    3.006800] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Sep 28 18:04:03 paul-laptop kernel: [    3.007468] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Sep 28 18:04:03 paul-laptop kernel: [    3.007543] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    3.012832] ndiswrapper: using IRQ 16
Sep 28 18:04:03 paul-laptop kernel: [    3.239103] usb 1-1: new low speed USB device using uhci_hcd and address 4
Sep 28 18:04:03 paul-laptop kernel: [    3.384164] wlan0: ethernet device 00:19:7e:69:11:d1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
Sep 28 18:04:03 paul-laptop kernel: [    3.384884] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Sep 28 18:04:03 paul-laptop kernel: [    3.386757] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Sep 28 18:04:03 paul-laptop kernel: [    3.386881] udev: renamed network interface wlan0 to eth1
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.426360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_19_7e_69_11_d1'). 
Sep 28 18:04:03 paul-laptop kernel: [    3.418220] usb 1-1: configuration #1 chosen from 1 choice
Sep 28 18:04:03 paul-laptop kernel: [    3.420854] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 28 18:04:03 paul-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'ndiswrapper'. 
Sep 28 18:04:03 paul-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Sep 28 18:04:03 paul-laptop kernel: [    3.435615] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input13
Sep 28 18:04:03 paul-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep 28 18:04:03 paul-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep 28 18:04:03 paul-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Sep 28 18:04:03 paul-laptop NetworkManager: <info>  Deactivating device eth1. 
Sep 28 18:04:03 paul-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Invalid argument 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.480044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial'). 
Sep 28 18:04:03 paul-laptop kernel: [    3.483932] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Sep 28 18:04:03 paul-laptop kernel: [    3.484490] usbcore: registered new interface driver ndiswrapper
Sep 28 18:04:03 paul-laptop kernel: [    3.514855] 8139too Fast Ethernet driver 0.9.28
Sep 28 18:04:03 paul-laptop kernel: [    3.514940] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 21
Sep 28 18:04:03 paul-laptop kernel: [    3.516398] eth0: RealTek RTL8139 at 0x2000, 00:0f:b0:d6:72:15, IRQ 21
Sep 28 18:04:03 paul-laptop kernel: [    3.516401] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.568732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0'). 
Sep 28 18:04:03 paul-laptop kernel: [    3.581124] eth0: link down
Sep 28 18:04:03 paul-laptop kernel: [    3.583183] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.623345] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0f_b0_d6_72_15'). 
Sep 28 18:04:03 paul-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 21698
Sep 28 18:04:03 paul-laptop dhclient: killed old client process, removed PID file
Sep 28 18:04:03 paul-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep 28 18:04:03 paul-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep 28 18:04:03 paul-laptop dhclient: All rights reserved.
Sep 28 18:04:03 paul-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 28 18:04:03 paul-laptop dhclient: 
Sep 28 18:04:03 paul-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep 28 18:04:03 paul-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep 28 18:04:03 paul-laptop dhclient: All rights reserved.
Sep 28 18:04:03 paul-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 28 18:04:03 paul-laptop dhclient: 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.675355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0_logicaldev_input'). 
Sep 28 18:04:03 paul-laptop dhclient: Listening on LPF/eth0/00:0f:b0:d6:72:15
Sep 28 18:04:03 paul-laptop dhclient: Sending on   LPF/eth0/00:0f:b0:d6:72:15
Sep 28 18:04:03 paul-laptop dhclient: Sending on   Socket/fallback
Sep 28 18:04:03 paul-laptop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Sep 28 18:04:03 paul-laptop dhclient: send_packet: Network is unreachable
Sep 28 18:04:03 paul-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Sep 28 18:04:03 paul-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Sep 28 18:04:03 paul-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep 28 18:04:03 paul-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep 28 18:04:03 paul-laptop dhclient: All rights reserved.
Sep 28 18:04:03 paul-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 28 18:04:03 paul-laptop dhclient: 
Sep 28 18:04:04 paul-laptop dhclient: Listening on LPF/eth0/00:0f:b0:d6:72:15
Sep 28 18:04:04 paul-laptop dhclient: Sending on   LPF/eth0/00:0f:b0:d6:72:15
Sep 28 18:04:04 paul-laptop dhclient: Sending on   Socket/fallback
Sep 28 18:04:04 paul-laptop dhclient: receive_packet failed on eth0: Network is down
Sep 28 18:04:04 paul-laptop dhclient: Bind socket to interface: No such device
Sep 28 18:04:04 paul-laptop kernel: [    4.823953] eth0: link down
Sep 28 18:04:04 paul-laptop kernel: [    4.828042] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 18:04:04 paul-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Sep 28 18:04:04 paul-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep 28 18:04:04 paul-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep 28 18:04:04 paul-laptop dhclient: All rights reserved.
Sep 28 18:04:04 paul-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 28 18:04:04 paul-laptop dhclient: 
Sep 28 18:04:05 paul-laptop dhclient: Listening on LPF/eth0/00:0f:b0:d6:72:15
Sep 28 18:04:05 paul-laptop dhclient: Sending on   LPF/eth0/00:0f:b0:d6:72:15
Sep 28 18:04:05 paul-laptop dhclient: Sending on   Socket/fallback
Sep 28 18:04:07 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep 28 18:04:08 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Sep 28 18:04:12 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 28 18:04:12 paul-laptop ntpd[22199]: sendto(132.236.56.250) (fd=20): Invalid argument
Sep 28 18:04:14 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Sep 28 18:04:18 paul-laptop ntpd[22199]: sendto(91.189.94.4) (fd=20): Invalid argument
Sep 28 18:04:20 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Sep 28 18:04:25 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Sep 28 18:04:31 paul-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 28 18:04:38 paul-laptop dhclient: No DHCPOFFERS received.
Sep 28 18:04:38 paul-laptop dhclient: No working leases in persistent database - sleeping.
Sep 28 18:04:38 paul-laptop avahi-autoipd(eth0)[25270]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Sep 28 18:04:38 paul-laptop avahi-autoipd(eth0)[25270]: Successfully called chroot().
Sep 28 18:04:38 paul-laptop avahi-autoipd(eth0)[25270]: Successfully dropped root privileges.
Sep 28 18:04:38 paul-laptop avahi-autoipd(eth0)[25270]: fopen() failed: Permission denied
Sep 28 18:04:38 paul-laptop avahi-autoipd(eth0)[25270]: Starting with address 169.254.6.35
Sep 28 18:04:39 paul-laptop dhclient: No DHCPOFFERS received.
Sep 28 18:04:39 paul-laptop dhclient: No working leases in persistent database - sleeping.
Sep 28 18:04:39 paul-laptop ntpd[22199]: ntpd exiting on signal 15
Sep 28 18:04:39 paul-laptop ntpdate[25334]: can't find host ntp.ubuntu.com 
Sep 28 18:04:39 paul-laptop ntpdate[25334]: can't find host ntp0.cornell.edu 
Sep 28 18:04:39 paul-laptop ntpdate[25334]: no servers can be used, exiting
Sep 28 18:04:39 paul-laptop ntpd[25364]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Sep 28 18:04:39 paul-laptop ntpd[25367]: precision = 1.000 usec
Sep 28 18:04:39 paul-laptop ntpd[25367]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep 28 18:04:39 paul-laptop ntpd[25367]: Listening on interface #1 wildcard, ::#123 Disabled
Sep 28 18:04:39 paul-laptop ntpd[25367]: Listening on interface #2 lo, ::1#123 Enabled
Sep 28 18:04:39 paul-laptop ntpd[25367]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Sep 28 18:04:39 paul-laptop ntpd[25367]: kernel time sync status 0040
Sep 28 18:04:39 paul-laptop ntpd[25367]: frequency initialized -58.272 PPM from /var/lib/ntp/ntp.drift
Sep 28 18:04:41 paul-laptop ntpd_initres[25368]: host name not found: ntp.ubuntu.com
Sep 28 18:04:41 paul-laptop ntpd_initres[25368]: couldn't resolve `ntp.ubuntu.com', giving up on it
Sep 28 18:04:41 paul-laptop ntpd_initres[25368]: host name not found: ntp0.cornell.edu
Sep 28 18:04:41 paul-laptop ntpd_initres[25368]: couldn't resolve `ntp0.cornell.edu', giving up on it
Sep 28 18:04:42 paul-laptop avahi-autoipd(eth0)[25270]: Callout BIND, address 169.254.6.35 on interface eth0
Sep 28 18:04:42 paul-laptop avahi-daemon[5302]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.6.35.
Sep 28 18:04:42 paul-laptop avahi-daemon[5302]: New relevant interface eth0.IPv4 for mDNS.
Sep 28 18:04:42 paul-laptop avahi-daemon[5302]: Registering new address record for 169.254.6.35 on eth0.IPv4.
Sep 28 18:04:46 paul-laptop avahi-autoipd(eth0)[25270]: Successfully claimed IP address 169.254.6.35
Sep 28 18:04:46 paul-laptop avahi-autoipd(eth0)[25270]: fopen() failed: Permission denied
Sep 28 18:04:47 paul-laptop ntpd[25367]: ntpd exiting on signal 15
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  Waking up from sleep. 
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  Deactivating device eth1. 
Sep 28 18:04:47 paul-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Invalid argument 
Sep 28 18:04:47 paul-laptop kernel: [   47.095428] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'ndiswrapper'. 
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Sep 28 18:04:47 paul-laptop NetworkManager: <info>  Deactivating device eth1. 
Sep 28 18:04:47 paul-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Invalid argument 
Sep 28 18:04:57 paul-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
```

And here are other logs, in case you want to see them:

messages
```
Sep 28 17:50:05 paul-laptop kernel: [24604.627475] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Sep 28 18:03:02 paul-laptop kernel: [25380.796907] ACPI: PCI interrupt for device 0000:05:01.0 disabled
Sep 28 18:03:02 paul-laptop kernel: [25380.893081] ndiswrapper: device eth1 removed
Sep 28 18:03:02 paul-laptop kernel: [25380.893114] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Sep 28 18:03:02 paul-laptop kernel: [25380.893244] usbcore: deregistering interface driver ndiswrapper
Sep 28 18:04:03 paul-laptop kernel: [25381.822218] Syncing filesystems ... done.
Sep 28 18:04:03 paul-laptop kernel: [25381.822257] Freezing user space processes ... (elapsed 0.00 seconds) done.
Sep 28 18:04:03 paul-laptop kernel: [25381.823142] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Sep 28 18:04:03 paul-laptop kernel: [25381.920837] Suspending console(s)
Sep 28 18:04:03 paul-laptop kernel: [25381.936336] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25381.951851] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Sep 28 18:04:03 paul-laptop kernel: [25382.149378] sd 0:0:0:0: [sda] Stopping disk
Sep 28 18:04:03 paul-laptop kernel: [25383.111974] ACPI: PCI interrupt for device 0000:05:06.1 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.147231] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.162820] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178718] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178756] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178793] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178829] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.194665] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.227517] Disabling non-boot CPUs ...
Sep 28 18:04:03 paul-laptop kernel: [25383.342497] CPU 1 is now offline
Sep 28 18:04:03 paul-laptop kernel: [25383.342501] SMP alternatives: switching to UP code
Sep 28 18:04:03 paul-laptop kernel: [25383.344399] CPU1 is down
Sep 28 18:04:03 paul-laptop kernel: [    0.208141] Enabling non-boot CPUs ...
Sep 28 18:04:03 paul-laptop kernel: [    0.217950] SMP alternatives: switching to SMP code
Sep 28 18:04:03 paul-laptop kernel: [    0.219275] Booting processor 1/1 eip 3000
Sep 28 18:04:03 paul-laptop kernel: [    0.229379] Initializing CPU#1
Sep 28 18:04:03 paul-laptop kernel: [    0.309754] Calibrating delay using timer specific routine.. 3192.14 BogoMIPS (lpj=6384290)
Sep 28 18:04:03 paul-laptop kernel: [    0.309769] monitor/mwait feature present.
Sep 28 18:04:03 paul-laptop kernel: [    0.309772] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 18:04:03 paul-laptop kernel: [    0.309775] CPU: L2 cache: 1024K
Sep 28 18:04:03 paul-laptop kernel: [    0.309777] CPU: Physical Processor ID: 0
Sep 28 18:04:03 paul-laptop kernel: [    0.309778] CPU: Processor Core ID: 1
Sep 28 18:04:03 paul-laptop kernel: [    0.310207] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
Sep 28 18:04:03 paul-laptop kernel: [    0.310652] CPU1 is up
Sep 28 18:04:03 paul-laptop kernel: [    0.785397] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Sep 28 18:04:03 paul-laptop kernel: [    0.785582] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.785642] usb usb1: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785677] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Sep 28 18:04:03 paul-laptop kernel: [    0.785735] usb usb2: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785755] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Sep 28 18:04:03 paul-laptop kernel: [    0.785813] usb usb3: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785832] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Sep 28 18:04:03 paul-laptop kernel: [    0.785890] usb usb4: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.801310] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.817341] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Sep 28 18:04:03 paul-laptop kernel: [    0.885968] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 28 18:04:03 paul-laptop kernel: [    0.905270] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    1.137492] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    1.137496] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    1.309272] ata2.00: configured for UDMA/33
Sep 28 18:04:03 paul-laptop kernel: [    2.311920] sd 0:0:0:0: [sda] Starting disk
Sep 28 18:04:03 paul-laptop kernel: [    2.776818] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    2.776822] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    2.797064] ata1.00: configured for UDMA/100
Sep 28 18:04:03 paul-laptop kernel: [    2.815805] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Sep 28 18:04:03 paul-laptop kernel: [    2.815826] sd 0:0:0:0: [sda] Write Protect is off
Sep 28 18:04:03 paul-laptop kernel: [    2.815848] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 18:04:03 paul-laptop kernel: [    2.831469] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Sep 28 18:04:03 paul-laptop kernel: [    2.832855] Restarting tasks ... <6>usb 1-1: USB disconnect, address 3
Sep 28 18:04:03 paul-laptop kernel: [    2.838409] done.
Sep 28 18:04:03 paul-laptop gnome-power-manager: (paul) Resuming computer
Sep 28 18:04:03 paul-laptop kernel: [    2.991321] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)

Sep 28 18:04:03 paul-laptop kernel: [    3.006800] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Sep 28 18:04:03 paul-laptop kernel: [    3.007468] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Sep 28 18:04:03 paul-laptop kernel: [    3.012832] ndiswrapper: using IRQ 16
Sep 28 18:04:03 paul-laptop kernel: [    3.239103] usb 1-1: new low speed USB device using uhci_hcd and address 4
Sep 28 18:04:03 paul-laptop kernel: [    3.384164] wlan0: ethernet device 00:19:7e:69:11:d1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
Sep 28 18:04:03 paul-laptop kernel: [    3.384884] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Sep 28 18:04:03 paul-laptop kernel: [    3.386757] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Sep 28 18:04:03 paul-laptop kernel: [    3.386881] udev: renamed network interface wlan0 to eth1
Sep 28 18:04:03 paul-laptop kernel: [    3.418220] usb 1-1: configuration #1 chosen from 1 choice
Sep 28 18:04:03 paul-laptop kernel: [    3.420854] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 28 18:04:03 paul-laptop kernel: [    3.435615] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input13
Sep 28 18:04:03 paul-laptop kernel: [    3.483932] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Sep 28 18:04:03 paul-laptop kernel: [    3.484490] usbcore: registered new interface driver ndiswrapper
Sep 28 18:04:03 paul-laptop kernel: [    3.514855] 8139too Fast Ethernet driver 0.9.28
Sep 28 18:04:03 paul-laptop kernel: [    3.514940] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 21
Sep 28 18:04:03 paul-laptop kernel: [    3.516398] eth0: RealTek RTL8139 at 0x2000, 00:0f:b0:d6:72:15, IRQ 21
Sep 28 18:04:03 paul-laptop kernel: [    3.581124] eth0: link down
Sep 28 18:04:03 paul-laptop kernel: [    3.583183] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 18:04:04 paul-laptop kernel: [    4.823953] eth0: link down
Sep 28 18:04:04 paul-laptop kernel: [    4.828042] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 18:04:47 paul-laptop kernel: [   47.095428] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 28 18:05:03 paul-laptop kernel: [   62.975267] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```

kern.log
```
Sep 28 17:50:05 paul-laptop kernel: [24604.627475] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Sep 28 18:03:02 paul-laptop kernel: [25380.796907] ACPI: PCI interrupt for device 0000:05:01.0 disabled
Sep 28 18:03:02 paul-laptop kernel: [25380.893081] ndiswrapper: device eth1 removed
Sep 28 18:03:02 paul-laptop kernel: [25380.893114] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Sep 28 18:03:02 paul-laptop kernel: [25380.893244] usbcore: deregistering interface driver ndiswrapper
Sep 28 18:04:03 paul-laptop kernel: [25381.822218] Syncing filesystems ... done.
Sep 28 18:04:03 paul-laptop kernel: [25381.822253] PM: Preparing system for mem sleep
Sep 28 18:04:03 paul-laptop kernel: [25381.822257] Freezing user space processes ... (elapsed 0.00 seconds) done.
Sep 28 18:04:03 paul-laptop kernel: [25381.823142] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Sep 28 18:04:03 paul-laptop kernel: [25381.920835] PM: Entering mem sleep
Sep 28 18:04:03 paul-laptop kernel: [25381.920837] Suspending console(s)
Sep 28 18:04:03 paul-laptop kernel: [25381.936336] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25381.951851] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Sep 28 18:04:03 paul-laptop kernel: [25382.149378] sd 0:0:0:0: [sda] Stopping disk
Sep 28 18:04:03 paul-laptop kernel: [25383.111777] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.111953] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.111974] ACPI: PCI interrupt for device 0000:05:06.1 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.111980] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.131749] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.147231] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.162820] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178718] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178756] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178793] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.178829] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.194665] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Sep 28 18:04:03 paul-laptop kernel: [25383.227517] Disabling non-boot CPUs ...
Sep 28 18:04:03 paul-laptop kernel: [25383.227543] CPU0 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [25383.227545] CPU1 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [25383.342497] CPU 1 is now offline
Sep 28 18:04:03 paul-laptop kernel: [25383.342501] SMP alternatives: switching to UP code
Sep 28 18:04:03 paul-laptop kernel: [25383.344156] CPU0 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [25383.344159]  domain 0: span 01
Sep 28 18:04:03 paul-laptop kernel: [25383.344161]   groups: 01
Sep 28 18:04:03 paul-laptop kernel: [25383.344399] CPU1 is down
Sep 28 18:04:03 paul-laptop kernel: [    0.207623] Back to C!
Sep 28 18:04:03 paul-laptop kernel: [    0.208141] Enabling non-boot CPUs ...
Sep 28 18:04:03 paul-laptop kernel: [    0.208251] CPU0 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [    0.217950] SMP alternatives: switching to SMP code
Sep 28 18:04:03 paul-laptop kernel: [    0.219275] Booting processor 1/1 eip 3000
Sep 28 18:04:03 paul-laptop kernel: [    0.229379] Initializing CPU#1
Sep 28 18:04:03 paul-laptop kernel: [    0.309754] Calibrating delay using timer specific routine.. 3192.14 BogoMIPS (lpj=6384290)
Sep 28 18:04:03 paul-laptop kernel: [    0.309762] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Sep 28 18:04:03 paul-laptop kernel: [    0.309769] monitor/mwait feature present.
Sep 28 18:04:03 paul-laptop kernel: [    0.309772] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 18:04:03 paul-laptop kernel: [    0.309775] CPU: L2 cache: 1024K
Sep 28 18:04:03 paul-laptop kernel: [    0.309777] CPU: Physical Processor ID: 0
Sep 28 18:04:03 paul-laptop kernel: [    0.309778] CPU: Processor Core ID: 1
Sep 28 18:04:03 paul-laptop kernel: [    0.309780] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00042940 0000c189 00000000 00000000 00000000
Sep 28 18:04:03 paul-laptop kernel: [    0.310207] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
Sep 28 18:04:03 paul-laptop kernel: [    0.310268] CPU0 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [    0.310271]  domain 0: span 03
Sep 28 18:04:03 paul-laptop kernel: [    0.310273]   groups: 01 02
Sep 28 18:04:03 paul-laptop kernel: [    0.310276] CPU1 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [    0.310278]  domain 0: span 03
Sep 28 18:04:03 paul-laptop kernel: [    0.310279]   groups: 02 01
Sep 28 18:04:03 paul-laptop kernel: [    0.310652] CPU1 is up
Sep 28 18:04:03 paul-laptop kernel: [    0.311167] APIC error on CPU0: 00(40)
Sep 28 18:04:03 paul-laptop kernel: [    0.314250] Switched to high resolution mode on CPU 1
Sep 28 18:04:03 paul-laptop kernel: [    0.754967] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
Sep 28 18:04:03 paul-laptop kernel: [    0.785368] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Sep 28 18:04:03 paul-laptop kernel: [    0.785397] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Sep 28 18:04:03 paul-laptop kernel: [    0.785406] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785444] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
Sep 28 18:04:03 paul-laptop kernel: [    0.785455] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100107, writing 100507)
Sep 28 18:04:03 paul-laptop kernel: [    0.785498] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785531] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100107, writing 100507)
Sep 28 18:04:03 paul-laptop kernel: [    0.785573] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785582] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.785588] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785642] usb usb1: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785677] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Sep 28 18:04:03 paul-laptop kernel: [    0.785683] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785735] usb usb2: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785755] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Sep 28 18:04:03 paul-laptop kernel: [    0.785761] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785813] usb usb3: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.785832] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Sep 28 18:04:03 paul-laptop kernel: [    0.785838] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785890] usb usb4: root hub lost power or was reset
Sep 28 18:04:03 paul-laptop kernel: [    0.801310] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.801316] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.801388] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050500, writing 20090500)
Sep 28 18:04:03 paul-laptop kernel: [    0.801400] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
Sep 28 18:04:03 paul-laptop kernel: [    0.801422] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.817322] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
Sep 28 18:04:03 paul-laptop kernel: [    0.817341] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Sep 28 18:04:03 paul-laptop kernel: [    0.817347] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.817452] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
Sep 28 18:04:03 paul-laptop kernel: [    0.817536] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing d0000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817552] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
Sep 28 18:04:03 paul-laptop kernel: [    0.817575] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100103)
Sep 28 18:04:03 paul-laptop kernel: [    0.817685] PM: Writing back config space on device 0000:05:01.0 at offset 3 (was 0, writing 4000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817693] PM: Writing back config space on device 0000:05:01.0 at offset 1 (was 2900007, writing 2900003)
Sep 28 18:04:03 paul-laptop kernel: [    0.817726] PM: Writing back config space on device 0000:05:04.0 at offset f (was 74001ff, writing 5c001ff)
Sep 28 18:04:03 paul-laptop kernel: [    0.817735] PM: Writing back config space on device 0000:05:04.0 at offset e (was 0, writing 28fc)
Sep 28 18:04:03 paul-laptop kernel: [    0.817742] PM: Writing back config space on device 0000:05:04.0 at offset d (was 0, writing 2800)
Sep 28 18:04:03 paul-laptop kernel: [    0.817749] PM: Writing back config space on device 0000:05:04.0 at offset c (was 0, writing 24fc)
Sep 28 18:04:03 paul-laptop kernel: [    0.817758] PM: Writing back config space on device 0000:05:04.0 at offset b (was 0, writing 2400)
Sep 28 18:04:03 paul-laptop kernel: [    0.817764] PM: Writing back config space on device 0000:05:04.0 at offset a (was 0, writing 57fff000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817771] PM: Writing back config space on device 0000:05:04.0 at offset 9 (was 0, writing 54000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817778] PM: Writing back config space on device 0000:05:04.0 at offset 8 (was 0, writing 53fff000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817785] PM: Writing back config space on device 0000:05:04.0 at offset 7 (was 0, writing 50000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817792] PM: Writing back config space on device 0000:05:04.0 at offset 6 (was 20000000, writing b0090605)
Sep 28 18:04:03 paul-laptop kernel: [    0.817800] PM: Writing back config space on device 0000:05:04.0 at offset 4 (was 0, writing d0102000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817807] PM: Writing back config space on device 0000:05:04.0 at offset 3 (was 24008, writing 2a820)
Sep 28 18:04:03 paul-laptop kernel: [    0.833305] PM: Writing back config space on device 0000:05:06.0 at offset 3 (was 800000, writing 804000)
Sep 28 18:04:03 paul-laptop kernel: [    0.833313] PM: Writing back config space on device 0000:05:06.0 at offset 1 (was 2100000, writing 2100006)
Sep 28 18:04:03 paul-laptop kernel: [    0.885968] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 28 18:04:03 paul-laptop kernel: [    0.905241] PM: Writing back config space on device 0000:05:06.1 at offset 3 (was 800000, writing 804000)
Sep 28 18:04:03 paul-laptop kernel: [    0.905249] PM: Writing back config space on device 0000:05:06.1 at offset 1 (was 2100000, writing 2100006)
Sep 28 18:04:03 paul-laptop kernel: [    0.905270] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 18
Sep 28 18:04:03 paul-laptop kernel: [    0.905310] PM: Writing back config space on device 0000:05:06.2 at offset 4 (was d0101000, writing d0101400)
Sep 28 18:04:03 paul-laptop kernel: [    0.905355] PM: Writing back config space on device 0000:05:06.3 at offset 4 (was d0101400, writing d0101800)
Sep 28 18:04:03 paul-laptop kernel: [    0.905382] PM: Writing back config space on device 0000:05:06.4 at offset f (was 205, writing 2ff)
Sep 28 18:04:03 paul-laptop kernel: [    0.905405] PM: Writing back config space on device 0000:05:06.4 at offset 4 (was d0101800, writing ffffff00)
Sep 28 18:04:03 paul-laptop kernel: [    0.905415] PM: Writing back config space on device 0000:05:06.4 at offset 1 (was 2100000, writing 2100542)
Sep 28 18:04:03 paul-laptop kernel: [    1.137492] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    1.137496] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    1.309272] ata2.00: configured for UDMA/33
Sep 28 18:04:03 paul-laptop kernel: [    2.311920] sd 0:0:0:0: [sda] Starting disk
Sep 28 18:04:03 paul-laptop kernel: [    2.776818] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    2.776822] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep 28 18:04:03 paul-laptop kernel: [    2.797064] ata1.00: configured for UDMA/100
Sep 28 18:04:03 paul-laptop kernel: [    2.815805] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Sep 28 18:04:03 paul-laptop kernel: [    2.815826] sd 0:0:0:0: [sda] Write Protect is off
Sep 28 18:04:03 paul-laptop kernel: [    2.815829] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 28 18:04:03 paul-laptop kernel: [    2.815848] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 18:04:03 paul-laptop kernel: [    2.831469] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Sep 28 18:04:03 paul-laptop kernel: [    2.832854] PM: Finishing wakeup.
Sep 28 18:04:03 paul-laptop kernel: [    2.832855] Restarting tasks ... <6>usb 1-1: USB disconnect, address 3
Sep 28 18:04:03 paul-laptop kernel: [    2.838409] done.
Sep 28 18:04:03 paul-laptop kernel: [    2.991321] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Sep 28 18:04:03 paul-laptop kernel: [    3.006800] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Sep 28 18:04:03 paul-laptop kernel: [    3.007468] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Sep 28 18:04:03 paul-laptop kernel: [    3.007543] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    3.012832] ndiswrapper: using IRQ 16
Sep 28 18:04:03 paul-laptop kernel: [    3.239103] usb 1-1: new low speed USB device using uhci_hcd and address 4
Sep 28 18:04:03 paul-laptop kernel: [    3.384164] wlan0: ethernet device 00:19:7e:69:11:d1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
Sep 28 18:04:03 paul-laptop kernel: [    3.384884] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Sep 28 18:04:03 paul-laptop kernel: [    3.386757] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Sep 28 18:04:03 paul-laptop kernel: [    3.386881] udev: renamed network interface wlan0 to eth1
Sep 28 18:04:03 paul-laptop kernel: [    3.418220] usb 1-1: configuration #1 chosen from 1 choice
Sep 28 18:04:03 paul-laptop kernel: [    3.420854] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 28 18:04:03 paul-laptop kernel: [    3.435615] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input13
Sep 28 18:04:03 paul-laptop kernel: [    3.483932] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Sep 28 18:04:03 paul-laptop kernel: [    3.484490] usbcore: registered new interface driver ndiswrapper
Sep 28 18:04:03 paul-laptop kernel: [    3.514855] 8139too Fast Ethernet driver 0.9.28
Sep 28 18:04:03 paul-laptop kernel: [    3.514940] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 21
Sep 28 18:04:03 paul-laptop kernel: [    3.516398] eth0: RealTek RTL8139 at 0x2000, 00:0f:b0:d6:72:15, IRQ 21
Sep 28 18:04:03 paul-laptop kernel: [    3.516401] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Sep 28 18:04:03 paul-laptop kernel: [    3.581124] eth0: link down
Sep 28 18:04:03 paul-laptop kernel: [    3.583183] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 18:04:04 paul-laptop kernel: [    4.823953] eth0: link down
Sep 28 18:04:04 paul-laptop kernel: [    4.828042] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 18:04:47 paul-laptop kernel: [   47.095428] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 28 18:05:03 paul-laptop kernel: [   62.975267] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```

debug
```
Sep 28 17:50:05 paul-laptop NetworkManager: <debug> [1222638605.820248] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0_logicaldev_input'). 
Sep 28 18:03:02 paul-laptop NetworkManager: <debug> [1222639382.652035] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_0f_b0_d6_72_15'). 
Sep 28 18:03:02 paul-laptop NetworkManager: <debug> [1222639382.652127] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_19_7e_69_11_d1'). 
Sep 28 18:04:03 paul-laptop kernel: [25381.822253] PM: Preparing system for mem sleep
Sep 28 18:04:03 paul-laptop kernel: [25381.920835] PM: Entering mem sleep
Sep 28 18:04:03 paul-laptop kernel: [25383.111777] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.111953] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.111980] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.131749] ACPI handle has no context!
Sep 28 18:04:03 paul-laptop kernel: [25383.227543] CPU0 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [25383.227545] CPU1 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [25383.344156] CPU0 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [25383.344159]  domain 0: span 01
Sep 28 18:04:03 paul-laptop kernel: [25383.344161]   groups: 01
Sep 28 18:04:03 paul-laptop kernel: [    0.207623] Back to C!
Sep 28 18:04:03 paul-laptop kernel: [    0.208251] CPU0 attaching NULL sched-domain.
Sep 28 18:04:03 paul-laptop kernel: [    0.309762] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Sep 28 18:04:03 paul-laptop kernel: [    0.309780] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00042940 0000c189 00000000 00000000 00000000
Sep 28 18:04:03 paul-laptop kernel: [    0.310268] CPU0 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [    0.310271]  domain 0: span 03
Sep 28 18:04:03 paul-laptop kernel: [    0.310273]   groups: 01 02
Sep 28 18:04:03 paul-laptop kernel: [    0.310276] CPU1 attaching sched-domain:
Sep 28 18:04:03 paul-laptop kernel: [    0.310278]  domain 0: span 03
Sep 28 18:04:03 paul-laptop kernel: [    0.310279]   groups: 02 01
Sep 28 18:04:03 paul-laptop kernel: [    0.311167] APIC error on CPU0: 00(40)
Sep 28 18:04:03 paul-laptop kernel: [    0.314250] Switched to high resolution mode on CPU 1
Sep 28 18:04:03 paul-laptop kernel: [    0.754967] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
Sep 28 18:04:03 paul-laptop kernel: [    0.785368] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Sep 28 18:04:03 paul-laptop kernel: [    0.785406] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785444] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
Sep 28 18:04:03 paul-laptop kernel: [    0.785455] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100107, writing 100507)
Sep 28 18:04:03 paul-laptop kernel: [    0.785498] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785531] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100107, writing 100507)
Sep 28 18:04:03 paul-laptop kernel: [    0.785573] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785588] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785683] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785761] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.785838] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.801316] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.801388] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050500, writing 20090500)
Sep 28 18:04:03 paul-laptop kernel: [    0.801400] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
Sep 28 18:04:03 paul-laptop kernel: [    0.801422] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.817322] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
Sep 28 18:04:03 paul-laptop kernel: [    0.817347] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep 28 18:04:03 paul-laptop kernel: [    0.817452] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
Sep 28 18:04:03 paul-laptop kernel: [    0.817536] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing d0000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817552] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
Sep 28 18:04:03 paul-laptop kernel: [    0.817575] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100103)
Sep 28 18:04:03 paul-laptop kernel: [    0.817685] PM: Writing back config space on device 0000:05:01.0 at offset 3 (was 0, writing 4000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817693] PM: Writing back config space on device 0000:05:01.0 at offset 1 (was 2900007, writing 2900003)
Sep 28 18:04:03 paul-laptop kernel: [    0.817726] PM: Writing back config space on device 0000:05:04.0 at offset f (was 74001ff, writing 5c001ff)
Sep 28 18:04:03 paul-laptop kernel: [    0.817735] PM: Writing back config space on device 0000:05:04.0 at offset e (was 0, writing 28fc)
Sep 28 18:04:03 paul-laptop kernel: [    0.817742] PM: Writing back config space on device 0000:05:04.0 at offset d (was 0, writing 2800)
Sep 28 18:04:03 paul-laptop kernel: [    0.817749] PM: Writing back config space on device 0000:05:04.0 at offset c (was 0, writing 24fc)
Sep 28 18:04:03 paul-laptop kernel: [    0.817758] PM: Writing back config space on device 0000:05:04.0 at offset b (was 0, writing 2400)
Sep 28 18:04:03 paul-laptop kernel: [    0.817764] PM: Writing back config space on device 0000:05:04.0 at offset a (was 0, writing 57fff000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817771] PM: Writing back config space on device 0000:05:04.0 at offset 9 (was 0, writing 54000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817778] PM: Writing back config space on device 0000:05:04.0 at offset 8 (was 0, writing 53fff000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817785] PM: Writing back config space on device 0000:05:04.0 at offset 7 (was 0, writing 50000000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817792] PM: Writing back config space on device 0000:05:04.0 at offset 6 (was 20000000, writing b0090605)
Sep 28 18:04:03 paul-laptop kernel: [    0.817800] PM: Writing back config space on device 0000:05:04.0 at offset 4 (was 0, writing d0102000)
Sep 28 18:04:03 paul-laptop kernel: [    0.817807] PM: Writing back config space on device 0000:05:04.0 at offset 3 (was 24008, writing 2a820)
Sep 28 18:04:03 paul-laptop kernel: [    0.833305] PM: Writing back config space on device 0000:05:06.0 at offset 3 (was 800000, writing 804000)
Sep 28 18:04:03 paul-laptop kernel: [    0.833313] PM: Writing back config space on device 0000:05:06.0 at offset 1 (was 2100000, writing 2100006)
Sep 28 18:04:03 paul-laptop kernel: [    0.905241] PM: Writing back config space on device 0000:05:06.1 at offset 3 (was 800000, writing 804000)
Sep 28 18:04:03 paul-laptop kernel: [    0.905249] PM: Writing back config space on device 0000:05:06.1 at offset 1 (was 2100000, writing 2100006)
Sep 28 18:04:03 paul-laptop kernel: [    0.905310] PM: Writing back config space on device 0000:05:06.2 at offset 4 (was d0101000, writing d0101400)
Sep 28 18:04:03 paul-laptop kernel: [    0.905355] PM: Writing back config space on device 0000:05:06.3 at offset 4 (was d0101400, writing d0101800)
Sep 28 18:04:03 paul-laptop kernel: [    0.905382] PM: Writing back config space on device 0000:05:06.4 at offset f (was 205, writing 2ff)
Sep 28 18:04:03 paul-laptop kernel: [    0.905405] PM: Writing back config space on device 0000:05:06.4 at offset 4 (was d0101800, writing ffffff00)
Sep 28 18:04:03 paul-laptop kernel: [    0.905415] PM: Writing back config space on device 0000:05:06.4 at offset 1 (was 2100000, writing 2100542)
Sep 28 18:04:03 paul-laptop kernel: [    2.815829] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 28 18:04:03 paul-laptop kernel: [    2.832854] PM: Finishing wakeup.
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.822785] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0_logicaldev_input'). 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.835617] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0'). 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.841181] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial'). 
Sep 28 18:04:03 paul-laptop kernel: [    3.007543] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.426360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_19_7e_69_11_d1'). 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.480044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial'). 
Sep 28 18:04:03 paul-laptop kernel: [    3.516401] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.568732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0'). 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.623345] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0f_b0_d6_72_15'). 
Sep 28 18:04:03 paul-laptop NetworkManager: <debug> [1222639443.675355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c044_noserial_if0_logicaldev_input'). 
Sep 28 18:05:22 paul-laptop kernel: [   81.085808] eth1: no IPv6 routers present
```

So, would anyone have any idea why dhclient is keeping my desktop from coming up, and how to prevent that?

---

### Post by pgn674 on 2008-09-28
Oh yeah, I forgot some information. The wireless is turned on and connected when I put it to sleep, and I didn't move the laptop before turning it on again. There is no ethernet cord in the ethernet port. The Ethernet Network Controller is a RTL-8139/8139C/8139C+ from Realtek Semiconductor Co., Ltd. (Lenovo). I've tried using the front switch and using nm-applet to turn off wireless before sleeping, and those tests made no difference in the wake time.

---

### Post by pgn674 on 2008-10-02
A bit more information: I tried plugging in and using an ethernet cord, having both wired and wireless having an IP address before going to sleep. When I woke  up the computer this time, it came up much faster. Also, eth0 is my wired while eth1 is my wireless. So, anybody have any ideas?

---

### Post by pgn674 on 2008-10-02
I tried disabling the wired port using "sudo ifconfig eth0 down", but waking up still took a long time. I checked ifconfig after waking, and it said eth0 was back up.

---

### Post by pgn674 on 2008-10-22
It's not doing it anymore. I think it may be because I went to System > Administration > Network, and either unchecked the wired connection, or disabled its roaming mode. I'll see if this solution sticks.

---

