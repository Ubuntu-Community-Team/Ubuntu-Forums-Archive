---
title: "Atheros AR242x AR5BXB63 drops connection"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by patryk77 on 2008-12-02
Hello,

I am using Ubuntu Netbook Remix 1.0.1 (Hardy), on an Acer AspireOne 150L.

The wireless adapter randomly stops working. It hasn't worked for more than some 36 hours in a row so far.

In order to get it working, I have to shutdown and wait a few seconds. If I simply reboot, it gives me an error loading HAL, or something like that.

I haven't yet had the time to copy/paste the log files, but I will post them next time it happens.

However, from [http://aspireone.wikia.com/wiki/List_of_Known_Bugs_and_Fixes:](http://aspireone.wikia.com/wiki/List_of_Known_Bugs_and_Fixes:)
> For Windows users, go to Device Manager -> Network Adapters -> Atheros AR5007EG, and change the power management from Maximum to either normal or off. This helps some users but doesn't seem to help everyone.

Is there a way to disable it in Linux as well?

Has anybody else had this problem and know of a solution?

Thanks

Sticker under laptop says Atheros AR5BXB63

```

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:23:4d:76:72:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.67 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by patryk77 on 2008-12-02
Ok, here are the logs for after it hangs, as well as a lot more info from when it loads... pretty much everything that is related to my ath0 device.

I also left some messages about the built-in cam as it may be related? Anyways, they appear right before it starts complaining about disconnection.

So, now does anybody have a clue?


```
DMESG:
======

[    0.000000] Linux version 2.6.24-19-lpia (root@macbook) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 3 15:25:26 UTC 2008 (Unofficial)
[   22.436395] ath_hal: module license 'Proprietary' taints kernel.
[   22.530066] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[   22.717863] intel_rng: FWH not detected
[   22.789817] wlan: trunk
[   22.929670] ath_pci: trunk
[   24.422875] MadWifi: ath_attach: Switching rfkill capability off
[   24.481982] ath_rate_sample: 1.2 (trunk)
[   24.482855] MadWifi: ath_attach: Switching per-packet transmit power control off
[   24.484445] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   24.484463] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   24.484485] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   24.484507] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
[   24.484514] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
[   24.484520] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
[   24.484526] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
[   24.484533] wifi0: ath_announce: Use hw queue 8 for CAB traffic
[   24.484538] wifi0: ath_announce: Use hw queue 9 for beacons
[   24.565815] ath_pci: wifi0: Atheros 5424/2424: mem=0x75200000, irq=18
[   53.010200] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   72.810525] ath0: no IPv6 routers present
[18421.526914] uvcvideo: Failed to resubmit video URB (-45).
[18421.526964] uvcvideo: Failed to resubmit video URB (-45).
[18421.526996] uvcvideo: Failed to resubmit video URB (-45).
[18421.527025] uvcvideo: Failed to resubmit video URB (-45).
[18486.341303] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 0)
[18487.367595] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 998195634)
[18488.200370] wifi0: ath_chan_set: Unable to reset channel 7 (2442 MHz) flags 0xc0 '' (HAL status 1830391837)
[18489.225385] wifi0: ath_chan_set: Unable to reset channel 13 (2472 MHz) flags 0xc0 '' (HAL status 4149459392)
[18616.233689] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 80038452)
[18616.233908] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[18705.230585] NETDEV WATCHDOG: wifi0: transmit timed out
[18706.066818] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
[18746.117109] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 0)
[18747.151136] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 3076017611)
[18821.118819] NETDEV WATCHDOG: wifi0: transmit timed out
[18821.954636] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
[18875.998348] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 3081373204)
[18877.025288] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 4108388687)
[18942.002254] NETDEV WATCHDOG: wifi0: transmit timed out
[18942.838080] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
[18997.948282] NETDEV WATCHDOG: wifi0: transmit timed out
[18998.784191] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
[19005.881063] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 4115114101)


```


```
Syslog:
=======
Dec  2 15:56:16 patryk kernel: [   22.436395] ath_hal: module license 'Proprietary' taints kernel.
Dec  2 15:56:16 patryk kernel: [   22.530066] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
Dec  2 15:56:16 patryk kernel: [   22.717863] intel_rng: FWH not detected
Dec  2 15:56:16 patryk kernel: [   22.789817] wlan: trunk
Dec  2 15:56:16 patryk kernel: [   22.929670] ath_pci: trunk
Dec  2 15:56:16 patryk kernel: [   22.929859] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec  2 15:56:16 patryk kernel: [   24.124711] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec  2 15:56:16 patryk kernel: [   24.422875] MadWifi: ath_attach: Switching rfkill capability off
Dec  2 15:56:16 patryk kernel: [   24.481982] ath_rate_sample: 1.2 (trunk)
Dec  2 15:56:16 patryk kernel: [   24.482855] MadWifi: ath_attach: Switching per-packet transmit power control off
Dec  2 15:56:16 patryk kernel: [   24.484445] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Dec  2 15:56:16 patryk kernel: [   24.484463] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Dec  2 15:56:16 patryk kernel: [   24.484485] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Dec  2 15:56:16 patryk kernel: [   24.484507] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
Dec  2 15:56:16 patryk kernel: [   24.484514] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
Dec  2 15:56:16 patryk kernel: [   24.484520] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
Dec  2 15:56:16 patryk kernel: [   24.484526] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
Dec  2 15:56:16 patryk kernel: [   24.484533] wifi0: ath_announce: Use hw queue 8 for CAB traffic
Dec  2 15:56:16 patryk kernel: [   24.484538] wifi0: ath_announce: Use hw queue 9 for beacons
Dec  2 15:56:16 patryk kernel: [   24.565815] ath_pci: wifi0: Atheros 5424/2424: mem=0x75200000, irq=18
Dec  2 15:56:25 patryk NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
Dec  2 15:56:25 patryk NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
Dec  2 15:56:25 patryk NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Dec  2 15:56:25 patryk NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Dec  2 15:56:25 patryk NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
Dec  2 15:56:25 patryk NetworkManager: <info>  Deactivating device ath0. 
Dec  2 15:56:25 patryk hcid[4531]: Bluetooth HCI daemon
Dec  2 15:56:38 patryk NetworkManager: <info>  Updating allowed wireless network lists. 
Dec  2 15:56:38 patryk NetworkManager: <info>  SWITCH: no current connection, found better connection 'ath0'. 
Dec  2 15:56:38 patryk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Dec  2 15:56:38 patryk NetworkManager: <info>  Will activate connection 'ath0/INFINITUM3830'. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Device ath0 activation scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) started... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0/wireless): access point 'INFINITUM3830' is encrypted, but NO valid key exists.  New key needed. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'INFINITUM3830'. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) New wireless user key for network 'INFINITUM3830' received. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0/wireless): access point 'INFINITUM3830' is encrypted, and a key exists.  No new key needed. 
Dec  2 15:56:40 patryk NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Dec  2 15:56:40 patryk kernel: [   53.010200] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was '0' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid xxxxxxxxxxxxxxxxxxxxxxxxx' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Dec  2 15:56:41 patryk avahi-daemon[4157]: Registering new address record for fe80::223:4dff:fe76:7281 on ath0.*.
Dec  2 15:56:43 patryk NetworkManager: <info>  Supplicant state changed: 1 
Dec  2 15:56:43 patryk NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'INFINITUM3830'. 
Dec  2 15:56:43 patryk NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  2 15:56:43 patryk NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Dec  2 15:56:44 patryk NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Dec  2 15:56:44 patryk NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Dec  2 15:56:44 patryk NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
Dec  2 15:56:44 patryk dhclient: wifi0: unknown hardware address type 801
Dec  2 15:56:45 patryk dhclient: wifi0: unknown hardware address type 801
Dec  2 15:56:45 patryk NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0 
Dec  2 15:56:47 patryk dhclient: DHCPREQUEST of 192.168.1.67 on ath0 to 255.255.255.255 port 67
Dec  2 15:56:47 patryk dhclient: DHCPACK of 192.168.1.67 from 192.168.1.254
Dec  2 15:56:47 patryk avahi-daemon[4157]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.67.
Dec  2 15:56:47 patryk avahi-daemon[4157]: New relevant interface ath0.IPv4 for mDNS.
Dec  2 15:56:47 patryk avahi-daemon[4157]: Registering new address record for 192.168.1.67 on ath0.IPv4.
Dec  2 15:56:47 patryk NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface ath0 
Dec  2 15:56:47 patryk NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec  2 15:56:47 patryk NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
Dec  2 15:56:47 patryk dhclient: bound to 192.168.1.67 -- renewal in 36959 seconds.
Dec  2 15:56:48 patryk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Dec  2 15:56:48 patryk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Dec  2 15:56:48 patryk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Dec  2 15:56:48 patryk NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Dec  2 15:56:48 patryk NetworkManager: <info>    address 192.168.1.67 
Dec  2 15:56:48 patryk NetworkManager: <info>    netmask 255.255.255.0 
Dec  2 15:56:48 patryk NetworkManager: <info>    broadcast 192.168.1.255 
Dec  2 15:56:48 patryk NetworkManager: <info>    gateway 192.168.1.254 
Dec  2 15:56:48 patryk NetworkManager: <info>    nameserver 192.168.1.254 
Dec  2 15:56:48 patryk NetworkManager: <info>    domain name 'gateway.2wire.net' 
Dec  2 15:56:48 patryk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Dec  2 15:56:48 patryk NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec  2 15:56:48 patryk NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
Dec  2 15:56:48 patryk NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
Dec  2 15:56:48 patryk NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Dec  2 15:56:48 patryk avahi-daemon[4157]: Withdrawing address record for 192.168.1.67 on ath0.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.67.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Interface ath0.IPv4 no longer relevant for mDNS.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Withdrawing address record for fe80::223:4dff:fe76:7281 on ath0.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.67.
Dec  2 15:56:48 patryk avahi-daemon[4157]: New relevant interface ath0.IPv4 for mDNS.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Registering new address record for 192.168.1.67 on ath0.IPv4.
Dec  2 15:56:49 patryk NetworkManager: <info>  Clearing nscd hosts cache. 
Dec  2 15:56:49 patryk NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Dec  2 15:56:49 patryk NetworkManager: <info>  Activation (ath0) successful, device activated. 
Dec  2 15:56:49 patryk NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
Dec  2 15:56:49 patryk NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec  2 15:56:50 patryk ntpdate[4983]: step time server 91.189.94.4 offset -0.747024 sec
Dec  2 15:56:50 patryk avahi-daemon[4157]: Registering new address record for fe80::223:4dff:fe76:7281 on ath0.*.
Dec  2 15:59:56 patryk kernel: [  249.512126] CE: __tick_program_event of hpet is stuck 3839a0e388 3839a0f710
Dec  2 15:59:56 patryk kernel: [  249.512149] CE: increasing min_delta_ns 5000 to 10000 nsec
Dec  2 15:59:56 patryk kernel: [  249.512162] WARNING: at /root/src/hardy-netbook/debian/build/custom-source-lpia/kernel/time/tick-oneshot.c:52 tick_dev_program_event()
Dec  2 15:59:56 patryk kernel: [  249.512183] Pid: 0, comm: swapper Tainted: P        2.6.24-19-lpia #1
Dec  2 15:59:56 patryk kernel: [  249.512219]  [tick_dev_program_event+0xdc/0x130] tick_dev_program_event+0xdc/0x130
Dec  2 15:59:56 patryk kernel: [  249.512294]  [tick_broadcast_set_event+0x14/0x20] tick_broadcast_set_event+0x14/0x20
Dec  2 15:59:56 patryk kernel: [  249.512318]  [tick_broadcast_oneshot_control+0x109/0x110] tick_broadcast_oneshot_control+0x109/0x110
Dec  2 15:59:56 patryk kernel: [  249.512354]  [tick_notify+0x25b/0x390] tick_notify+0x25b/0x390
Dec  2 15:59:56 patryk kernel: [  249.512390]  [get_next_timer_interrupt+0x19b/0x220] get_next_timer_interrupt+0x19b/0x220
Dec  2 15:59:56 patryk kernel: [  249.512424]  [notifier_call_chain+0x30/0x60] notifier_call_chain+0x30/0x60
Dec  2 15:59:56 patryk kernel: [  249.512465]  [raw_notifier_call_chain+0x17/0x20] raw_notifier_call_chain+0x17/0x20
Dec  2 15:59:56 patryk kernel: [  249.512492]  [clockevents_notify+0x19/0x60] clockevents_notify+0x19/0x60
Dec  2 15:59:56 patryk kernel: [  249.512517]  [acpi_idle_enter_simple+0x7f/0x1b6] acpi_idle_enter_simple+0x7f/0x1b6
Dec  2 15:59:56 patryk kernel: [  249.512536]  [menu_select+0x84/0xa0] menu_select+0x84/0xa0
Dec  2 15:59:56 patryk kernel: [  249.512573]  [cpuidle_idle_call+0x7c/0xb0] cpuidle_idle_call+0x7c/0xb0
Dec  2 15:59:56 patryk kernel: [  249.512598]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
Dec  2 15:59:56 patryk kernel: [  249.512689]  =======================
Dec  2 21:03:06 patryk kernel: [18421.526914] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:03:06 patryk kernel: [18421.526964] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:03:06 patryk kernel: [18421.526996] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:03:06 patryk kernel: [18421.527025] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:04:10 patryk kernel: [18486.341303] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 0)
Dec  2 21:04:11 patryk kernel: [18487.367595] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 998195634)
Dec  2 21:04:12 patryk kernel: [18488.200370] wifi0: ath_chan_set: Unable to reset channel 7 (2442 MHz) flags 0xc0 '' (HAL status 1830391837)
Dec  2 21:04:13 patryk kernel: [18489.225385] wifi0: ath_chan_set: Unable to reset channel 13 (2472 MHz) flags 0xc0 '' (HAL status 4149459392)
Dec  2 21:06:20 patryk kernel: [18616.233689] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 80038452)
Dec  2 21:06:20 patryk kernel: [18616.233908] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Dec  2 21:07:50 patryk kernel: [18705.230585] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:07:50 patryk kernel: [18706.066818] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:08:30 patryk kernel: [18746.117109] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 0)
Dec  2 21:08:31 patryk kernel: [18747.151136] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 3076017611)
Dec  2 21:09:46 patryk kernel: [18821.118819] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:09:46 patryk kernel: [18821.954636] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:10:40 patryk kernel: [18875.998348] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 3081373204)
Dec  2 21:10:41 patryk kernel: [18877.025288] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 4108388687)
Dec  2 21:11:47 patryk kernel: [18942.002254] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:11:47 patryk kernel: [18942.838080] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:12:43 patryk kernel: [18997.948282] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:12:43 patryk kernel: [18998.784191] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:12:50 patryk kernel: [19005.881063] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 4115114101)

```


```



kern.log:
=========

Dec  2 15:56:16 patryk kernel: [   22.436395] ath_hal: module license 'Proprietary' taints kernel.
Dec  2 15:56:16 patryk kernel: [   22.530066] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
Dec  2 15:56:16 patryk kernel: [   22.717863] intel_rng: FWH not detected
Dec  2 15:56:16 patryk kernel: [   22.789817] wlan: trunk
Dec  2 15:56:16 patryk kernel: [   22.929670] ath_pci: trunk
Dec  2 15:56:16 patryk kernel: [   22.929859] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec  2 15:56:16 patryk kernel: [   24.124711] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec  2 15:56:16 patryk kernel: [   24.422875] MadWifi: ath_attach: Switching rfkill capability off
Dec  2 15:56:16 patryk kernel: [   24.481982] ath_rate_sample: 1.2 (trunk)
Dec  2 15:56:16 patryk kernel: [   24.482855] MadWifi: ath_attach: Switching per-packet transmit power control off
Dec  2 15:56:16 patryk kernel: [   24.484445] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Dec  2 15:56:16 patryk kernel: [   24.484463] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Dec  2 15:56:16 patryk kernel: [   24.484485] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Dec  2 15:56:16 patryk kernel: [   24.484507] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
Dec  2 15:56:16 patryk kernel: [   24.484514] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
Dec  2 15:56:16 patryk kernel: [   24.484520] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
Dec  2 15:56:16 patryk kernel: [   24.484526] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
Dec  2 15:56:16 patryk kernel: [   24.484533] wifi0: ath_announce: Use hw queue 8 for CAB traffic
Dec  2 15:56:16 patryk kernel: [   24.484538] wifi0: ath_announce: Use hw queue 9 for beacons
Dec  2 15:56:16 patryk kernel: [   24.565815] ath_pci: wifi0: Atheros 5424/2424: mem=0x75200000, irq=18
Dec  2 15:56:40 patryk kernel: [   53.010200] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Dec  2 21:03:06 patryk kernel: [18421.526914] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:03:06 patryk kernel: [18421.526964] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:03:06 patryk kernel: [18421.526996] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:03:06 patryk kernel: [18421.527025] uvcvideo: Failed to resubmit video URB (-45).
Dec  2 21:04:10 patryk kernel: [18486.341303] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 0)
Dec  2 21:04:11 patryk kernel: [18487.367595] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 998195634)
Dec  2 21:04:12 patryk kernel: [18488.200370] wifi0: ath_chan_set: Unable to reset channel 7 (2442 MHz) flags 0xc0 '' (HAL status 1830391837)
Dec  2 21:04:13 patryk kernel: [18489.225385] wifi0: ath_chan_set: Unable to reset channel 13 (2472 MHz) flags 0xc0 '' (HAL status 4149459392)
Dec  2 21:06:20 patryk kernel: [18616.233689] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 80038452)
Dec  2 21:06:20 patryk kernel: [18616.233908] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Dec  2 21:07:50 patryk kernel: [18705.230585] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:07:50 patryk kernel: [18706.066818] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:08:30 patryk kernel: [18746.117109] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 0)
Dec  2 21:08:31 patryk kernel: [18747.151136] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 3076017611)
Dec  2 21:09:46 patryk kernel: [18821.118819] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:09:46 patryk kernel: [18821.954636] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:10:40 patryk kernel: [18875.998348] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 3081373204)
Dec  2 21:10:41 patryk kernel: [18877.025288] wifi0: ath_chan_set: Unable to reset channel 11 (2462 MHz) flags 0xc0 '' (HAL status 4108388687)
Dec  2 21:11:47 patryk kernel: [18942.002254] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:11:47 patryk kernel: [18942.838080] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:12:43 patryk kernel: [18997.948282] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:12:43 patryk kernel: [18998.784191] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)
Dec  2 21:12:50 patryk kernel: [19005.881063] wifi0: ath_chan_set: Unable to reset channel 6 (2437 MHz) flags 0xc0 '' (HAL status 4115114101)
Dec  2 21:13:54 patryk kernel: [19068.879901] NETDEV WATCHDOG: wifi0: transmit timed out
Dec  2 21:13:54 patryk kernel: [19069.716184] wifi0: ath_reset: Unable to reset hardware: '' (HAL status 3227283328)

```



```
daemon.log:
===========


Dec  2 15:56:25 patryk NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
Dec  2 15:56:25 patryk NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
Dec  2 15:56:25 patryk NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Dec  2 15:56:25 patryk NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Dec  2 15:56:25 patryk NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
Dec  2 15:56:25 patryk NetworkManager: <info>  Deactivating device ath0. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Updating allowed wireless network lists. 
Dec  2 15:56:38 patryk NetworkManager: <info>  SWITCH: no current connection, found better connection 'ath0'. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Will activate connection 'ath0/INFINITUM3830'. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Device ath0 activation scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) started... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0/wireless): access point 'INFINITUM3830' is encrypted, but NO valid key exists.  New key needed. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'INFINITUM3830'. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) New wireless user key for network 'INFINITUM3830' received. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Dec  2 15:56:38 patryk NetworkManager: <info>  Activation (ath0/wireless): access point 'INFINITUM3830' is encrypted, and a key exists.  No new key needed. 
Dec  2 15:56:40 patryk NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was '0' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid xxxxxxxxxxxxxxxxxxxxxxxxxx' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  2 15:56:40 patryk NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 15:56:40 patryk NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Dec  2 15:56:41 patryk avahi-daemon[4157]: Registering new address record for fe80::223:4dff:fe76:7281 on ath0.*.
Dec  2 15:56:43 patryk NetworkManager: <info>  Supplicant state changed: 1 
Dec  2 15:56:43 patryk NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'INFINITUM3830'. 
Dec  2 15:56:43 patryk NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  2 15:56:43 patryk NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Dec  2 15:56:44 patryk NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Dec  2 15:56:44 patryk NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Dec  2 15:56:44 patryk NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
Dec  2 15:56:44 patryk dhclient: wifi0: unknown hardware address type 801
Dec  2 15:56:45 patryk dhclient: wifi0: unknown hardware address type 801
Dec  2 15:56:45 patryk NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0 
Dec  2 15:56:47 patryk dhclient: DHCPREQUEST of 192.168.1.67 on ath0 to 255.255.255.255 port 67
Dec  2 15:56:47 patryk dhclient: DHCPACK of 192.168.1.67 from 192.168.1.254
Dec  2 15:56:47 patryk avahi-daemon[4157]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.67.
Dec  2 15:56:47 patryk avahi-daemon[4157]: New relevant interface ath0.IPv4 for mDNS.
Dec  2 15:56:47 patryk avahi-daemon[4157]: Registering new address record for 192.168.1.67 on ath0.IPv4.
Dec  2 15:56:47 patryk NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface ath0 
Dec  2 15:56:47 patryk NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec  2 15:56:47 patryk NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
Dec  2 15:56:47 patryk dhclient: bound to 192.168.1.67 -- renewal in 36959 seconds.
Dec  2 15:56:48 patryk NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Dec  2 15:56:48 patryk NetworkManager: <info>    address 192.168.1.67 
Dec  2 15:56:48 patryk NetworkManager: <info>    netmask 255.255.255.0 
Dec  2 15:56:48 patryk NetworkManager: <info>    broadcast 192.168.1.255 
Dec  2 15:56:48 patryk NetworkManager: <info>    gateway 192.168.1.254 
Dec  2 15:56:48 patryk NetworkManager: <info>    nameserver 192.168.1.254 
Dec  2 15:56:48 patryk NetworkManager: <info>    domain name 'gateway.2wire.net' 
Dec  2 15:56:48 patryk NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec  2 15:56:48 patryk NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
Dec  2 15:56:48 patryk NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
Dec  2 15:56:48 patryk NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Dec  2 15:56:48 patryk avahi-daemon[4157]: Withdrawing address record for 192.168.1.67 on ath0.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.67.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Interface ath0.IPv4 no longer relevant for mDNS.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Withdrawing address record for fe80::223:4dff:fe76:7281 on ath0.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.67.
Dec  2 15:56:48 patryk avahi-daemon[4157]: New relevant interface ath0.IPv4 for mDNS.
Dec  2 15:56:48 patryk avahi-daemon[4157]: Registering new address record for 192.168.1.67 on ath0.IPv4.
Dec  2 15:56:49 patryk NetworkManager: <info>  Clearing nscd hosts cache. 
Dec  2 15:56:49 patryk NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Dec  2 15:56:49 patryk NetworkManager: <info>  Activation (ath0) successful, device activated. 
Dec  2 15:56:49 patryk NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
Dec  2 15:56:49 patryk NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec  2 15:56:50 patryk ntpdate[4983]: step time server 91.189.94.4 offset -0.747024 sec
Dec  2 15:56:50 patryk avahi-daemon[4157]: Registering new address record for fe80::223:4dff:fe76:7281 on ath0.*.

```

---

### Post by atlas95 on 2008-12-05
Hello,

I have the same tick-oneshot error with ubuntu network remix hardy  lpia on my Toshiba NB100.

I search how to fix this too...

---

### Post by patryk77 on 2008-12-10
bump

---

### Post by atlas95 on 2009-01-15
bump

129 profile="/usr/sbin/smbd" namespace="default"
[ 1606.530543] CE: __tick_program_event of hpet is stuck 174126dbaa6 174126dce2e
[ 1606.530567] CE: increasing min_delta_ns 5000 to 10000 nsec
[ 1606.530580] WARNING: at /root/src/hardy-netbook/debian/build/custom-source-lpia/kernel/time/tick-oneshot.c:52 tick_dev_program_event()
[ 1606.530601] Pid: 0, comm: swapper Tainted: PF       2.6.24-19-lpia #1
[ 1606.530646]  [<c014b13c>] tick_dev_program_event+0xdc/0x130
[ 1606.530744]  [<c014a774>] tick_broadcast_set_event+0x14/0x20
[ 1606.530771]  [<c014acd9>] tick_broadcast_oneshot_control+0x109/0x110
[ 1606.530817]  [<c014a44b>] tick_notify+0x25b/0x390
[ 1606.530861]  [<c0136c1b>] get_next_timer_interrupt+0x19b/0x220
[ 1606.530903]  [<c03f7a50>] notifier_call_chain+0x30/0x60
[ 1606.530955]  [<c0146107>] raw_notifier_call_chain+0x17/0x20
[ 1606.530987]  [<c0149e19>] clockevents_notify+0x19/0x60
[ 1606.531018]  [<c0287321>] acpi_idle_enter_simple+0x7f/0x1b6
[ 1606.531037]  [<c0329724>] menu_select+0x84/0xa0
[ 1606.531085]  [<c0328aac>] cpuidle_idle_call+0x7c/0xb0
[ 1606.531114]  [<c0103695>] cpu_idle+0x45/0xd0
[ 1606.531243]  =======================
[ 2057.690487] nautilus[7114]: segfault at d6000020 eip b773dcbb esp bfdbc454 error 5

---

