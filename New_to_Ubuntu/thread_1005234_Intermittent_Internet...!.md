---
title: "Intermittent Internet...!"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by hopelessone on 2008-12-08
HI All,

I can only use my computer for about 5 mins before i have to unplug the modem or reboot. This has only started since 3 days ago..

i found this in the logs..

> Dec  8 15:29:03 some-one kernel: [ 2025.816023] ------------[ cut here ]------------
Dec  8 15:29:03 some-one kernel: [ 2025.816033] WARNING: at /build/buildd/linux-2.6.27/net/sched/sch_generic.c:219 dev_watchdog+0x272/0x280()
Dec  8 15:29:03 some-one kernel: [ 2025.816036] NETDEV WATCHDOG: eth1 (rndis_host): transmit timed out
Dec  8 15:29:03 some-one kernel: [ 2025.816039] Modules linked in: af_packet ipv6 binfmt_misc i915 drm vboxdrv ppdev acpi_cpufreq cpufreq_userspace cpufreq_powersave cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table sbs pci_slot video output container wmi sbshc battery iptable_filter ip_tables x_tables ac lp serio_raw psmouse evdev snd_hda_intel pcspkr iTCO_wdt iTCO_vendor_support snd_pcm_oss rndis_wlan snd_mixer_oss rndis_host cdc_ether snd_pcm usbnet snd_seq_dummy mii atl2 snd_seq_oss parport_pc snd_seq_midi parport snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc button intel_agp shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_acpi sd_mod crc_t10dif sg ata_piix pata_sil680 ata_generic libata scsi_mod ehci_hcd dock uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Dec  8 15:29:03 some-one kernel: [ 2025.816140] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
Dec  8 15:29:03 some-one kernel: [ 2025.816143] 
Dec  8 15:29:03 some-one kernel: [ 2025.816144] Call Trace:
Dec  8 15:29:03 some-one kernel: [ 2025.816147]  <IRQ>  [<ffffffff8024e91c>] warn_slowpath+0xbc/0xf0
Dec  8 15:29:03 some-one kernel: [ 2025.816158]  [<ffffffff80494600>] ? ip_finish_output+0x120/0x2f0
Dec  8 15:29:03 some-one kernel: [ 2025.816163]  [<ffffffff8049483a>] ? ip_output+0x6a/0xc0
Dec  8 15:29:03 some-one kernel: [ 2025.816167]  [<ffffffff804935c5>] ? ip_local_out+0x25/0x40
Dec  8 15:29:03 some-one kernel: [ 2025.816171]  [<ffffffff80493e3c>] ? ip_queue_xmit+0x1ec/0x3b0
Dec  8 15:29:03 some-one kernel: [ 2025.816177]  [<ffffffff8045cedc>] ? __alloc_skb+0x7c/0x160
Dec  8 15:29:03 some-one kernel: [ 2025.816182]  [<ffffffff8045b919>] ? __copy_skb_header+0x9/0x1d0
Dec  8 15:29:03 some-one kernel: [ 2025.816187]  [<ffffffff8025a84b>] ? lock_timer_base+0x3b/0x70
Dec  8 15:29:03 some-one kernel: [ 2025.816191]  [<ffffffff8025ab44>] ? __mod_timer+0xc4/0xe0
Dec  8 15:29:03 some-one kernel: [ 2025.816197]  [<ffffffff80273ff4>] ? timer_stats_update_stats+0x24/0x370
Dec  8 15:29:03 some-one kernel: [ 2025.816202]  [<ffffffff804ac350>] ? tcp_write_timer+0x0/0x220
Dec  8 15:29:03 some-one kernel: [ 2025.816206]  [<ffffffff803a89ea>] ? strlcpy+0x4a/0x60
Dec  8 15:29:03 some-one kernel: [ 2025.816211]  [<ffffffff8047ba22>] dev_watchdog+0x272/0x280
Dec  8 15:29:03 some-one kernel: [ 2025.816215]  [<ffffffff8026cf5c>] ? sched_clock_cpu+0xcc/0x160
Dec  8 15:29:03 some-one kernel: [ 2025.816219]  [<ffffffff8047b7b0>] ? dev_watchdog+0x0/0x280
Dec  8 15:29:03 some-one kernel: [ 2025.816223]  [<ffffffff8025a019>] run_timer_softirq+0x179/0x260
Dec  8 15:29:03 some-one kernel: [ 2025.816228]  [<ffffffff802717b4>] ? clockevents_program_event+0x54/0xa0
Dec  8 15:29:03 some-one kernel: [ 2025.816233]  [<ffffffff80254d8c>] __do_softirq+0x8c/0x100
Dec  8 15:29:03 some-one kernel: [ 2025.816238]  [<ffffffff8021417c>] call_softirq+0x1c/0x30
Dec  8 15:29:03 some-one kernel: [ 2025.816242]  [<ffffffff80215875>] do_softirq+0x65/0xa0
Dec  8 15:29:03 some-one kernel: [ 2025.816246]  [<ffffffff80254af5>] irq_exit+0x95/0xa0
Dec  8 15:29:03 some-one kernel: [ 2025.816252]  [<ffffffff802268f9>] smp_apic_timer_interrupt+0x89/0xc0
Dec  8 15:29:03 some-one kernel: [ 2025.816256]  [<ffffffff80213983>] apic_timer_interrupt+0x83/0x90
Dec  8 15:29:03 some-one kernel: [ 2025.816259]  <EOI>  [<ffffffff8021ab82>] ? mwait_idle+0x52/0x60
Dec  8 15:29:03 some-one kernel: [ 2025.816267]  [<ffffffff8021ab39>] ? mwait_idle+0x9/0x60
Dec  8 15:29:03 some-one kernel: [ 2025.816273]  [<ffffffff80210e95>] ? cpu_idle+0x75/0x110
Dec  8 15:29:03 some-one kernel: [ 2025.816278]  [<ffffffff804f0536>] ? rest_init+0x66/0x70
Dec  8 15:29:03 some-one kernel: [ 2025.816281] 
Dec  8 15:29:03 some-one kernel: [ 2025.816283] ---[ end trace 6dc033106def88f3 ]---
Dec  8 15:33:27 some-one kernel: [ 2289.820429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input7
Dec  8 15:39:01 some-one kernel: [ 2623.586907] atl2: eth0 NIC Link is Down
Dec  8 15:39:04 some-one kernel: [ 2626.623248] usb 5-3: USB disconnect, address 2
Dec  8 15:39:04 some-one kernel: [ 2626.624796] eth1: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
Dec  8 15:39:09 some-one kernel: [ 2631.700089] usb 5-3: new high speed USB device using ehci_hcd and address 3
Dec  8 15:39:09 some-one kernel: [ 2631.834278] usb 5-3: configuration #1 chosen from 2 choices
Dec  8 15:39:09 some-one kernel: [ 2631.870955] eth1: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 00:02:00:dc:19:05
Dec  8 15:39:12 some-one kernel: [ 2634.458928] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 15:39:24 some-one kernel: [ 2646.140008] eth1: no IPv6 routers present
Dec  8 15:40:07 some-one kernel: [ 2689.930529] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 15:40:07 some-one kernel: [ 2689.931712] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  8 15:40:07 some-one kernel: [ 2689.932910] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec  8 15:40:18 some-one kernel: [ 2700.260010] eth0: no IPv6 routers present
Dec  8 15:40:18 some-one kernel: [ 2700.464009] eth1: no IPv6 routers present
Dec  8 15:44:30 some-one kernel: [ 2952.922191] usb 5-3: USB disconnect, address 3
Dec  8 15:44:30 some-one kernel: [ 2952.922468] atl2: eth0 NIC Link is Down
Dec  8 15:44:30 some-one kernel: [ 2952.924765] eth1: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
Dec  8 15:44:36 some-one kernel: [ 2958.477654] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 15:44:42 some-one kernel: [ 2964.869982] atl2: eth0 NIC Link is Down
Dec  8 15:44:44 some-one kernel: [ 2966.164031] usb 5-3: new high speed USB device using ehci_hcd and address 5
Dec  8 15:44:44 some-one kernel: [ 2966.298330] usb 5-3: configuration #1 chosen from 2 choices
Dec  8 15:44:44 some-one kernel: [ 2966.302080] eth1: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 00:02:00:dc:19:05
Dec  8 15:44:44 some-one kernel: [ 2966.702393] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 15:44:59 some-one kernel: [ 2981.084508] eth1: no IPv6 routers present
Dec  8 16:18:09 some-one kernel: [ 4971.215333] usb 5-3: USB disconnect, address 5
Dec  8 16:18:09 some-one kernel: [ 4971.215618] atl2: eth0 NIC Link is Down
Dec  8 16:18:09 some-one kernel: [ 4971.217894] eth1: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
Dec  8 16:18:14 some-one kernel: [ 4976.223845] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 16:18:20 some-one kernel: [ 4982.607087] atl2: eth0 NIC Link is Down
Dec  8 16:18:21 some-one kernel: [ 4983.912179] usb 5-3: new high speed USB device using ehci_hcd and address 7
Dec  8 16:18:22 some-one kernel: [ 4984.042491] usb 5-3: configuration #1 chosen from 2 choices
Dec  8 16:18:22 some-one kernel: [ 4984.046870] eth1: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 00:02:00:dc:19:05
Dec  8 16:18:22 some-one kernel: [ 4984.382088] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 16:18:36 some-one kernel: [ 4998.524510] eth1: no IPv6 routers present

Any ideas as it's frustrating...

Thanks..

---

### Post by hopelessone on 2008-12-08
Any Ideas?

heres some more logs..

> Dec  8 17:18:11 some-one NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Dec  8 17:18:11 some-one NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Dec  8 17:18:11 some-one NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 10088 
Dec  8 17:18:11 some-one NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Dec  8 17:18:11 some-one avahi-daemon[4703]: Withdrawing address record for 219.254.183.86 on eth1.
Dec  8 17:18:11 some-one avahi-daemon[4703]: Leaving mDNS multicast group on interface eth1.IPv4 with address 219.254.183.86.
Dec  8 17:18:11 some-one avahi-daemon[4703]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1' 
Dec  8 17:18:11 some-one NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec  8 17:18:11 some-one NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Dec  8 17:18:11 some-one NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Dec  8 17:18:11 some-one NetworkManager: <info>  dhclient started with pid 12100 
Dec  8 17:18:11 some-one NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Dec  8 17:18:11 some-one dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec  8 17:18:11 some-one dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec  8 17:18:11 some-one dhclient: All rights reserved.
Dec  8 17:18:11 some-one dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec  8 17:18:11 some-one dhclient: 
Dec  8 17:18:11 some-one NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Dec  8 17:18:12 some-one dhclient: Listening on LPF/eth1/00:02:00:dc:19:05
Dec  8 17:18:12 some-one dhclient: Sending on   LPF/eth1/00:02:00:dc:19:05
Dec  8 17:18:12 some-one dhclient: Sending on   Socket/fallback
Dec  8 17:18:12 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Dec  8 17:18:14 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec  8 17:18:21 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Dec  8 17:18:39 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec  8 17:18:46 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Dec  8 17:18:56 some-one NetworkManager: <info>  Device 'eth1' DHCP transaction took too long (>45s), stopping it. 
Dec  8 17:18:57 some-one NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 12100 
Dec  8 17:18:57 some-one NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Dec  8 17:18:57 some-one NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Dec  8 17:18:57 some-one NetworkManager: <info>  (eth1): device state change: 7 -> 9 
Dec  8 17:18:57 some-one NetworkManager: <info>  Marking connection 'Auto eth1' invalid. 
Dec  8 17:18:57 some-one NetworkManager: <info>  Activation (eth1) failed. 
Dec  8 17:18:57 some-one NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Dec  8 17:18:57 some-one NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Dec  8 17:18:57 some-one NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Dec  8 17:19:52 some-one kernel: [ 8674.830730] usb 5-3: USB disconnect, address 9
Dec  8 17:19:52 some-one kernel: [ 8674.830970] atl2: eth0 NIC Link is Down
Dec  8 17:19:52 some-one kernel: [ 8674.833838] eth1: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
Dec  8 17:19:52 some-one nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_02_00_dc_19_05)
Dec  8 17:19:52 some-one NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Dec  8 17:19:52 some-one NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Dec  8 17:19:52 some-one NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Dec  8 17:19:52 some-one NetworkManager: <info>  (eth1): now unmanaged 
Dec  8 17:19:52 some-one NetworkManager: <info>  (eth1): device state change: 3 -> 1 
Dec  8 17:19:52 some-one NetworkManager: <info>  (eth1): cleaning up... 
Dec  8 17:20:01 some-one kernel: [ 8683.864008] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 17:20:01 some-one NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Dec  8 17:20:01 some-one NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Dec  8 17:20:01 some-one /USR/SBIN/CRON[12271]: (some) CMD (export DISPLAY=:0 && /home/some/.aMule/amule.cron)
Dec  8 17:20:08 some-one kernel: [ 8690.088578] atl2: eth0 NIC Link is Down
Dec  8 17:20:08 some-one NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Dec  8 17:20:08 some-one NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Dec  8 17:20:08 some-one NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Dec  8 17:20:09 some-one kernel: [ 8691.384032] usb 5-3: new high speed USB device using ehci_hcd and address 11
Dec  8 17:20:09 some-one kernel: [ 8691.518350] usb 5-3: configuration #1 chosen from 2 choices
Dec  8 17:20:09 some-one kernel: [ 8691.522957] eth1: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 00:02:00:dc:19:05
Dec  8 17:20:09 some-one nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_02_00_dc_19_05, iface: eth1)
Dec  8 17:20:09 some-one NetworkManager: <info>  eth1: driver is 'rndis_host'. 
Dec  8 17:20:09 some-one NetworkManager: <info>  Found new Ethernet device 'eth1'. 
Dec  8 17:20:09 some-one NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_02_00_dc_19_05 
Dec  8 17:20:09 some-one kernel: [ 8691.863587] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
Dec  8 17:20:09 some-one NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Dec  8 17:20:09 some-one NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Dec  8 17:20:09 some-one NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec  8 17:20:09 some-one NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec  8 17:20:13 some-one nm-system-settings: Adding default connection 'Auto eth1' for /org/freedesktop/Hal/devices/net_00_02_00_dc_19_05
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): bringing up device. 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): preparing device. 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): carrier now ON (device state 2) 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1' 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Dec  8 17:20:13 some-one NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Dec  8 17:20:13 some-one dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec  8 17:20:13 some-one dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec  8 17:20:13 some-one dhclient: All rights reserved.
Dec  8 17:20:13 some-one dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec  8 17:20:13 some-one dhclient: 
Dec  8 17:20:13 some-one NetworkManager: <info>  dhclient started with pid 12341 
Dec  8 17:20:13 some-one NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Dec  8 17:20:13 some-one NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Dec  8 17:20:13 some-one dhclient: Listening on LPF/eth1/00:02:00:dc:19:05
Dec  8 17:20:13 some-one dhclient: Sending on   LPF/eth1/00:02:00:dc:19:05
Dec  8 17:20:13 some-one dhclient: Sending on   Socket/fallback
Dec  8 17:20:15 some-one avahi-daemon[4703]: Registering new address record for fe80::202:ff:fedc:1905 on eth1.*.
Dec  8 17:20:16 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec  8 17:20:16 some-one dhclient: DHCPOFFER of 192.168.100.10 from 192.168.100.1
Dec  8 17:20:16 some-one dhclient: DHCPREQUEST of 192.168.100.10 on eth1 to 255.255.255.255 port 67
Dec  8 17:20:17 some-one dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Dec  8 17:20:17 some-one NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Dec  8 17:20:17 some-one NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec  8 17:20:17 some-one NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Dec  8 17:20:17 some-one NetworkManager: <info>    address 192.168.100.10 
Dec  8 17:20:17 some-one NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec  8 17:20:17 some-one NetworkManager: <info>    gateway 192.168.100.1 
Dec  8 17:20:17 some-one NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec  8 17:20:17 some-one NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Dec  8 17:20:17 some-one NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Dec  8 17:20:17 some-one avahi-daemon[4703]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.100.10.
Dec  8 17:20:17 some-one avahi-daemon[4703]: New relevant interface eth1.IPv4 for mDNS.
Dec  8 17:20:17 some-one avahi-daemon[4703]: Registering new address record for 192.168.100.10 on eth1.IPv4.
Dec  8 17:20:17 some-one dhclient: bound to 192.168.100.10 -- renewal in 7 seconds.
Dec  8 17:20:18 some-one NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Dec  8 17:20:18 some-one NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS. 
Dec  8 17:20:18 some-one NetworkManager: <info>  Activation (eth1) successful, device activated. 
Dec  8 17:20:18 some-one NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Dec  8 17:20:18 some-one ntpd[10189]: ntpd exiting on signal 15
Dec  8 17:20:18 some-one ntpdate[12412]: can't find host ntp.ubuntu.com 
Dec  8 17:20:18 some-one ntpdate[12412]: no servers can be used, exiting
Dec  8 17:20:18 some-one ntpd[12441]: ntpd 4.2.4p4@1.1520-o Wed Aug 20 17:03:31 UTC 2008 (1)
Dec  8 17:20:18 some-one ntpd[12442]: precision = 1.000 usec
Dec  8 17:20:18 some-one ntpd[12442]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec  8 17:20:18 some-one ntpd[12442]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Dec  8 17:20:18 some-one ntpd[12442]: Listening on interface #2 eth1, 192.168.100.10#123 Enabled
Dec  8 17:20:18 some-one ntpd[12442]: kernel time sync status 0040
Dec  8 17:20:18 some-one ntpd[12442]: frequency initialized -4.273 PPM from /var/lib/ntp/ntp.drift
Dec  8 17:20:18 some-one ntpd[12442]: getaddrinfo: "::1" invalid host address, ignored
Dec  8 17:20:18 some-one ntpd[12444]: signal_no_reset: signal 17 had flags 4000000
Dec  8 17:20:20 some-one ntpd_initres[12444]: couldn't resolve `ntp.ubuntu.com', giving up on it
Dec  8 17:20:24 some-one dhclient: DHCPREQUEST of 192.168.100.10 on eth1 to 192.168.100.1 port 67
Dec  8 17:20:24 some-one kernel: [ 8706.424015] eth1: no IPv6 routers present
Dec  8 17:20:24 some-one dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Dec  8 17:20:24 some-one dhclient: bound to 192.168.100.10 -- renewal in 6 seconds.
Dec  8 17:20:24 some-one NetworkManager: <info>  DHCP: device eth1 state changed bound -> renew 
Dec  8 17:20:24 some-one NetworkManager: <info>    address 192.168.100.10 
Dec  8 17:20:24 some-one NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec  8 17:20:24 some-one NetworkManager: <info>    gateway 192.168.100.1 
Dec  8 17:20:25 some-one avahi-daemon[4703]: Withdrawing address record for 192.168.100.10 on eth1.
Dec  8 17:20:25 some-one avahi-daemon[4703]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.100.10.
Dec  8 17:20:25 some-one avahi-daemon[4703]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec  8 17:20:25 some-one avahi-daemon[4703]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.100.10.
Dec  8 17:20:25 some-one avahi-daemon[4703]: New relevant interface eth1.IPv4 for mDNS.
Dec  8 17:20:25 some-one avahi-daemon[4703]: Registering new address record for 192.168.100.10 on eth1.IPv4.
Dec  8 17:20:26 some-one NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS. 
Dec  8 17:20:30 some-one dhclient: DHCPREQUEST of 192.168.100.10 on eth1 to 192.168.100.1 port 67
Dec  8 17:20:35 some-one NetworkManager: <info>  DHCP: device eth1 state changed renew -> expire 
Dec  8 17:20:35 some-one dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec  8 17:20:35 some-one NetworkManager: <info>  DHCP: device eth1 state changed expire -> preinit 
Dec  8 17:20:35 some-one dhclient: DHCPOFFER of 219.254.183.86 from 10.165.96.1
Dec  8 17:20:35 some-one dhclient: DHCPREQUEST of 219.254.183.86 on eth1 to 255.255.255.255 port 67
Dec  8 17:20:35 some-one dhclient: DHCPACK of 219.254.183.86 from 10.165.96.1
Dec  8 17:20:35 some-one dhclient: bound to 219.254.183.86 -- renewal in 3030 seconds.
Dec  8 17:20:35 some-one NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Dec  8 17:20:35 some-one NetworkManager: <info>    address 219.254.183.86 
Dec  8 17:20:35 some-one NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec  8 17:20:35 some-one NetworkManager: <info>    gateway 219.254.183.1 
Dec  8 17:20:35 some-one NetworkManager: <info>    hostname 'some-one' 
Dec  8 17:20:35 some-one NetworkManager: <info>    nameserver '219.250.36.130' 
Dec  8 17:20:35 some-one NetworkManager: <info>    nameserver '210.220.163.82' 
Dec  8 17:20:35 some-one NetworkManager: <info>    domain name 'hananet' 
Dec  8 17:20:35 some-one avahi-daemon[4703]: Withdrawing address record for 192.168.100.10 on eth1.
Dec  8 17:20:35 some-one avahi-daemon[4703]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.100.10.
Dec  8 17:20:35 some-one avahi-daemon[4703]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec  8 17:20:35 some-one avahi-daemon[4703]: Joining mDNS multicast group on interface eth1.IPv4 with address 219.254.183.86.
Dec  8 17:20:35 some-one avahi-daemon[4703]: New relevant interface eth1.IPv4 for mDNS.
Dec  8 17:20:35 some-one avahi-daemon[4703]: Registering new address record for 219.254.183.86 on eth1.IPv4.
Dec  8 17:20:36 some-one avahi-daemon[4703]: Withdrawing address record for fe80::202:ff:fedc:1905 on eth1.
Dec  8 17:20:36 some-one NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS. 

Any light at all would be much appreciated...

---

### Post by hopelessone on 2008-12-09
Re-install?

---

### Post by Peter09 on 2008-12-09
Once failed can you post the output of:

```
ifconfig
```
and
```
[CODE]route -n
```[/CODE]

---

### Post by hopelessone on 2008-12-10
Hi,

Thanks,

Here are the outputs:

> some@some-one:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:63:42:fe  
          inet6 addr: fe80::2e0:4dff:fe63:42fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1137963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:18
          collisions:0 txqueuelen:1000 
          RX bytes:68888480 (68.8 MB)  TX bytes:0 (0.0 B)
          Memory:fdd80000-fddc0000 

eth1      Link encap:Ethernet  HWaddr 00:02:00:dc:19:05  
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:4719550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5218976 errors:29638 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:881229346 (881.2 MB)  TX bytes:2646572844 (2.6 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:508976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55775100 (55.7 MB)  TX bytes:55775100 (55.7 MB)


and

> some@some-one:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


hope this will help...

---

### Post by Peter09 on 2008-12-10
You appear to have two active ethernet connections, is this correct, one of which has a large number of transmission errors.

As you can see you have no active routing information.

---

### Post by hopelessone on 2008-12-10
OK so how would i go about fixing this?

Thanks

---

### Post by Peter09 on 2008-12-10
Are we looking at a wired connection and a wireless connection which are active at the same time. If so, do you get the same problem if one is switched off / disconnected.

---

