---
title: "Intel e1000e not working after resume from suspend."
date: 2017-04-06
forum: Networking &amp; Wireless
---

### Post by goatboy73 on 2017-04-06
Hi, all!

My motherboard is an ASUS Rampage V Extreme/U3.1, and everything had worked (nearly) flawlessly until about 2 weeks ago.  The issue in play has to do with a software change that I've been unable to pin down.  Basically, the problem is that when the computer resumes from a successful, the networking device will not communicate with the network properly.  A reboot fixes the issue.

The problem doesn't appear to be hardware-related since there's very strange behavior afoot.  Apropos, a ping sample:

```

(.... more successful pings preceding)
64 bytes from 192.168.3.253: icmp_seq=235 ttl=64 time=0.602 ms    <-- Last ping viewed live on-screen when suspend triggered
64 bytes from 192.168.3.253: icmp_seq=236 ttl=64 time=0.584 ms
64 bytes from 192.168.3.253: icmp_seq=237 ttl=64 time=0.616 ms
64 bytes from 192.168.3.253: icmp_seq=238 ttl=64 time=0.604 ms    <-- Suspend point
(resume triggered)
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.3.253: icmp_seq=244 ttl=64 time=0.500 ms    <-- Already resuming...all looks OK...
64 bytes from 192.168.3.253: icmp_seq=245 ttl=64 time=0.502 ms
64 bytes from 192.168.3.253: icmp_seq=246 ttl=64 time=0.518 ms
64 bytes from 192.168.3.253: icmp_seq=247 ttl=64 time=0.517 ms
64 bytes from 192.168.3.253: icmp_seq=248 ttl=64 time=0.608 ms
64 bytes from 192.168.3.253: icmp_seq=249 ttl=64 time=0.524 ms
64 bytes from 192.168.3.253: icmp_seq=250 ttl=64 time=0.459 ms
64 bytes from 192.168.3.253: icmp_seq=251 ttl=64 time=0.495 ms
64 bytes from 192.168.3.253: icmp_seq=252 ttl=64 time=0.500 ms
64 bytes from 192.168.3.253: icmp_seq=253 ttl=64 time=0.515 ms
64 bytes from 192.168.3.253: icmp_seq=254 ttl=64 time=0.624 ms
64 bytes from 192.168.3.253: icmp_seq=255 ttl=64 time=0.545 ms
ping: sendmsg: Network is unreachable                              <-- ??? WTF???
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.3.253: icmp_seq=261 ttl=64 time=0.884 ms     <-- ???? WTF x 2?
From 192.168.1.1 icmp_seq=310 Destination Host Unreachable         <-- ??? WTF x 2 ^ WTF?
From 192.168.1.1 icmp_seq=311 Destination Host Unreachable
From 192.168.1.1 icmp_seq=312 Destination Host Unreachable
From 192.168.1.1 icmp_seq=313 Destination Host Unreachable
From 192.168.1.1 icmp_seq=314 Destination Host Unreachable
(... same message repeated ad infinitum...)

```


A similar scenario can be viewed from an external machine pinging the box as it goes down and comes back up.  Inspecting the traffic, removing the module (with rmmod or modprobe -r) and reinstalling it (via modprobe) has no effect in resetting its functionality.  Apparently, it does execute the DHCP request properly (as viewed from the DHCP server), but after that it seems to have difficulty resolving ARP requests, which would obviously lead to problems in achieving connectivity.

Interestingly enough, switching to a static IP has no effect.  Windows has no problems going down and back up.  I tried to test with a "pristine" Ubuntu version (i.e. from USB) but I'm having problems due to 16.10 not supporting the GTX 1080 (nomodeset isn't working, and nouveau doesn't seem to support the chipset).

I guess the bigger issue here is that I'm drawing a blank as to where to look to find leads for the problem.  There's no obvious culprit in the logs, and to the local O/S everything seems kosher - with the exception that there's no connectivity with the outside world.  As I mentioned, everything worked flawlessly until a couple of weeks ago.  Sadly, I'm very liberal with updates so it's going to be very difficult to investigate which specific software update messed up the works for me.

That said, I'm fairly technical and relatively knowledgeable as a Linux admin, so I'll be happy to provide any additional info you might need.

Any help will be greatly appreciated, and I'll be happy to help debug the issue!

---

### Post by goatboy73 on 2017-04-06
Forgot to add: I tried disabling the module manually pre-suspend, and re-enabling post, and had no effect either: still borked somehow.  It would appear that it's something in the networking stack that's actually getting borked by the resume operation, judging by the ping working, then failing, then working, then failing (during my other tests) while the computer is resuming...

---

### Post by goatboy73 on 2017-04-06
Further, here's the output from dmesg, starting from the moment "systemctl suspend" is invoked all the way back until the resume is "complete":

```

[  104.972043] PM: Syncing filesystems ... done.
[  104.993830] PM: Preparing system for sleep (mem)
[  105.217100] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 0
[  105.298193] Freezing user space processes ... (elapsed 0.002 seconds) done.
[  105.300770] Double checking all user space processes after OOM killer disable... (elapsed 0.000 seconds)
[  105.300936] Freezing remaining freezable tasks ... (elapsed 1.335 seconds) done.
[  106.636605] PM: Suspending system (mem)
[  106.636629] Suspending console(s) (use no_console_suspend to debug)
[  106.637525] sd 7:0:0:0: [sdd] Synchronizing SCSI cache
[  106.637649] sd 6:0:0:0: [sdc] Synchronizing SCSI cache
[  106.637734] sd 5:0:0:0: [sdb] Synchronizing SCSI cache
[  106.637811] sd 4:0:0:0: [sda] Synchronizing SCSI cache
[  106.638304] sd 5:0:0:0: [sdb] Stopping disk
[  106.638359] sd 4:0:0:0: [sda] Stopping disk
[  106.639353] sd 7:0:0:0: [sdd] Stopping disk
[  106.639548] sd 6:0:0:0: [sdc] Stopping disk
[  106.661254] e1000e: EEE TX LPI TIMER: 00000011
[  106.741127] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 25
[  106.789118] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 1
[  107.294111] PM: suspend of devices complete after 657.002 msecs
[  107.295637] PM: late suspend of devices complete after 1.523 msecs
[  107.296912] e1000e 0000:00:19.0: System wakeup enabled by ACPI
[  107.296932] pcieport 0000:00:1c.6: System wakeup enabled by ACPI
[  107.333103] PM: noirq suspend of devices complete after 37.462 msecs
[  107.333939] ACPI: Preparing to enter system sleep state S3
[  107.541328] ACPI : EC: EC stopped
[  107.541329] PM: Saving platform NVS memory
[  107.541682] Disabling non-boot CPUs ...
[  107.543572] smpboot: CPU 1 is now offline
[  107.559699] smpboot: CPU 2 is now offline
[  107.587221] smpboot: CPU 3 is now offline
[  107.603777] smpboot: CPU 4 is now offline
[  107.631867] smpboot: CPU 5 is now offline
[  107.658463] Broke affinity for irq 34
[  107.659531] smpboot: CPU 6 is now offline
[  107.682222] Broke affinity for irq 23
[  107.682225] Broke affinity for irq 25
[  107.682230] Broke affinity for irq 28
[  107.682242] Broke affinity for irq 34
[  107.682247] Broke affinity for irq 37
[  107.683302] smpboot: CPU 7 is now offline
[  107.698497] Broke affinity for irq 23
[  107.698500] Broke affinity for irq 25
[  107.698505] Broke affinity for irq 28
[  107.698508] Broke affinity for irq 29
[  107.698510] Broke affinity for irq 30
[  107.698519] Broke affinity for irq 34
[  107.698525] Broke affinity for irq 37
[  107.698529] Broke affinity for irq 39
[  107.699567] smpboot: CPU 8 is now offline
[  107.730404] Broke affinity for irq 23
[  107.730408] Broke affinity for irq 25
[  107.730412] Broke affinity for irq 28
[  107.730414] Broke affinity for irq 29
[  107.730416] Broke affinity for irq 30
[  107.730422] Broke affinity for irq 33
[  107.730425] Broke affinity for irq 34
[  107.730429] Broke affinity for irq 36
[  107.730431] Broke affinity for irq 37
[  107.730435] Broke affinity for irq 39
[  107.730440] Broke affinity for irq 53
[  107.731472] smpboot: CPU 9 is now offline
[  107.754378] Broke affinity for irq 23
[  107.754381] Broke affinity for irq 25
[  107.754386] Broke affinity for irq 28
[  107.754388] Broke affinity for irq 29
[  107.754391] Broke affinity for irq 30
[  107.754393] Broke affinity for irq 31
[  107.754396] Broke affinity for irq 32
[  107.754399] Broke affinity for irq 33
[  107.754401] Broke affinity for irq 34
[  107.754406] Broke affinity for irq 36
[  107.754408] Broke affinity for irq 37
[  107.754412] Broke affinity for irq 39
[  107.754416] Broke affinity for irq 42
[  107.754420] Broke affinity for irq 53
[  107.755465] smpboot: CPU 10 is now offline
[  107.778192] Broke affinity for irq 1
[  107.778197] Broke affinity for irq 8
[  107.778199] Broke affinity for irq 9
[  107.778203] Broke affinity for irq 12
[  107.778206] Broke affinity for irq 16
[  107.778210] Broke affinity for irq 23
[  107.778213] Broke affinity for irq 25
[  107.778216] Broke affinity for irq 26
[  107.778219] Broke affinity for irq 28
[  107.778221] Broke affinity for irq 29
[  107.778224] Broke affinity for irq 30
[  107.778226] Broke affinity for irq 31
[  107.778229] Broke affinity for irq 32
[  107.778232] Broke affinity for irq 33
[  107.778235] Broke affinity for irq 34
[  107.778237] Broke affinity for irq 35
[  107.778240] Broke affinity for irq 36
[  107.778242] Broke affinity for irq 37
[  107.778245] Broke affinity for irq 38
[  107.778247] Broke affinity for irq 39
[  107.778250] Broke affinity for irq 42
[  107.778254] Broke affinity for irq 53
[  107.778257] Broke affinity for irq 54
[  107.779291] smpboot: CPU 11 is now offline
[  107.800435] ACPI: Low-level resume complete
[  107.800473] ACPI : EC: EC started
[  107.800473] PM: Restoring platform NVS memory
[  107.801147] Enabling non-boot CPUs ...
[  107.824618] x86: Booting SMP configuration:
[  107.824618] smpboot: Booting Node 0 Processor 1 APIC 0x2
[  107.827388] TSC synchronization [CPU#0 -> CPU#1]:
[  107.827388] Measured 15090337639 cycles TSC warp between CPUs, turning off TSC clock.
[  107.827393] tsc: Marking TSC unstable due to check_tsc_sync_source failed
[  112.141470]  cache: parent cpu1 should not be sleeping
[  107.827706] CPU1 is up
[  107.868672] smpboot: Booting Node 0 Processor 2 APIC 0x4
[  112.183400]  cache: parent cpu2 should not be sleeping
[  107.869645] CPU2 is up
[  107.892687] smpboot: Booting Node 0 Processor 3 APIC 0x6
[  112.207361]  cache: parent cpu3 should not be sleeping
[  107.893616] CPU3 is up
[  107.916698] smpboot: Booting Node 0 Processor 4 APIC 0x8
[  112.231344]  cache: parent cpu4 should not be sleeping
[  107.917610] CPU4 is up
[  107.940716] smpboot: Booting Node 0 Processor 5 APIC 0xa
[  112.255341]  cache: parent cpu5 should not be sleeping
[  107.941621] CPU5 is up
[  107.964685] smpboot: Booting Node 0 Processor 6 APIC 0x1
[  112.279470]  cache: parent cpu6 should not be sleeping
[  107.965765] CPU6 is up
[  107.988729] smpboot: Booting Node 0 Processor 7 APIC 0x3
[  112.303374]  cache: parent cpu7 should not be sleeping
[  107.989679] CPU7 is up
[  108.012706] smpboot: Booting Node 0 Processor 8 APIC 0x5
[  112.327349]  cache: parent cpu8 should not be sleeping
[  108.013868] CPU8 is up
[  108.036727] smpboot: Booting Node 0 Processor 9 APIC 0x7
[  112.351369]  cache: parent cpu9 should not be sleeping
[  108.037931] CPU9 is up
[  108.060744] smpboot: Booting Node 0 Processor 10 APIC 0x9
[  112.375389]  cache: parent cpu10 should not be sleeping
[  108.061968] CPU10 is up
[  108.084773] smpboot: Booting Node 0 Processor 11 APIC 0xb
[  112.399424]  cache: parent cpu11 should not be sleeping
[  108.085808] CPU11 is up
[    0.008000] ACPI: Waking up from system sleep state S3
[  112.349036] clocksource: Switched to clocksource hpet
[  112.349726] pcieport 0000:00:1c.6: System wakeup disabled by ACPI
[  112.349726] PM: noirq resume of devices complete after 37.485 msecs
[  112.349726] PM: early resume of devices complete after 1.083 msecs
[  112.349726] e1000e 0000:00:19.0: System wakeup disabled by ACPI
[  112.349726] usb usb3: root hub lost power or was reset
[  112.349726] usb usb4: root hub lost power or was reset
[  112.349726] usb usb1: root hub lost power or was reset
[  112.349726] usb usb2: root hub lost power or was reset
[  112.349726] rtc_cmos 00:00: System wakeup disabled by ACPI
[  112.349726] sd 4:0:0:0: [sda] Starting disk
[  112.349726] sd 5:0:0:0: [sdb] Starting disk
[  112.349726] sd 6:0:0:0: [sdc] Starting disk
[  112.349726] sd 7:0:0:0: [sdd] Starting disk
[  112.349726] usb 2-5: reset SuperSpeed USB device number 2 using xhci_hcd
[  112.349726] ata3: SATA link down (SStatus 0 SControl 300)
[  112.349726] ata1: SATA link down (SStatus 0 SControl 300)
[  112.349726] ata2: SATA link down (SStatus 0 SControl 300)
[  112.349726] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  112.349726] ata4.00: configured for UDMA/100
[  112.349726] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  112.349726] ata10: SATA link down (SStatus 0 SControl 300)
[  112.349726] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  112.349726] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  112.349726] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  112.349726] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata7.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata7.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata7.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata8.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata8.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata8.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata7.00: supports DRM functions and may not be fully accessible
[  112.349726] ata8.00: supports DRM functions and may not be fully accessible
[  112.349726] ata7.00: NCQ Send/Recv Log not supported
[  112.349726] ata7.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata7.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata7.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata7.00: supports DRM functions and may not be fully accessible
[  112.349726] ata7.00: NCQ Send/Recv Log not supported
[  112.349726] ata7.00: configured for UDMA/133
[  112.349726] ata8.00: NCQ Send/Recv Log not supported
[  112.349726] ata8.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata8.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata8.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata8.00: supports DRM functions and may not be fully accessible
[  112.349726] ata8.00: NCQ Send/Recv Log not supported
[  112.349726] ata8.00: configured for UDMA/133
[  112.349726] ata6.00: NCQ Send/Recv Log not supported
[  112.349726] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata6.00: NCQ Send/Recv Log not supported
[  112.349726] ata6.00: configured for UDMA/133
[  112.349726] ata9: SATA link down (SStatus 0 SControl 300)
[  112.349726] ata5.00: NCQ Send/Recv Log not supported
[  112.349726] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  112.349726] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  112.349726] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  112.349726] ata5.00: NCQ Send/Recv Log not supported
[  112.349726] ata5.00: configured for UDMA/133
[  112.349726] usb 2-6: reset SuperSpeed USB device number 3 using xhci_hcd
[  112.349726] ata6.00: Enabling discard_zeroes_data
[  112.349726] usb 4-1: reset SuperSpeed USB device number 2 using xhci_hcd
[  112.349726] ata5.00: Enabling discard_zeroes_data
[  112.349726] usb 1-7: reset full-speed USB device number 3 using xhci_hcd
[  112.349726] usb 3-1: reset high-speed USB device number 2 using xhci_hcd
[  112.349726] usb 4-1.1: reset SuperSpeed USB device number 3 using xhci_hcd
[  112.349726] usb 1-5: reset low-speed USB device number 2 using xhci_hcd
[  112.349726] usb 3-1.1: reset high-speed USB device number 3 using xhci_hcd
[  112.349726] usb 3-1.2: reset high-speed USB device number 4 using xhci_hcd
[  112.349726] usb 1-14: reset full-speed USB device number 8 using xhci_hcd
[  112.349726] usb 4-1.1.4: reset SuperSpeed USB device number 4 using xhci_hcd
[  112.349726] usb 1-9: reset high-speed USB device number 4 using xhci_hcd
[  112.349726] usb 3-1.1.4: reset high-speed USB device number 5 using xhci_hcd
[  112.349726] usb 1-10: reset high-speed USB device number 5 using xhci_hcd
[  112.349726] usb 1-11: reset full-speed USB device number 6 using xhci_hcd
[  112.349726] usb 1-10.1: reset full-speed USB device number 7 using xhci_hcd
[  112.349726] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  112.349726] usb 1-10.3: reset low-speed USB device number 9 using xhci_hcd
[  112.349726] PM: resume of devices complete after 3873.319 msecs
[  112.349726] PM: Finishing wakeup.
[  112.349726] Restarting tasks ... done.
[  112.444058] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 5
[  112.949794] e1000e: eno1 NIC Link is Down
[  112.962010] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  113.152167] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  116.530119] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  116.530159] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[  117.806231] systemd[1]: apt-daily.timer: Adding 2h 20min 25.421707s random time.
[  129.091459] systemd[1]: apt-daily.timer: Adding 3h 38min 27.399488s random time.

```

---

### Post by lauricat on 2018-01-10
Did you have any resolution to this?

I am running another # ASUS M/B with e1000e intel.

I am running 16.04 MATE with all the updates.

Exact same problem..

---

