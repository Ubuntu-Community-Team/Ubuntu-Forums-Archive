---
title: "hibernate"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-03-25
When I hibernate in Ubuntu, the LED light of the laptop still glows. But the hibernation is supposed to mean: Do not consume any power but save the current contents and instead of booting the next time, just resume the previously saved contents. How do I do that?

---

### Post by NightwishFan on 2011-03-25
It is likely your machine does not support hibernate correctly yet. Some machines do not from my experience. My laptop does, but my desktop with a nvidia card will not hibernate or suspend.

---

### Post by RobikShrestha on 2011-03-25
I can hibernate properly with Windows 7

---

### Post by NightwishFan on 2011-03-25
Irrelevant. Windows 7 uses the NT Kernel and has vendor support for your hardware. Ubuntu uses Linux and may or may not have vendor support depending on your hardware. Petition your hardware vendors to engineer Linux drivers.

In this case I would say something is blocking the machine from completely hibernating. The short answer is wait. Newer versions of Ubuntu will bring better hardware support.

Long answer is that you can try to debug the issue, however I really do not feel up to the task. I will help if you are interested in doing so though.

---

### Post by RobikShrestha on 2011-03-25
I am interested if the debugging is not risky. And what is vendor support?

---

### Post by NightwishFan on 2011-03-25
Vender support is the hardware manufacturer giving engineering and drivers for an operating system.

Debugging is not harmful it is just chances are we will not find any worth while information, and even if we do, we will probably not be able to fix it.

What you can do is try to hibernate the machine, and when it fails, reboot and open System -> Administration -> Log File Viewer. You can check the logs called "messages" "syslog" and "dmesg" for information about the failure to hibernate. It might be useful to mark the time the hibernate failed so you know pretty much where to look in the log.

After that post the sections from the log here so us forums members can look up what is wrong.

---

### Post by RobikShrestha on 2011-03-26
messages:

```
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.665143] PM: Syncing filesystems ... done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.670154] Freezing user space processes ... (elapsed 0.00 seconds) done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.671423] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.671503] PM: Shrinking memory...  -done (0 pages freed)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.810633] PM: Freed 0 kbytes in 0.13 seconds (0.00 MB/s)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.810636] Suspending console(s) (use no_console_suspend to debug)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.810953] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.988083] usb 1-2: reset high speed USB device using ehci_hcd and address 2
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.124075] jmb38x_ms 0000:03:00.3: PME# disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.124089] jmb38x_ms 0000:03:00.3: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.140235] sdhci-pci 0000:03:00.0: PME# disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.140248] sdhci-pci 0000:03:00.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.156075] pci 0000:01:00.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.260142] HDA Intel 0000:00:0f.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308185] ahci 0000:00:05.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308196] sis190 0000:00:04.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308337] pata_sis 0000:00:02.5: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.309693] ACPI: Preparing to enter system sleep state S4
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.397035] PM: Saving platform NVS memory
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.397354] Disabling non-boot CPUs ...
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.500023] CPU 1 is now offline
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.500027] SMP alternatives: switching to UP code
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509635] CPU1 is down
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509683] Extended CMOS year: 2000
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509754] PM: Creating hibernation image: 
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] PM: Need to copy 116068 pages
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] PM: Hibernation image created (116068 pages copied)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] Extended CMOS year: 2000
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] Enabling non-boot CPUs ...
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] SMP alternatives: switching to SMP code
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.518951] Booting processor 1 APIC 0x1 ip 0x6000
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] Initializing CPU#1
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] Calibrating delay using timer specific routine.. 4401.02 BogoMIPS (lpj=8802050)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: L2 cache: 2048K
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: Physical Processor ID: 0
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: Processor Core ID: 1
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] mce: CPU supports 6 MCE banks
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU1: Thermal monitoring enabled (TM1)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.610558] CPU1: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz stepping 0a
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624710] CPU1 is up
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624724] ACPI: Waking up from system sleep state S4
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754502] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754530] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754610] ahci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.768130] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.865309] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.880193] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.896194] jmb38x_ms 0000:03:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.951547] sd 0:0:0:0: [sda] Starting disk
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.236076] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.236102] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.244744] ata2.00: configured for UDMA/133
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.255360] ata1.00: configured for UDMA/133
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.537856] phy2: hwaddr 00:25:d3:18:f0:9a, RTL8187BvE V0 + rtl8225z2
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559393] rtl8187: Customer ID is 0x00
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559450] Registered led device: rtl8187-phy2::tx
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559480] Registered led device: rtl8187-phy2::rx
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.619982] Restarting tasks ... done.
Mar 26 14:16:23 suzuki-laptop kernel: [ 7968.802724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 26 14:16:29 suzuki-laptop kernel: [ 7974.832074] eth0: mii ext = 0000.
Mar 26 14:16:29 suzuki-laptop kernel: [ 7974.856042] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Mar 26 14:16:29 suzuki-laptop kernel: [ 7974.856048] eth0: link on 100 Mbps Full Duplex mode.




syslog:

Mar 26 14:16:08 suzuki-laptop wpa_supplicant[1122]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:16:12 suzuki-laptop anacron[3265]: Anacron 2.3 started on 2011-03-26
Mar 26 14:16:12 suzuki-laptop anacron[3265]: Normal exit (0 jobs run)
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  Sleeping...
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): now unmanaged
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 3009
Mar 26 14:16:12 suzuki-laptop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): cleaning up...
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): taking down device.
Mar 26 14:16:12 suzuki-laptop avahi-daemon[866]: Withdrawing address record for 192.168.1.3 on eth0.
Mar 26 14:16:12 suzuki-laptop avahi-daemon[866]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (wlan0): now unmanaged
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37)
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (wlan0): cleaning up...
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (wlan0): taking down device.
Mar 26 14:16:12 suzuki-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Mar 26 14:16:12 suzuki-laptop avahi-daemon[866]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 26 14:16:12 suzuki-laptop avahi-daemon[866]: Withdrawing address record for fe80::290:f5ff:fe8e:b3bf on eth0.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.665130] PM: Marking nosave pages: 0000000000099000 - 0000000000100000
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  Found radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/ieee80211/phy2/rfkill2) (driver <unknown>)
Mar 26 14:16:19 suzuki-laptop acpid: client 1118[0:0] has disconnected
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.665140] PM: Basic memory bitmaps created
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.665143] PM: Syncing filesystems ... done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.670154] Freezing user space processes ... (elapsed 0.00 seconds) done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.671423] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.671503] PM: Shrinking memory...  -done (0 pages freed)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.810633] PM: Freed 0 kbytes in 0.13 seconds (0.00 MB/s)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.810636] Suspending console(s) (use no_console_suspend to debug)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.810953] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Mar 26 14:16:19 suzuki-laptop kernel: [ 7961.988083] usb 1-2: reset high speed USB device using ehci_hcd and address 2
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.124061] ACPI handle has no context!
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.124075] jmb38x_ms 0000:03:00.3: PME# disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.124089] jmb38x_ms 0000:03:00.3: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.124102] ACPI handle has no context!
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.140223] ACPI handle has no context!
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.140235] sdhci-pci 0000:03:00.0: PME# disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.140248] sdhci-pci 0000:03:00.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.140261] ACPI handle has no context!
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.156075] pci 0000:01:00.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.260142] HDA Intel 0000:00:0f.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.260199] ACPI handle has no context!
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308185] ahci 0000:00:05.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308196] sis190 0000:00:04.0: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308268] ata4: port disabled. ignoring.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.308337] pata_sis 0000:00:02.5: PCI INT A disabled
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.309693] ACPI: Preparing to enter system sleep state S4
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.397035] PM: Saving platform NVS memory
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.397354] Disabling non-boot CPUs ...
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.500023] CPU 1 is now offline
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.500027] SMP alternatives: switching to UP code
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509348] CPU0 attaching NULL sched-domain.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509352] CPU1 attaching NULL sched-domain.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509364] CPU0 attaching NULL sched-domain.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509635] CPU1 is down
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509683] Extended CMOS year: 2000
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509754] PM: Creating hibernation image: 
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] PM: Need to copy 116068 pages
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] PM: Normal pages needed: 57493 + 1024 + 56, available pages: 169713
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] PM: Hibernation image created (116068 pages copied)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] CPU0: Thermal LVT vector (0xfa) already installed
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] Extended CMOS year: 2000
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] Enabling non-boot CPUs ...
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.512005] SMP alternatives: switching to SMP code
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.518951] Booting processor 1 APIC 0x1 ip 0x6000
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] Initializing CPU#1
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] Calibrating delay using timer specific routine.. 4401.02 BogoMIPS (lpj=8802050)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: L2 cache: 2048K
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: Physical Processor ID: 0
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU: Processor Core ID: 1
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] mce: CPU supports 6 MCE banks
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] CPU1: Thermal monitoring enabled (TM1)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.509173] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.610558] CPU1: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz stepping 0a
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.610665] CPU0 attaching NULL sched-domain.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.613016] Switched to high resolution mode on CPU 1
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624024] CPU0 attaching sched-domain:
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/ieee80211/phy1/rfkill1 disappeared
Mar 26 14:16:19 suzuki-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/net/wmaster0, iface: wmaster0)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624029]  domain 0: span 0-1 level MC
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624032]   groups: 0 1
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624038] CPU1 attaching sched-domain:
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624041]  domain 0: span 0-1 level MC
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624045]   groups: 1 0
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624710] CPU1 is up
Mar 26 14:16:19 suzuki-laptop kernel: [ 7962.624724] ACPI: Waking up from system sleep state S4
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754422] pci 0000:00:01.0: setting latency timer to 64
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754476] pata_sis 0000:00:02.5: restoring config space at offset 0x1 (was 0x2100001, writing 0x2100005)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754502] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754530] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754539] sis190 0000:00:04.0: setting latency timer to 64
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754590] ahci 0000:00:05.0: restoring config space at offset 0x1 (was 0x2100003, writing 0x2100007)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.754610] ahci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.755018] ata4: port disabled. ignoring.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.768130] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.768140] HDA Intel 0000:00:0f.0: setting latency timer to 64
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.865309] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.865317] pci 0000:01:00.0: setting latency timer to 64
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.880147] sdhci-pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.880193] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.880215] sdhci-pci 0000:03:00.0: setting latency timer to 64
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.896148] jmb38x_ms 0000:03:00.3: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.896194] jmb38x_ms 0000:03:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.896204] jmb38x_ms 0000:03:00.3: setting latency timer to 64
Mar 26 14:16:19 suzuki-laptop kernel: [ 7963.951547] sd 0:0:0:0: [sda] Starting disk
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.236076] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.236102] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.244744] ata2.00: configured for UDMA/133
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.255360] ata1.00: configured for UDMA/133
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.536707] phy2: Selected rate control algorithm 'minstrel'
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.537856] phy2: hwaddr 00:25:d3:18:f0:9a, RTL8187BvE V0 + rtl8225z2
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559393] rtl8187: Customer ID is 0x00
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559450] Registered led device: rtl8187-phy2::tx
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559480] Registered led device: rtl8187-phy2::rx
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559753] PM: writing image.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559757] PM: Cannot find swap device, try swapon -a.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.619982] Restarting tasks ... done.
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.620546] PM: Basic memory bitmaps freed
Mar 26 14:16:19 suzuki-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/net/wmaster0, iface: wmaster0)
Mar 26 14:16:19 suzuki-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Mar 26 14:16:19 suzuki-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0)
Mar 26 14:16:19 suzuki-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8187')
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Mar 26 14:16:19 suzuki-laptop acpid: client connected from 1118[0:0]
Mar 26 14:16:19 suzuki-laptop anacron[3389]: Anacron 2.3 started on 2011-03-26
Mar 26 14:16:19 suzuki-laptop anacron[3389]: Normal exit (0 jobs run)
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  Waking up...
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (eth0): now managed
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (eth0): bringing up device.
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (eth0): preparing device.
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (wlan0): now managed
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Mar 26 14:16:19 suzuki-laptop NetworkManager: <info>  (wlan0): bringing up device.
Mar 26 14:16:20 suzuki-laptop avahi-daemon[866]: Registering new address record for fe80::290:f5ff:fe8e:b3bf on eth0.*.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (wlan0): preparing device.
Mar 26 14:16:23 suzuki-laptop kernel: [ 7968.802724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 26 14:16:23 suzuki-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 26 14:16:23 suzuki-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 26 14:16:23 suzuki-laptop dhclient: All rights reserved.
Mar 26 14:16:23 suzuki-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 26 14:16:23 suzuki-laptop dhclient: 
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  dhclient started with pid 3406
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Mar 26 14:16:23 suzuki-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Mar 26 14:16:23 suzuki-laptop dhclient: Listening on LPF/eth0/00:90:f5:8e:b3:bf
Mar 26 14:16:23 suzuki-laptop dhclient: Sending on   LPF/eth0/00:90:f5:8e:b3:bf
Mar 26 14:16:23 suzuki-laptop dhclient: Sending on   Socket/fallback
Mar 26 14:16:25 suzuki-laptop dhclient: DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
Mar 26 14:16:25 suzuki-laptop dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Mar 26 14:16:25 suzuki-laptop dhclient: bound to 192.168.1.3 -- renewal in 109146 seconds.
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>    address 192.168.1.3
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>    gateway 192.168.1.1
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>    hostname 'dhcppc1'
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>    nameserver '192.168.1.1'
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 26 14:16:25 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 26 14:16:25 suzuki-laptop avahi-daemon[866]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
Mar 26 14:16:25 suzuki-laptop avahi-daemon[866]: New relevant interface eth0.IPv4 for mDNS.
Mar 26 14:16:25 suzuki-laptop avahi-daemon[866]: Registering new address record for 192.168.1.3 on eth0.IPv4.
Mar 26 14:16:25 suzuki-laptop wpa_supplicant[1122]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:16:26 suzuki-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 26 14:16:26 suzuki-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 26 14:16:26 suzuki-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 26 14:16:26 suzuki-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 26 14:16:28 suzuki-laptop ntpdate[3528]: adjust time server 91.189.94.4 offset -0.096256 sec
Mar 26 14:16:29 suzuki-laptop kernel: [ 7974.832074] eth0: mii ext = 0000.
Mar 26 14:16:29 suzuki-laptop kernel: [ 7974.856042] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Mar 26 14:16:29 suzuki-laptop kernel: [ 7974.856048] eth0: link on 100 Mbps Full Duplex mode.
Mar 26 14:16:29 suzuki-laptop kernel: [ 7975.056027] eth0: no IPv6 routers present
Mar 26 14:16:31 suzuki-laptop wpa_supplicant[1122]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:16:51 suzuki-laptop wpa_supplicant[1122]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:17:04 suzuki-laptop CRON[3550]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 26 14:17:21 suzuki-laptop wpa_supplicant[1122]: CTRL-EVENT-SCAN-RESULTS
```

---

### Post by NightwishFan on 2011-03-26
Someone posted a bug similar (but with suspend instead of hibernate) to your results. The line in red caught my interest.

> Sometimes, my Eee PC 1000HG fails to suspend and I get:

[130899.106047] sd 0:0:0:0: [sda] Stopping disk
[COLOR="Red"][130899.971193] ACPI handle has no context![/COLOR]
[130899.971205] ACPI handle has no context!
[130899.984470] ata_piix 0000:00:1f.2: PCI INT B disabled
[130900.000260] hcd_pci_suspend(): ehci_pci_suspend+0x0/0x6f [ehci_hcd] returns -22
[130900.000305] pci_pm_suspend(): hcd_pci_suspend+0x0/0x6c [usbcore] returns -22
[130900.000324] pm_op(): pci_pm_suspend+0x0/0xc1 returns -22
[130900.000335] PM: Device 0000:00:1d.7 failed to suspend: error -22
[130900.000342] PM: Some devices failed to suspend

He stated running a command in a terminal solved the issue however I do not think it will in your case. As I said, likely we will need to just "wait for hardware support to improve" in a later Ubuntu.

Edit: This line caught my interest.
```
Mar 26 14:16:19 suzuki-laptop kernel: [ 7964.559757] PM: Cannot find swap device, try swapon -a.
```

Can you open a terminal, type this command and post the output here?
```
free -m
```

---

### Post by RobikShrestha on 2011-03-26
total       used       free     shared    buffers     cached
Mem:          2895        447       2447          0         38        180
-/+ buffers/cache:        228       2667
Swap:            0          0          0

---

### Post by NightwishFan on 2011-03-26
Ah! We figured it out. You need a swap partition to be able to hibernate on Ubuntu. Are you using Wubi (windows installer) or a full Ubuntu dual boot?

---

### Post by RobikShrestha on 2011-03-26
I am using a full ubuntu dual boot

---

### Post by NightwishFan on 2011-03-26
You will have to boot from a live cd and add a small (2gb) partition and create a linux swap on it. Then add it to the /etc/fstab on your installed system (if it does not automatically detect it, which I think it does not)

---

### Post by RobikShrestha on 2011-03-26
I do not have a live CD, can i do with a live usb. I do not have iso file, can I make a live usb then? or is there another way to create partition and add to fstab?

---

### Post by TroN-0074 on 2011-03-26
you can go to system>preferences>Power manager and select when the lid is close, Blank Screen, put computer to sleep, Never and put display to sleep, Never. That is kind of a quick fix.
Good Luck to you.

---

### Post by NightwishFan on 2011-03-26
No, generally it is only safe to do partition operations from a live cd/usb.

---

### Post by RobikShrestha on 2011-03-27
If I do not have an iso file can I still make a live USB? If I take out a partition from say G: (from Windows), can I merge it to main drive of ubuntu and then use it for hibernation or should it be a separate drive?

---

### Post by NightwishFan on 2011-03-27
I am not sure what you mean. All you need is a new linux swap partition at least the size of your ram. It is possible to use a swap file but not for hibernation without complicated workarounds (at least last time I checked). If making a swap partition requires moving around partitions already in place you will likely a live cd/usb to do so as partitions in use are not safe to re-size.

---

### Post by mikewhatever on 2011-03-27
Here is a neat walk through on how to create a swap file.
[http://distrowatch.com/weekly.php?issue=20110117#qa](http://distrowatch.com/weekly.php?issue=20110117#qa)

While it involves command line trickery, the steps are pretty straight forward, and no live cd/usb is required.

---

