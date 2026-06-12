---
title: "Router visible but no connection"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Pixtu on 2008-11-09
I believe that my driver must be working correctly because I can scan for and see my router along with others in the area.

However, the system won't connect with it and I can't ping it.

I have enclosed the content of my syslog which, hopefully, might provide a clue to those more knowledgable about what is going wrong. I have extracted lines that don't have anything to do with the networking element.

```

Nov  9 13:39:55 linux-dt syslogd 1.5.0#2ubuntu6: restart.
Nov  9 13:39:55 linux-dt kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov  9 13:39:56 linux-dt kernel: Cannot find map file.
Nov  9 13:39:56 linux-dt kernel: Loaded 48284 symbols from 88 modules.
Nov  9 13:39:56 linux-dt kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  9 13:39:56 linux-dt kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  9 13:39:56 linux-dt kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)

Nov  9 13:39:56 linux-dt kernel: [   23.964159] at76_usb: Atmel at76c50x USB Wireless LAN Driver 0.14beta1 loading
Nov  9 13:39:56 linux-dt kernel: [   23.964220] firmware: requesting atmel_at76c503-rfmd-acc.bin
Nov  9 13:39:56 linux-dt kernel: [   24.130000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10

Nov  9 13:39:56 linux-dt kernel: [   28.907391] usbcore: registered new interface driver at76_usb
Nov  9 13:39:56 linux-dt kernel: [   31.113989] lp0: using parport0 (interrupt-driven).
Nov  9 13:39:56 linux-dt kernel: [   31.136154] at76_usb: wlan0 disconnecting
Nov  9 13:39:56 linux-dt kernel: [   31.136175] at76_usb: at76_usb disconnected
Nov  9 13:39:56 linux-dt kernel: [   31.249318] usb 1-1: reset full speed USB device using uhci_hcd and address 2
Nov  9 13:39:56 linux-dt kernel: [   31.397805] usb 1-1: device firmware changed
Nov  9 13:39:56 linux-dt kernel: [   31.397887] usb 1-1: USB disconnect, address 2
Nov  9 13:39:56 linux-dt kernel: [   31.397924] firmware: requesting atmel_at76c503-rfmd-acc.bin
Nov  9 13:39:56 linux-dt kernel: [   31.405782] at76_usb: wlan0 disconnecting
Nov  9 13:39:56 linux-dt kernel: [   31.405814] at76_usb: downloading internal fw failed with -19
Nov  9 13:39:56 linux-dt kernel: [   31.405839] at76_usb: at76_usb disconnected
Nov  9 13:39:56 linux-dt kernel: [   31.516246] usb 1-1: new full speed USB device using uhci_hcd and address 4
Nov  9 13:39:56 linux-dt kernel: [   31.576956] Adding 4883752k swap on /dev/sda2.  Priority:-1 extents:1 across:4883752k
Nov  9 13:39:56 linux-dt kernel: [   31.670375] usb 1-1: configuration #1 chosen from 1 choice
Nov  9 13:39:56 linux-dt kernel: [   31.671964] firmware: requesting atmel_at76c503-rfmd-acc.bin
Nov  9 13:39:56 linux-dt kernel: [   31.823746] at76_usb: firmware version 8.101.5 #84 (fcs_len 4)
Nov  9 13:39:56 linux-dt kernel: [   31.824770] at76_usb: device's MAC 00:31:47:cf:28:40, regulatory domain ETSI (Europe - (Spain+France) (id 48)
Nov  9 13:39:56 linux-dt kernel: [   31.826076] at76_usb: registered wlan0

Nov  9 13:40:00 linux-dt NetworkManager: <info>  starting... 
Nov  9 13:40:00 linux-dt NetworkManager: <info>  wlan0: driver is 'at76_usb'. 
Nov  9 13:40:00 linux-dt NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Nov  9 13:40:00 linux-dt NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Nov  9 13:40:00 linux-dt NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_30_bd_63_41_50 
Nov  9 13:40:00 linux-dt NetworkManager: <info>  Trying to start the supplicant... 
Nov  9 13:40:00 linux-dt NetworkManager: <info>  Trying to start the system settings daemon... 
Nov  9 13:40:01 linux-dt NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPlugin-Ifupdown: init!
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_30_bd_63_41_50, iface: wlan0)
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPlugin-Ifupdown: end _init.
Nov  9 13:40:01 linux-dt nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  9 13:40:01 linux-dt nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPlugin-Ifupdown: (159247088) ... get_connections.
Nov  9 13:40:01 linux-dt nm-system-settings:    SCPlugin-Ifupdown: (159247088) connections count: 0
Nov  9 13:40:01 linux-dt nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Nov  9 13:40:03 linux-dt acpid: client connected from 4923[0:0] 

Nov  9 13:40:04 linux-dt NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Nov  9 13:40:04 linux-dt NetworkManager: <info>  (wlan0): bringing up device. 
Nov  9 13:40:04 linux-dt NetworkManager: <info>  (wlan0): preparing device. 
Nov  9 13:40:04 linux-dt NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Nov  9 13:40:05 linux-dt NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Nov  9 13:40:05 linux-dt kernel: [   46.972977] NET: Registered protocol family 17
Nov  9 13:40:05 linux-dt NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Nov  9 13:40:07 linux-dt kernel: [   48.988092] at76_usb: 2515: assertion dev->istate == INIT failed
Nov  9 13:40:07 linux-dt kernel: [   49.720775] at76_usb: 2485: assertion dev->istate == SCANNING failed

Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) starting connection 'ssid-name' 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): access point 'ssid-name' has security, but secrets are required. 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Nov  9 13:40:52 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): connection 'ssid-name' has security, and secrets exist.  No new secrets needed. 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: added 'ssid' value 'ssid-name' 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  9 13:40:59 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 3 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ssid-name'. 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  dhclient started with pid 5501 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  9 13:41:03 linux-dt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  9 13:41:03 linux-dt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  9 13:41:03 linux-dt dhclient: All rights reserved.
Nov  9 13:41:03 linux-dt dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  9 13:41:03 linux-dt dhclient: 
Nov  9 13:41:03 linux-dt NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Nov  9 13:41:03 linux-dt dhclient: Listening on LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:41:03 linux-dt dhclient: Sending on   LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:41:03 linux-dt dhclient: Sending on   Socket/fallback
Nov  9 13:41:05 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Nov  9 13:41:11 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Nov  9 13:41:17 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Nov  9 13:41:31 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Nov  9 13:41:36 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 4 
Nov  9 13:41:36 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 13:41:45 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Nov  9 13:41:48 linux-dt NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5501 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'ssid-name'. 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov  9 13:41:48 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): connection 'ssid-name' has security, and secrets exist.  No new secrets needed. 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: added 'ssid' value 'ssid-name' 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  9 13:41:55 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Nov  9 13:41:56 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ssid-name'. 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov  9 13:42:00 linux-dt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  9 13:42:00 linux-dt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  9 13:42:00 linux-dt dhclient: All rights reserved.
Nov  9 13:42:00 linux-dt dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  9 13:42:00 linux-dt dhclient: 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  dhclient started with pid 5525 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  9 13:42:00 linux-dt NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Nov  9 13:42:00 linux-dt dhclient: Listening on LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:42:00 linux-dt dhclient: Sending on   LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:42:00 linux-dt dhclient: Sending on   Socket/fallback
Nov  9 13:42:04 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

Nov  9 13:42:11 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Nov  9 13:42:15 linux-dt kernel: [  177.004043] wlan0: no IPv6 routers present
Nov  9 13:42:30 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov  9 13:42:36 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 4 
Nov  9 13:42:36 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 13:42:43 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Nov  9 13:42:45 linux-dt NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5525 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'ssid-name'. 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov  9 13:42:45 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  9 13:42:56 linux-dt NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) failed for access point (ssid-name) 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Marking connection 'ssid-name' invalid. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) failed. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) starting connection 'ssid-name' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): access point 'ssid-name' has security, but secrets are required. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): connection 'ssid-name' has security, and secrets exist.  No new secrets needed. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: added 'ssid' value 'ssid-name' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  9 13:42:56 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Nov  9 13:42:57 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ssid-name'. 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  dhclient started with pid 5613 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  9 13:43:01 linux-dt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  9 13:43:01 linux-dt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  9 13:43:01 linux-dt dhclient: All rights reserved.
Nov  9 13:43:01 linux-dt dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  9 13:43:01 linux-dt dhclient: 
Nov  9 13:43:01 linux-dt NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Nov  9 13:43:01 linux-dt dhclient: Listening on LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:43:01 linux-dt dhclient: Sending on   LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:43:01 linux-dt dhclient: Sending on   Socket/fallback
Nov  9 13:43:04 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov  9 13:43:11 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  9 13:43:19 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Nov  9 13:43:36 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  9 13:43:44 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov  9 13:43:46 linux-dt NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5613 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'ssid-name'. 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov  9 13:43:46 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  9 13:43:50 linux-dt NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Nov  9 13:43:50 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Nov  9 13:43:50 linux-dt NetworkManager: <info>  Activation (wlan0) failed for access point (ssid-name) 
Nov  9 13:43:50 linux-dt NetworkManager: <info>  Marking connection 'ssid-name' invalid. 
Nov  9 13:43:50 linux-dt NetworkManager: <info>  Activation (wlan0) failed. 
Nov  9 13:43:50 linux-dt NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Nov  9 13:43:50 linux-dt NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Nov  9 13:43:54 linux-dt kernel: [  276.327005] at76_usb: 1777: assertion dev->curr_bss == NULL failed

Nov  9 13:45:04 linux-dt kernel: [  346.786259] at76_usb: 1777: assertion dev->curr_bss == NULL failed
Nov  9 13:45:19 linux-dt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  9 13:45:19 linux-dt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  9 13:45:19 linux-dt dhclient: All rights reserved.
Nov  9 13:45:19 linux-dt dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  9 13:45:19 linux-dt dhclient: 
Nov  9 13:45:20 linux-dt dhclient: Listening on LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:45:20 linux-dt dhclient: Sending on   LPF/wlan0/00:31:47:cf:28:40
Nov  9 13:45:20 linux-dt dhclient: Sending on   Socket/fallback
Nov  9 13:45:21 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  9 13:45:24 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  9 13:45:32 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov  9 13:45:45 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Nov  9 13:46:02 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov  9 13:46:15 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov  9 13:46:22 linux-dt dhclient: No DHCPOFFERS received.
Nov  9 13:46:22 linux-dt dhclient: No working leases in persistent database - sleeping.
Nov  9 13:46:22 linux-dt avahi-autoipd(wlan0)[5684]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Nov  9 13:46:22 linux-dt avahi-autoipd(wlan0)[5684]: Successfully called chroot().
Nov  9 13:46:22 linux-dt avahi-autoipd(wlan0)[5684]: Successfully dropped root privileges.
Nov  9 13:46:22 linux-dt avahi-autoipd(wlan0)[5684]: Starting with address 169.254.5.104
Nov  9 13:46:27 linux-dt avahi-autoipd(wlan0)[5684]: Callout BIND, address 169.254.5.104 on interface wlan0
Nov  9 13:46:31 linux-dt avahi-autoipd(wlan0)[5684]: Successfully claimed IP address 169.254.5.104
Nov  9 13:46:41 linux-dt avahi-autoipd(wlan0)[5684]: Failed to parse incoming ARP packet.
Nov  9 13:46:43 linux-dt last message repeated 2 times
Nov  9 13:47:13 linux-dt dhclient: receive_packet failed on wlan0: Network is down
Nov  9 13:47:13 linux-dt avahi-autoipd(wlan0)[5684]: SIOCSIFFLAGS failed: Permission denied
Nov  9 13:47:13 linux-dt avahi-autoipd(wlan0)[5684]: Callout STOP, address 169.254.5.104 on interface wlan0
Nov  9 13:47:13 linux-dt avahi-autoipd(wlan0)[5685]: client: RTNETLINK answers: No such process
Nov  9 13:47:33 linux-dt kernel: [  495.728104] wlan0: no IPv6 routers present
Nov  9 13:47:43 linux-dt kernel: [  505.673761] at76_usb: 1777: assertion dev->curr_bss == NULL failed
Nov  9 13:47:55 linux-dt kernel: [  517.513795] at76_usb: 1777: assertion dev->curr_bss == NULL failed
Nov  9 13:52:36 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Nov  9 13:52:41 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Nov  9 13:52:46 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Nov  9 13:52:55 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Nov  9 13:53:13 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Nov  9 13:53:29 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  9 13:53:37 linux-dt dhclient: No DHCPOFFERS received.
Nov  9 13:53:37 linux-dt dhclient: No working leases in persistent database - sleeping.
Nov  9 13:53:37 linux-dt avahi-autoipd(wlan0)[5736]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Nov  9 13:53:37 linux-dt avahi-autoipd(wlan0)[5736]: Successfully called chroot().
Nov  9 13:53:37 linux-dt avahi-autoipd(wlan0)[5736]: Successfully dropped root privileges.
Nov  9 13:53:37 linux-dt avahi-autoipd(wlan0)[5736]: Starting with address 169.254.5.104
Nov  9 13:53:37 linux-dt avahi-autoipd(wlan0)[5736]: Routable address already assigned, sleeping.
Nov  9 13:57:43 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov  9 13:57:50 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Nov  9 13:58:05 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov  9 13:58:17 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov  9 13:58:30 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Nov  9 13:58:41 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  9 13:58:44 linux-dt dhclient: No DHCPOFFERS received.
Nov  9 13:58:44 linux-dt dhclient: No working leases in persistent database - sleeping.
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) starting connection 'ssid-name' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): access point 'ssid-name' has security, but secrets are required. 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): connection 'ssid-name' has security, and secrets exist.  No new secrets needed. 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: added 'ssid' value 'ssid-name' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  9 14:00:33 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ssid-name'. 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov  9 14:00:34 linux-dt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  9 14:00:34 linux-dt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  9 14:00:34 linux-dt dhclient: All rights reserved.
Nov  9 14:00:34 linux-dt dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  9 14:00:34 linux-dt dhclient: 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  dhclient started with pid 5771 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  9 14:00:34 linux-dt NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Nov  9 14:00:34 linux-dt dhclient: Listening on LPF/wlan0/00:31:47:cf:28:40
Nov  9 14:00:34 linux-dt dhclient: Sending on   LPF/wlan0/00:31:47:cf:28:40
Nov  9 14:00:34 linux-dt dhclient: Sending on   Socket/fallback
Nov  9 14:00:34 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Nov  9 14:00:36 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 4 
Nov  9 14:00:36 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 14:00:36 linux-dt kernel: [ 1278.052097] at76_usb: 2515: assertion dev->istate == INIT failed
Nov  9 14:00:37 linux-dt kernel: [ 1279.769728] at76_usb: 1777: assertion dev->curr_bss == NULL failed
Nov  9 14:00:38 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Nov  9 14:00:38 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 4 
Nov  9 14:00:38 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 14:00:44 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov  9 14:00:56 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  9 14:01:04 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Nov  9 14:01:14 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov  9 14:01:19 linux-dt NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5771 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'ssid-name'. 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov  9 14:01:19 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): connection 'ssid-name' has security, and secrets exist.  No new secrets needed. 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: added 'ssid' value 'ssid-name' 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  9 14:01:23 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Nov  9 14:01:24 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ssid-name'. 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov  9 14:01:28 linux-dt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  9 14:01:28 linux-dt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  9 14:01:28 linux-dt dhclient: All rights reserved.
Nov  9 14:01:28 linux-dt dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  9 14:01:28 linux-dt dhclient: 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  dhclient started with pid 5786 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  9 14:01:28 linux-dt NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Nov  9 14:01:28 linux-dt dhclient: Listening on LPF/wlan0/00:31:47:cf:28:40
Nov  9 14:01:28 linux-dt dhclient: Sending on   LPF/wlan0/00:31:47:cf:28:40
Nov  9 14:01:28 linux-dt dhclient: Sending on   Socket/fallback
Nov  9 14:01:30 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  9 14:01:33 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Nov  9 14:01:37 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Nov  9 14:01:48 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Nov  9 14:01:57 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Nov  9 14:02:08 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Nov  9 14:02:13 linux-dt NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5786 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'ssid-name'. 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov  9 14:02:13 linux-dt NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  9 14:02:16 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 4 
Nov  9 14:02:16 linux-dt NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov  9 14:02:17 linux-dt NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Nov  9 14:02:17 linux-dt NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Nov  9 14:02:17 linux-dt NetworkManager: <info>  Activation (wlan0) failed for access point (ssid-name) 
Nov  9 14:02:17 linux-dt NetworkManager: <info>  Marking connection 'ssid-name' invalid. 
Nov  9 14:02:17 linux-dt NetworkManager: <info>  Activation (wlan0) failed. 
Nov  9 14:02:17 linux-dt NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Nov  9 14:02:17 linux-dt NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Nov  9 14:02:17 linux-dt NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Nov  9 14:02:17 linux-dt avahi-autoipd(wlan0)[5736]: No longer a routable address configured, restarting probe process.
Nov  9 14:02:21 linux-dt kernel: [ 1383.473442] at76_usb: 1777: assertion dev->curr_bss == NULL failed
Nov  9 14:02:24 linux-dt avahi-autoipd(wlan0)[5736]: Callout BIND, address 169.254.5.104 on interface wlan0
Nov  9 14:02:28 linux-dt avahi-autoipd(wlan0)[5736]: Successfully claimed IP address 169.254.5.104
Nov  9 14:05:32 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  9 14:05:35 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  9 14:05:43 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Nov  9 14:05:54 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Nov  9 14:06:04 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Nov  9 14:06:19 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Nov  9 14:06:33 linux-dt dhclient: No DHCPOFFERS received.
Nov  9 14:06:33 linux-dt dhclient: No working leases in persistent database - sleeping.
Nov  9 14:12:14 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Nov  9 14:12:18 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Nov  9 14:12:28 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov  9 14:12:40 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Nov  9 14:12:54 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov  9 14:13:06 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Nov  9 14:13:15 linux-dt dhclient: No DHCPOFFERS received.
Nov  9 14:13:15 linux-dt dhclient: No working leases in persistent database - sleeping.
Nov  9 14:17:28 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Nov  9 14:17:33 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov  9 14:17:40 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Nov  9 14:17:55 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Nov  9 14:18:13 linux-dt dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Nov  9 14:18:29 linux-dt dhclient: No DHCPOFFERS received.
Nov  9 14:18:29 linux-dt dhclient: No working leases in persistent database - sleeping.

```

---

### Post by cwall on 2009-01-23
Any chance your issue was resolved?

---

### Post by Pixtu on 2009-02-03
I'm afraid not. I gave up trying to get my old Belkin adapter to work.

I think it should but couldn't work out what was wrong and with a disappointingly complete lack of support I purchased a new adapter.

I'm frustrated that I couldn't resolve the Belkin issue, but for less than £9 all my networking problems have been resolved. So I guess it has saved me a lot of time wasting but I felt that if I could have resolved the problems I would also have learnt quite a lot in the process.

---

