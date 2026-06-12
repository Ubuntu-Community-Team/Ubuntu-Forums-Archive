---
title: "wireless pretends to be connected after waking up from suspend"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by VitasLoWang on 2014-09-25
I have Ubuntu 14.04 and I work connected to our company wifi. Every time I suspend the computer and next day I wake it up it seems like connected, but nothing works! And it does not ever realize, that the connection is actually not working, thus does not even try to reconnect! I have to manually switch off the wireless and switch it on again to make it get an ip from dhcp and work again. I doubt this is an intended behavior. Maybe I broke it because I installed Cinnamon and there may be some bug in it causing it...? I will test it in Unity when I have time.

---

### Post by praseodym on 2014-09-25
Please show:
```

lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by VitasLoWang on 2014-09-25
```
vitas@T420-vitas:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

```

---

### Post by praseodym on 2014-09-25
This un-/reloads the driver before/after suspend/hibernate:
```

echo 'SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi" ' | sudo tee /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
```

---

### Post by VitasLoWang on 2014-09-25
OK so this is some kind of workaround? I am not sure I get it...
You didn't say this behavior is normal/abnormal in Ubuntu

---

### Post by praseodym on 2014-09-25
Yes. Some modules are not working ootb when waking-up, they need to be un-/reloaded before/afterwards. This is what this file is doing.

---

### Post by VitasLoWang on 2014-09-26
Well... isn't it easier just to click off/on to reconnect as I am doing already? :-]

---

### Post by praseodym on 2014-09-26
This is a "one-timer"

---

### Post by VitasLoWang on 2014-09-28
I am sorry it did not help, just made things more interesting :-] After booting to my Ubuntu, it connects automatically, but when I suspend a machine and wake it up it continuously tries to connect and keeps failing! :( Please check this syslog right after system wakeup if you see something in it which would explain it.
```
Sep 28 19:23:46 T420-vitas wpa_supplicant[1433]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 28 19:23:52 T420-vitas wpa_supplicant[1433]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Sep 28 19:25:46 T420-vitas wpa_supplicant[1433]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 28 19:25:52 T420-vitas wpa_supplicant[1433]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Sep 28 19:26:31 T420-vitas kernel: [ 1191.629823] thinkpad_acpi: EC reports that Thermal Table has changed
Sep 28 19:26:36 T420-vitas kernel: [ 1197.424965] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep 28 19:26:36 T420-vitas kernel: [ 1197.426315] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep 28 19:26:37 T420-vitas kernel: [ 1198.322083] thinkpad_acpi: EC reports that Thermal Table has changed
Sep 28 19:26:39 T420-vitas kernel: [ 1200.078235] thinkpad_acpi: EC reports that Thermal Table has changed
Sep 28 19:26:45 T420-vitas kernel: [ 1206.410058] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep 28 19:26:45 T420-vitas kernel: [ 1206.411529] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep 28 19:26:46 T420-vitas kernel: [ 1207.346468] thinkpad_acpi: EC reports that Thermal Table has changed
Sep 28 19:27:01 T420-vitas cinnamon-session[2178]: WARNING: Unable to determine session: Unable to lookup session information for process '2178'
Sep 28 19:27:04 T420-vitas anacron[4008]: Anacron 2.3 started on 2014-09-28
Sep 28 19:27:04 T420-vitas anacron[4008]: Will run job `cron.daily' in 5 min.
Sep 28 19:27:04 T420-vitas anacron[4008]: Jobs will be executed sequentially
Sep 28 19:27:04 T420-vitas kernel: [ 1225.044241] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Sep 28 19:27:05 T420-vitas kernel: [ 1225.527912] wlan0: deauthenticating from cc:35:40:78:5d:29 by local choice (reason=3)
Sep 28 19:27:05 T420-vitas wpa_supplicant[1433]: wlan0: CTRL-EVENT-DISCONNECTED bssid=cc:35:40:78:5d:29 reason=3 locally_generated=1
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> Connection disconnected (reason -3)
Sep 28 19:27:05 T420-vitas dhclient: receive_packet failed on wlan0: Network is down
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::120b:a9ff:fef7:34dc.
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.18.
Sep 28 19:27:05 T420-vitas acvpnagent[2231]: message repeated 29 times: [ Function: tableCallbackHandler File: RouteMgr.cpp Line: 1723 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown ]
Sep 28 19:27:05 T420-vitas acvpnagent[2231]: A network interface has gone down.
Sep 28 19:27:05 T420-vitas acvpnagent[2231]: Function: logInterfaces File: RouteMgr.cpp Line: 2105 Invoked Function: logInterfaces Return Code: 0 (0x00000000) Description: IP Address Interface List:  
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: IP_DROP_MEMBERSHIP failed: No such device
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Withdrawing address record for fe80::120b:a9ff:fef7:34dc on wlan0.
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Withdrawing address record for 192.168.0.18 on wlan0.
Sep 28 19:27:05 T420-vitas avahi-daemon[953]: Withdrawing workstation service for wlan0.
Sep 28 19:27:05 T420-vitas whoopsie[1299]: offline
Sep 28 19:27:05 T420-vitas kernel: [ 1225.596429] cfg80211: Calling CRDA to update world regulatory domain
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> (wlan0): deactivating device (reason 'removed') [36]
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627929] cfg80211: World regulatory domain updated:
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627932] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627934] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627935] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627937] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627938] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:05 T420-vitas kernel: [ 1225.627940] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1870
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/accept_ra': (2) No such file or directory
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/use_tempaddr': (2) No such file or directory
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> (3) failed to find interface name for index
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <error> [1411925225.318178] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> (3) failed to find interface name for index
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <error> [1411925225.318272] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> (wlan0): bringing up device.
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> (3) failed to find interface name for index
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> (3) failed to find interface name for index
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> DNS: plugin dnsmasq update failed
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> Removing DNS information from /sbin/resolvconf
Sep 28 19:27:05 T420-vitas dnsmasq[3017]: setting upstream servers from DBus
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> (wlan0): cleaning up...
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <warn> (3) failed to find interface name for index
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <error> [1411925225.358101] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 28 19:27:05 T420-vitas NetworkManager[1044]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Sep 28 19:27:05 T420-vitas NetworkManager[1044]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill2 disappeared
Sep 28 19:27:05 T420-vitas dbus[793]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 28 19:27:05 T420-vitas kernel: [ 1225.872055] PM: Syncing filesystems ... done.
Sep 28 19:27:05 T420-vitas kernel: [ 1225.878371] PM: Preparing system for mem sleep
Sep 28 19:27:05 T420-vitas dbus[793]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 28 19:27:05 T420-vitas kernel: [ 1226.268844] thinkpad_acpi: EC reports that Thermal Table has changed
Sep 28 19:27:05 T420-vitas kernel: [ 1226.459803] mmc0: card aaaa removed
Sep 28 19:27:05 T420-vitas udisksd[2681]: Cleaning up mount point /media/vitas/3339-6665 (device 179:1 no longer exist)
Sep 28 19:27:27 T420-vitas kernel: [ 1226.465595] Freezing user space processes ... (elapsed 0.003 seconds) done.
Sep 28 19:27:27 T420-vitas kernel: [ 1226.469519] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Sep 28 19:27:27 T420-vitas kernel: [ 1226.470708] PM: Entering mem sleep
Sep 28 19:27:27 T420-vitas kernel: [ 1226.470759] Suspending console(s) (use no_console_suspend to debug)
Sep 28 19:27:27 T420-vitas kernel: [ 1226.635433] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
Sep 28 19:27:27 T420-vitas kernel: [ 1226.635525] sd 1:0:0:0: [sdb] Stopping disk
Sep 28 19:27:27 T420-vitas kernel: [ 1226.635536] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Sep 28 19:27:27 T420-vitas kernel: [ 1226.636594] sd 0:0:0:0: [sda] Stopping disk
Sep 28 19:27:27 T420-vitas kernel: [ 1226.879578] nouveau  [     DRM] suspending display...
Sep 28 19:27:27 T420-vitas kernel: [ 1226.879594] nouveau  [     DRM] unpinning framebuffer(s)...
Sep 28 19:27:27 T420-vitas kernel: [ 1226.879605] nouveau  [     DRM] evicting buffers...
Sep 28 19:27:27 T420-vitas kernel: [ 1226.879607] nouveau  [     DRM] waiting for kernel channels to go idle...
Sep 28 19:27:27 T420-vitas kernel: [ 1226.879654] nouveau  [     DRM] suspending client object trees...
Sep 28 19:27:27 T420-vitas kernel: [ 1226.880078] nouveau  [     DRM] suspending kernel object tree...
Sep 28 19:27:27 T420-vitas kernel: [ 1227.659477] PM: suspend of devices complete after 1188.980 msecs
Sep 28 19:27:27 T420-vitas kernel: [ 1227.675352] PM: late suspend of devices complete after 15.877 msecs
Sep 28 19:27:27 T420-vitas kernel: [ 1227.675785] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
Sep 28 19:27:27 T420-vitas kernel: [ 1227.691450] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
Sep 28 19:27:27 T420-vitas kernel: [ 1227.739206] PM: noirq suspend of devices complete after 63.873 msecs
Sep 28 19:27:27 T420-vitas kernel: [ 1227.739379] ACPI: Preparing to enter system sleep state S3
Sep 28 19:27:27 T420-vitas kernel: [ 1227.741636] PM: Saving platform NVS memory
Sep 28 19:27:27 T420-vitas kernel: [ 1227.742524] Disabling non-boot CPUs ...
Sep 28 19:27:27 T420-vitas kernel: [ 1227.743783] kvm: disabling virtualization on CPU1
Sep 28 19:27:27 T420-vitas kernel: [ 1227.743978] smpboot: CPU 1 is now offline
Sep 28 19:27:27 T420-vitas kernel: [ 1227.745419] kvm: disabling virtualization on CPU2
Sep 28 19:27:27 T420-vitas kernel: [ 1227.847140] smpboot: CPU 2 is now offline
Sep 28 19:27:27 T420-vitas kernel: [ 1227.847589] Broke affinity for irq 42
Sep 28 19:27:27 T420-vitas kernel: [ 1227.848590] kvm: disabling virtualization on CPU3
Sep 28 19:27:27 T420-vitas kernel: [ 1227.951106] smpboot: CPU 3 is now offline
Sep 28 19:27:27 T420-vitas kernel: [ 1227.953464] ACPI: Low-level resume complete
Sep 28 19:27:27 T420-vitas kernel: [ 1227.953540] PM: Restoring platform NVS memory
Sep 28 19:27:27 T420-vitas kernel: [ 1227.955670] Enabling non-boot CPUs ...
Sep 28 19:27:27 T420-vitas kernel: [ 1227.955753] x86: Booting SMP configuration:
Sep 28 19:27:27 T420-vitas kernel: [ 1227.955756] smpboot: Booting Node 0 Processor 1 APIC 0x1
Sep 28 19:27:27 T420-vitas kernel: [ 1227.967081] Disabled fast string operations
Sep 28 19:27:27 T420-vitas kernel: [ 1227.967186] kvm: enabling virtualization on CPU1
Sep 28 19:27:27 T420-vitas kernel: [ 1227.999385] CPU1 is up
Sep 28 19:27:27 T420-vitas kernel: [ 1227.999443] smpboot: Booting Node 0 Processor 2 APIC 0x2
Sep 28 19:27:27 T420-vitas kernel: [ 1228.010410] Disabled fast string operations
Sep 28 19:27:27 T420-vitas kernel: [ 1228.010508] kvm: enabling virtualization on CPU2
Sep 28 19:27:27 T420-vitas kernel: [ 1228.043378] CPU2 is up
Sep 28 19:27:27 T420-vitas kernel: [ 1228.043441] smpboot: Booting Node 0 Processor 3 APIC 0x3
Sep 28 19:27:27 T420-vitas kernel: [ 1228.054523] Disabled fast string operations
Sep 28 19:27:27 T420-vitas kernel: [ 1228.054622] kvm: enabling virtualization on CPU3
Sep 28 19:27:27 T420-vitas kernel: [ 1228.087368] CPU3 is up
Sep 28 19:27:27 T420-vitas kernel: [ 1228.096330] ACPI: Waking up from system sleep state S3
Sep 28 19:27:27 T420-vitas kernel: [ 1228.243277] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
Sep 28 19:27:27 T420-vitas kernel: [ 1228.275259] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
Sep 28 19:27:27 T420-vitas kernel: [ 1228.323332] sdhci-pci 0000:0d:00.0: MMC controller base frequency changed to 50Mhz.
Sep 28 19:27:27 T420-vitas kernel: [ 1228.323482] PM: noirq resume of devices complete after 156.678 msecs
Sep 28 19:27:27 T420-vitas kernel: [ 1228.323804] PM: early resume of devices complete after 0.278 msecs
Sep 28 19:27:27 T420-vitas kernel: [ 1228.323923] mei_me 0000:00:16.0: irq 41 for MSI/MSI-X
Sep 28 19:27:27 T420-vitas kernel: [ 1228.324093] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Sep 28 19:27:27 T420-vitas kernel: [ 1228.324749] nouveau  [     DRM] re-enabling device...
Sep 28 19:27:27 T420-vitas kernel: [ 1228.324775] nouveau  [     DRM] resuming kernel object tree...
Sep 28 19:27:27 T420-vitas kernel: [ 1228.324791] nouveau  [   VBIOS][0000:01:00.0] running init tables
Sep 28 19:27:27 T420-vitas kernel: [ 1228.325348] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Sep 28 19:27:27 T420-vitas kernel: [ 1228.356263] [drm] Wrong MCH_SSKPD value: 0x16040307
Sep 28 19:27:27 T420-vitas kernel: [ 1228.356264] [drm] This can cause pipe underruns and display issues.
Sep 28 19:27:27 T420-vitas kernel: [ 1228.356265] [drm] Please upgrade your BIOS to fix this.
Sep 28 19:27:27 T420-vitas kernel: [ 1228.379192] tpm_tis 00:09: TPM is disabled/deactivated (0x6)
Sep 28 19:27:27 T420-vitas kernel: [ 1228.535328] usb 1-1.4: reset full-speed USB device number 3 using ehci-pci
Sep 28 19:27:27 T420-vitas kernel: [ 1228.544192] mei_me 0000:00:16.0: hbm: properties response: wrong status = 1
Sep 28 19:27:27 T420-vitas kernel: [ 1228.544205] mei_me 0000:00:16.0: unexpected reset: dev_state = INIT_CLIENTS
Sep 28 19:27:27 T420-vitas kernel: [ 1228.581470] nouveau  [    VOLT][0000:01:00.0] GPU voltage: 850000uv
Sep 28 19:27:27 T420-vitas kernel: [ 1228.581478] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
Sep 28 19:27:27 T420-vitas kernel: [ 1228.581691] nouveau  [     CLK][0000:01:00.0] --: core 270 MHz memory 405 MHz 
Sep 28 19:27:27 T420-vitas kernel: [ 1228.583011] nouveau  [     DRM] resuming client object trees...
Sep 28 19:27:27 T420-vitas kernel: [ 1228.583192] nouveau  [     DRM] resuming display...
Sep 28 19:27:27 T420-vitas kernel: [ 1228.659126] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 28 19:27:27 T420-vitas kernel: [ 1228.659159] ata4: SATA link down (SStatus 0 SControl 300)
Sep 28 19:27:27 T420-vitas kernel: [ 1228.667083] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Sep 28 19:27:27 T420-vitas kernel: [ 1228.667088] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1228.667092] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1228.667138] ata5: SATA link down (SStatus 0 SControl 300)
Sep 28 19:27:27 T420-vitas kernel: [ 1228.687075] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Sep 28 19:27:27 T420-vitas kernel: [ 1228.687080] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1228.687084] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1228.697538] ata1.00: configured for UDMA/133
Sep 28 19:27:27 T420-vitas kernel: [ 1228.699300] usb 1-1.6: reset high-speed USB device number 4 using ehci-pci
Sep 28 19:27:27 T420-vitas kernel: [ 1228.711165] sd 0:0:0:0: [sda] Starting disk
Sep 28 19:27:27 T420-vitas kernel: [ 1228.867220] usb 2-1.5: reset full-speed USB device number 3 using ehci-pci
Sep 28 19:27:27 T420-vitas kernel: [ 1229.422877] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Sep 28 19:27:27 T420-vitas kernel: [ 1230.506630] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 28 19:27:27 T420-vitas kernel: [ 1230.508630] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Sep 28 19:27:27 T420-vitas kernel: [ 1230.508636] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1230.508639] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1230.511782] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Sep 28 19:27:27 T420-vitas kernel: [ 1230.511787] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1230.511791] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Sep 28 19:27:27 T420-vitas kernel: [ 1230.512808] ata2.00: configured for UDMA/100
Sep 28 19:27:27 T420-vitas kernel: [ 1230.526687] sd 1:0:0:0: [sdb] Starting disk
Sep 28 19:27:27 T420-vitas kernel: [ 1230.545379] PM: resume of devices complete after 2222.271 msecs
Sep 28 19:27:27 T420-vitas kernel: [ 1230.546442] PM: Finishing wakeup.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.546446] Restarting tasks ... done.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.591576] video LNXVIDEO:00: Restoring backlight state
Sep 28 19:27:27 T420-vitas kernel: [ 1230.593383] video LNXVIDEO:01: Restoring backlight state
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Adapter /org/bluez/879/hci0 has been disabled
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Unregister path: /org/bluez/879/hci0
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint unregistered: sender=:1.23 path=/MediaEndpoint/A2DPSink
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint unregistered: sender=:1.23 path=/MediaEndpoint/A2DPSource
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint unregistered: sender=:1.23 path=/MediaEndpoint/HFPAG
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint unregistered: sender=:1.23 path=/MediaEndpoint/HFPHS
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Adapter /org/bluez/879/hci0 has been enabled
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint registered: sender=:1.23 path=/MediaEndpoint/HFPAG
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint registered: sender=:1.23 path=/MediaEndpoint/HFPHS
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint registered: sender=:1.23 path=/MediaEndpoint/A2DPSource
Sep 28 19:27:27 T420-vitas bluetoothd[879]: Endpoint registered: sender=:1.23 path=/MediaEndpoint/A2DPSink
Sep 28 19:27:27 T420-vitas bluetoothd[879]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Sep 28 19:27:27 T420-vitas kernel: [ 1230.852513] mmc0: new high speed SDHC card at address aaaa
Sep 28 19:27:27 T420-vitas kernel: [ 1230.862117] mmcblk0: mmc0:aaaa SD08G 7.40 GiB 
Sep 28 19:27:27 T420-vitas kernel: [ 1230.871459] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.871551]  mmcblk0: p1
Sep 28 19:27:27 T420-vitas kernel: [ 1230.877489] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.878194] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.880074] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.882350] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.885488] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.889238] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.890625] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.904565] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.906051] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.909860] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.912178] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.912956] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.914514] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.917630] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.920961] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.928556] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.929356] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.930062] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.930849] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.931663] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.934738] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.937057] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.940941] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.944156] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.962042] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.962788] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.963545] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.964248] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.972137] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.973489] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.974991] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.979558] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.980273] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.981062] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.983292] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.986244] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.987722] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.996902] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1230.999215] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.004624] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.006107] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.006929] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.010886] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.012364] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.013168] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.014757] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.015502] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.017841] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.022495] mmc0: Got command interrupt 0x00000001 even though no command operation was in progress.
Sep 28 19:27:27 T420-vitas anacron[4481]: Anacron 2.3 started on 2014-09-28
Sep 28 19:27:27 T420-vitas anacron[4481]: Will run job `cron.daily' in 5 min.
Sep 28 19:27:27 T420-vitas anacron[4481]: Jobs will be executed sequentially
Sep 28 19:27:27 T420-vitas kernel: [ 1231.206031] cfg80211: Calling CRDA to update world regulatory domain
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209777] cfg80211: World regulatory domain updated:
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209780] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209781] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209782] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209783] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209784] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:27 T420-vitas kernel: [ 1231.209785] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 19:27:27 T420-vitas kernel: [ 1231.227897] Intel(R) Wireless WiFi driver for Linux, in-tree:
Sep 28 19:27:27 T420-vitas kernel: [ 1231.227901] Copyright(c) 2003-2013 Intel Corporation
Sep 28 19:27:27 T420-vitas kernel: [ 1231.228231] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
Sep 28 19:27:27 T420-vitas kernel: [ 1231.228608] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
Sep 28 19:27:27 T420-vitas kernel: [ 1231.229544] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
Sep 28 19:27:27 T420-vitas kernel: [ 1231.241610] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
Sep 28 19:27:27 T420-vitas kernel: [ 1231.241613] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
Sep 28 19:27:27 T420-vitas kernel: [ 1231.241614] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
Sep 28 19:27:27 T420-vitas kernel: [ 1231.241616] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
Sep 28 19:27:27 T420-vitas kernel: [ 1231.241818] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Sep 28 19:27:27 T420-vitas kernel: [ 1231.259864] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Sep 28 19:27:27 T420-vitas NetworkManager[1044]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Sep 28 19:27:27 T420-vitas NetworkManager[1044]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep 28 19:27:27 T420-vitas NetworkManager[1044]: <info> (wlan0): using nl80211 for WiFi device control
Sep 28 19:27:27 T420-vitas NetworkManager[1044]: <info> (wlan0): driver supports Access Point (AP) mode
Sep 28 19:27:27 T420-vitas NetworkManager[1044]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 5)
Sep 28 19:27:27 T420-vitas NetworkManager[1044]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Sep 28 19:27:27 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 28 19:27:27 T420-vitas NetworkManager[1044]: <info> (wlan0): bringing up device.
Sep 28 19:27:27 T420-vitas kernel: [ 1231.292254] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Sep 28 19:27:27 T420-vitas kernel: [ 1231.292492] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Sep 28 19:27:28 T420-vitas kernel: [ 1231.583681] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Sep 28 19:27:28 T420-vitas kernel: [ 1231.583885] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0): preparing device.
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0): deactivating device (reason 'managed') [2]
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> NetworkManager state is now DISCONNECTED
Sep 28 19:27:28 T420-vitas kernel: [ 1231.667320] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 28 19:27:28 T420-vitas kernel: [ 1231.667595] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> rfkill4: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill4) (driver iwlwifi)
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0) supports 5 scan SSIDs
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: starting -> ready
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <warn> Trying to remove a non-existant call id.
Sep 28 19:27:28 T420-vitas wpa_supplicant[1433]: wlan0: Reject scan trigger since one is already pending
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: ready -> disconnected
Sep 28 19:27:28 T420-vitas NetworkManager[1044]: <info> (wlan0) supports 5 scan SSIDs
Sep 28 19:27:33 T420-vitas cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Auto-activating connection 'Auto UPCdecka'.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) starting connection 'Auto UPCdecka'
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> NetworkManager state is now CONNECTING
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0/wireless): access point 'Auto UPCdecka' has security, but secrets are required.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0/wireless): connection 'Auto UPCdecka' has security, and secrets exist.  No new secrets needed.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Config: added 'ssid' value 'UPCdecka'
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Config: added 'scan_ssid' value '1'
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Config: added 'auth_alg' value 'OPEN'
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Config: added 'psk' value '<omitted>'
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> Config: set interface ap_scan to 1
Sep 28 19:27:38 T420-vitas wpa_supplicant[1433]: wlan0: SME: Trying to authenticate with cc:35:40:78:5d:29 (SSID='UPCdecka' freq=2422 MHz)
Sep 28 19:27:38 T420-vitas kernel: [ 1241.770411] wlan0: authenticate with cc:35:40:78:5d:29
Sep 28 19:27:38 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Sep 28 19:27:38 T420-vitas kernel: [ 1241.774897] wlan0: send auth to cc:35:40:78:5d:29 (try 1/3)
Sep 28 19:27:38 T420-vitas kernel: [ 1241.777719] wlan0: authenticated
Sep 28 19:27:40 T420-vitas kernel: [ 1243.598474] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep 28 19:27:40 T420-vitas kernel: [ 1243.599651] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Sep 28 19:27:41 T420-vitas kernel: [ 1244.519575] thinkpad_acpi: EC reports that Thermal Table has changed
Sep 28 19:27:43 T420-vitas kernel: [ 1246.783283] wlan0: deauthenticating from cc:35:40:78:5d:29 by local choice (reason=3)
Sep 28 19:27:43 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 28 19:27:43 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 19:27:53 T420-vitas kernel: [ 1256.889634] wlan0: authenticate with cc:35:40:78:5d:29
Sep 28 19:27:53 T420-vitas kernel: [ 1256.892333] wlan0: send auth to cc:35:40:78:5d:29 (try 1/3)
Sep 28 19:27:53 T420-vitas kernel: [ 1256.895175] wlan0: authenticated
Sep 28 19:27:53 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 28 19:27:58 T420-vitas kernel: [ 1261.891156] wlan0: deauthenticating from cc:35:40:78:5d:29 by local choice (reason=3)
Sep 28 19:27:58 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 28 19:27:58 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <info> NetworkManager state is now DISCONNECTED
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <warn> Activation (wlan0) failed for connection 'Auto UPCdecka'
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep 28 19:27:53 T420-vitas wpa_supplicant[1433]: wlan0: SME: Trying to authenticate with cc:35:40:78:5d:29 (SSID='UPCdecka' freq=2422 MHz)
Sep 28 19:28:03 T420-vitas wpa_supplicant[1433]: wlan0: Reject scan trigger since one is already pending
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Sep 28 19:28:03 T420-vitas NetworkManager[1044]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Auto-activating connection 'Auto UPCdecka'.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) starting connection 'Auto UPCdecka'
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> NetworkManager state is now CONNECTING
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0/wireless): access point 'Auto UPCdecka' has security, but secrets are required.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0/wireless): connection 'Auto UPCdecka' has security, and secrets exist.  No new secrets needed.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Config: added 'ssid' value 'UPCdecka'
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Config: added 'scan_ssid' value '1'
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Config: added 'auth_alg' value 'OPEN'
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Config: added 'psk' value '<omitted>'
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 19:28:06 T420-vitas NetworkManager[1044]: <info> Config: set interface ap_scan to 1
Sep 28 19:28:06 T420-vitas wpa_supplicant[1433]: wlan0: Reject scan trigger since one is already pending
Sep 28 19:28:06 T420-vitas wpa_supplicant[1433]: wlan0: Failed to initiate AP scan
Sep 28 19:28:07 T420-vitas wpa_supplicant[1433]: wlan0: Reject scan trigger since one is already pending
Sep 28 19:28:07 T420-vitas wpa_supplicant[1433]: wlan0: Failed to initiate AP scan
Sep 28 19:28:08 T420-vitas wpa_supplicant[1433]: wlan0: Reject scan trigger since one is already pending
Sep 28 19:28:08 T420-vitas wpa_supplicant[1433]: wlan0: Failed to initiate AP scan
Sep 28 19:28:08 T420-vitas wpa_supplicant[1433]: wlan0: SME: Trying to authenticate with cc:35:40:78:5d:29 (SSID='UPCdecka' freq=2422 MHz)
Sep 28 19:28:08 T420-vitas kernel: [ 1272.395337] wlan0: authenticate with cc:35:40:78:5d:29
Sep 28 19:28:08 T420-vitas kernel: [ 1272.398265] wlan0: send auth to cc:35:40:78:5d:29 (try 1/3)
Sep 28 19:28:08 T420-vitas kernel: [ 1272.401146] wlan0: authenticated
Sep 28 19:28:08 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Sep 28 19:28:13 T420-vitas kernel: [ 1277.409463] wlan0: deauthenticating from cc:35:40:78:5d:29 by local choice (reason=3)
Sep 28 19:28:13 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 28 19:28:14 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 19:28:21 T420-vitas dnsmasq[1794]: no servers found in /var/run/dnsmasq/resolv.conf, will retry
Sep 28 19:28:24 T420-vitas kernel: [ 1288.417689] wlan0: authenticate with cc:35:40:78:5d:29
Sep 28 19:28:24 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 28 19:28:24 T420-vitas kernel: [ 1288.420645] wlan0: send auth to cc:35:40:78:5d:29 (try 1/3)
Sep 28 19:28:24 T420-vitas kernel: [ 1288.423597] wlan0: authenticated
Sep 28 19:28:24 T420-vitas wpa_supplicant[1433]: wlan0: SME: Trying to authenticate with cc:35:40:78:5d:29 (SSID='UPCdecka' freq=2422 MHz)
Sep 28 19:28:29 T420-vitas wpa_supplicant[1433]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="UPCdecka" auth_failures=1 duration=10
Sep 28 19:28:29 T420-vitas kernel: [ 1293.421040] wlan0: deauthenticating from cc:35:40:78:5d:29 by local choice (reason=3)
Sep 28 19:28:29 T420-vitas NetworkManager[1044]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 28 19:28:31 T420-vitas NetworkManager[1044]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep 28 19:28:31 T420-vitas NetworkManager[1044]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep 28 19:28:31 T420-vitas NetworkManager[1044]: <info> NetworkManager state is now DISCONNECTED
```

---

### Post by VitasLoWang on 2014-09-30
so I guess I will have to just comment the line or delete the file until somebody figures it out...

---

### Post by praseodym on 2014-10-02
Try these module parameters:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by VitasLoWang on 2014-10-03
[h=2][FONT=arial][SIZE=2]vitas@T420-vitas:~$ sudo modprobe -rfv iwlwifi
modprobe: FATAL: Module iwlwifi is in use.
even when I disconnect and disable wifi and also use a hardware button to do it :-\[/SIZE][/FONT][/h]

---

### Post by praseodym on 2014-10-03
Reboot then

---

