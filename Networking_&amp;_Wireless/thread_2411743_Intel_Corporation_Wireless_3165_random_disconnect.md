---
title: "Intel Corporation Wireless 3165 random disconnect"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by darthvader1234 on 2019-02-03
Hi I have the same issue with Intel Wireless 3165 except for the part that I am using ubuntu 16.04

My error report is here:


```
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_get_uint32: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_UINT32)' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_get_uint32: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_UINT32)' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: (whoopsie:947): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Feb  3 11:41:44 anand-Inspiron-13-5378 whoopsie[947]: [11:41:44] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Feb  3 11:41:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549174309.6312] manager: WiFi hardware radio set enabled
Feb  3 11:41:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549174309.6313] manager: WWAN hardware radio set enabled
Feb  3 11:42:04 anand-Inspiron-13-5378 kernel: [  759.034236] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:42:04 anand-Inspiron-13-5378 kernel: [  759.034290] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:42:04 anand-Inspiron-13-5378 kernel: [  759.034295] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:42:04 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 11:42:37 anand-Inspiron-13-5378 kernel: [  792.020390] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:42:37 anand-Inspiron-13-5378 kernel: [  792.020415] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:42:37 anand-Inspiron-13-5378 kernel: [  792.020417] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:43:20 anand-Inspiron-13-5378 kernel: [  835.037565] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:43:20 anand-Inspiron-13-5378 kernel: [  835.037586] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:43:20 anand-Inspiron-13-5378 kernel: [  835.037589] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:44:13 anand-Inspiron-13-5378 kernel: [  888.051654] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:44:13 anand-Inspiron-13-5378 kernel: [  888.051682] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:44:13 anand-Inspiron-13-5378 kernel: [  888.051685] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:44:13 anand-Inspiron-13-5378 wpa_supplicant[933]: message repeated 3 times: [ wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
Feb  3 11:44:42 anand-Inspiron-13-5378 systemd[1]: Starting Cleanup of Temporary Directories...
Feb  3 11:44:42 anand-Inspiron-13-5378 systemd-tmpfiles[3086]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Feb  3 11:44:42 anand-Inspiron-13-5378 systemd[1]: Started Cleanup of Temporary Directories.
Feb  3 11:45:16 anand-Inspiron-13-5378 kernel: [  951.063235] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:45:16 anand-Inspiron-13-5378 kernel: [  951.063257] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:45:16 anand-Inspiron-13-5378 kernel: [  951.063259] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:45:16 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 11:46:19 anand-Inspiron-13-5378 kernel: [ 1014.021366] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:46:19 anand-Inspiron-13-5378 kernel: [ 1014.021447] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:46:19 anand-Inspiron-13-5378 kernel: [ 1014.021459] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:47:22 anand-Inspiron-13-5378 kernel: [ 1077.023234] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:47:22 anand-Inspiron-13-5378 kernel: [ 1077.023251] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:47:22 anand-Inspiron-13-5378 kernel: [ 1077.023253] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:48:25 anand-Inspiron-13-5378 kernel: [ 1140.052264] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:48:25 anand-Inspiron-13-5378 kernel: [ 1140.052346] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:48:25 anand-Inspiron-13-5378 kernel: [ 1140.052358] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:49:28 anand-Inspiron-13-5378 kernel: [ 1203.060909] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:49:28 anand-Inspiron-13-5378 kernel: [ 1203.060945] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:49:28 anand-Inspiron-13-5378 kernel: [ 1203.060950] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:50:31 anand-Inspiron-13-5378 kernel: [ 1266.040295] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:50:31 anand-Inspiron-13-5378 kernel: [ 1266.040375] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:50:31 anand-Inspiron-13-5378 kernel: [ 1266.040392] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:51:34 anand-Inspiron-13-5378 kernel: [ 1329.021272] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:51:34 anand-Inspiron-13-5378 kernel: [ 1329.021358] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:51:34 anand-Inspiron-13-5378 kernel: [ 1329.021371] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:52:37 anand-Inspiron-13-5378 kernel: [ 1392.062852] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:52:37 anand-Inspiron-13-5378 kernel: [ 1392.062940] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:52:37 anand-Inspiron-13-5378 kernel: [ 1392.062965] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:53:40 anand-Inspiron-13-5378 kernel: [ 1455.083589] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:53:40 anand-Inspiron-13-5378 kernel: [ 1455.083730] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:53:40 anand-Inspiron-13-5378 kernel: [ 1455.083748] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:54:43 anand-Inspiron-13-5378 kernel: [ 1518.021254] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:54:43 anand-Inspiron-13-5378 kernel: [ 1518.021361] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:54:43 anand-Inspiron-13-5378 kernel: [ 1518.021375] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:55:46 anand-Inspiron-13-5378 kernel: [ 1581.074615] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:55:46 anand-Inspiron-13-5378 kernel: [ 1581.074698] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:55:46 anand-Inspiron-13-5378 kernel: [ 1581.074716] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:56:49 anand-Inspiron-13-5378 kernel: [ 1644.021397] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:56:49 anand-Inspiron-13-5378 kernel: [ 1644.021478] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:56:49 anand-Inspiron-13-5378 kernel: [ 1644.021494] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:57:18 anand-Inspiron-13-5378 kernel: [ 1673.188256] usb 1-2: new high-speed USB device number 7 using xhci_hcd
Feb  3 11:57:18 anand-Inspiron-13-5378 kernel: [ 1673.365291] usb 1-2: New USB device found, idVendor=0b95, idProduct=772a
Feb  3 11:57:18 anand-Inspiron-13-5378 kernel: [ 1673.365300] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb  3 11:57:18 anand-Inspiron-13-5378 kernel: [ 1673.365307] usb 1-2: SerialNumber: DE9A0E
Feb  3 11:56:49 anand-Inspiron-13-5378 wpa_supplicant[933]: message repeated 11 times: [ wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
Feb  3 11:57:19 anand-Inspiron-13-5378 mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2"
Feb  3 11:57:19 anand-Inspiron-13-5378 mtp-probe: bus: 1, device: 7 was not an MTP device
Feb  3 11:57:20 anand-Inspiron-13-5378 kernel: [ 1675.280531] asix 1-2:1.0 eth0: register 'asix' at usb-0000:00:14.0-2, ASIX AX88772 USB 2.0 Ethernet, 00:50:b6:de:9a:0e
Feb  3 11:57:20 anand-Inspiron-13-5378 kernel: [ 1675.280819] usbcore: registered new interface driver asix
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549175240.9071] device (eth0): failed to find device 3 'eth0' with udev
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9114] manager: (eth0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Feb  3 11:57:20 anand-Inspiron-13-5378 kernel: [ 1675.336772] asix 1-2:1.0 enx0050b6de9a0e: renamed from eth0
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9787] device (eth0): interface index 3 renamed iface from 'eth0' to 'enx0050b6de9a0e'
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9897] devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enx0050b6de9a0e, iface: enx0050b6de9a0e)
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9897] device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enx0050b6de9a0e, iface: enx0050b6de9a0e): no ifupdown configuration found.
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9901] device (enx0050b6de9a0e): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb  3 11:57:20 anand-Inspiron-13-5378 kernel: [ 1675.365414] IPv6: ADDRCONF(NETDEV_UP): enx0050b6de9a0e: link is not ready
Feb  3 11:57:20 anand-Inspiron-13-5378 kernel: [ 1675.368048] IPv6: ADDRCONF(NETDEV_UP): enx0050b6de9a0e: link is not ready
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9956] keyfile: add connection in-memory (a93d1bbe-2ccd-3e8e-956e-c181cfb616e6,"Wired connection 1")
Feb  3 11:57:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175240.9968] settings: (enx0050b6de9a0e): created default wired connection 'Wired connection 1'
Feb  3 11:57:22 anand-Inspiron-13-5378 kernel: [ 1676.886790] IPv6: ADDRCONF(NETDEV_CHANGE): enx0050b6de9a0e: link becomes ready
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5126] device (enx0050b6de9a0e): link connected
Feb  3 11:57:22 anand-Inspiron-13-5378 kernel: [ 1676.890726] asix 1-2:1.0 enx0050b6de9a0e: link up, 100Mbps, full-duplex, lpa 0x41E1
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5256] device (enx0050b6de9a0e): state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5286] policy: auto-activating connection 'Wired connection 1'
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5403] device (enx0050b6de9a0e): Activation: starting connection 'Wired connection 1' (a93d1bbe-2ccd-3e8e-956e-c181cfb616e6)
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5410] device (enx0050b6de9a0e): state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5416] manager: NetworkManager state is now CONNECTING
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5437] device (enx0050b6de9a0e): state change: prepare -> config (reason 'none') [40 50 0]
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5458] device (enx0050b6de9a0e): state change: config -> ip-config (reason 'none') [50 70 0]
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5492] dhcp4 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:57:22 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175242.5532] dhcp4 (enx0050b6de9a0e): dhclient started with pid 3238
Feb  3 11:57:22 anand-Inspiron-13-5378 dhclient[3238]: DHCPREQUEST of 10.22.20.122 on enx0050b6de9a0e to 255.255.255.255 port 67 (xid=0x4d4a1095)
Feb  3 11:57:23 anand-Inspiron-13-5378 ModemManager[770]: <info>  Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2': not supported by any plugin
Feb  3 11:57:23 anand-Inspiron-13-5378 avahi-daemon[780]: Joining mDNS multicast group on interface enx0050b6de9a0e.IPv6 with address fe80::b162:e945:4e0c:d7a2.
Feb  3 11:57:23 anand-Inspiron-13-5378 avahi-daemon[780]: New relevant interface enx0050b6de9a0e.IPv6 for mDNS.
Feb  3 11:57:23 anand-Inspiron-13-5378 avahi-daemon[780]: Registering new address record for fe80::b162:e945:4e0c:d7a2 on enx0050b6de9a0e.*.
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.7477] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.7532] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3250
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.7849] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3254
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.7871] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3250
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.7873] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.7923] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175243.8063] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3255
Feb  3 11:57:23 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549175243.8116] (pid 3250) unhandled DHCP event for interface enx0050b6de9a0e
Feb  3 11:57:23 anand-Inspiron-13-5378 whoopsie[947]: [11:57:23] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Feb  3 11:57:24 anand-Inspiron-13-5378 dhclient[3255]: XMT: Info-Request on enx0050b6de9a0e, interval 960ms.
Feb  3 11:57:24 anand-Inspiron-13-5378 whoopsie[947]: [11:57:24] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Feb  3 11:57:25 anand-Inspiron-13-5378 dhclient[3255]: XMT: Info-Request on enx0050b6de9a0e, interval 1930ms.
Feb  3 11:57:26 anand-Inspiron-13-5378 dhclient[3238]: DHCPREQUEST of 10.22.20.122 on enx0050b6de9a0e to 255.255.255.255 port 67 (xid=0x4d4a1095)
Feb  3 11:57:26 anand-Inspiron-13-5378 dhclient[3238]: DHCPACK of 10.22.20.122 from 10.22.23.254
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0365]   address 10.22.20.122
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0366]   plen 22 (255.255.252.0)
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0367]   gateway 10.22.23.254
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0367]   server identifier 10.24.4.8
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0368]   lease time 26881
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0369]   nameserver '10.24.0.193'
Feb  3 11:57:26 anand-Inspiron-13-5378 avahi-daemon[780]: Joining mDNS multicast group on interface enx0050b6de9a0e.IPv4 with address 10.22.20.122.
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0370]   nameserver '10.24.0.194'
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0370]   domain name 'iitmlan'
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0371] dhcp4 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 11:57:26 anand-Inspiron-13-5378 avahi-daemon[780]: New relevant interface enx0050b6de9a0e.IPv4 for mDNS.
Feb  3 11:57:26 anand-Inspiron-13-5378 avahi-daemon[780]: Registering new address record for 10.22.20.122 on enx0050b6de9a0e.IPv4.
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0594] device (enx0050b6de9a0e): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0627] device (enx0050b6de9a0e): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0639] device (enx0050b6de9a0e): state change: secondaries -> activated (reason 'none') [90 100 0]
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.0645] manager: NetworkManager state is now CONNECTED_LOCAL
Feb  3 11:57:26 anand-Inspiron-13-5378 dhclient[3238]: bound to 10.22.20.122 -- renewal in 11037 seconds.
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.2144] manager: NetworkManager state is now CONNECTED_GLOBAL
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.2149] policy: set 'Wired connection 1' (enx0050b6de9a0e) as default for IPv4 routing and DNS
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.2153] policy: set 'Wired connection 1' (enx0050b6de9a0e) as default for IPv6 routing and DNS
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.2531] dns-plugin[0x15a48e0]: starting dnsmasq...
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.2639] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: started, version 2.75 cache disabled
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: DBus support enabled: connected to system bus
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: warning: no upstream servers configured
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.3540] device (enx0050b6de9a0e): Activation: successful, device activated.
Feb  3 11:57:26 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 11:57:26 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175246.3578] dnsmasq[0x15a48e0]: dnsmasq appeared as :1.104
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 11:57:26 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 11:57:26 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 11:57:26 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 11:57:26 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 11:57:26 anand-Inspiron-13-5378 nm-dispatcher: req:1 'up' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 11:57:26 anand-Inspiron-13-5378 nm-dispatcher: req:1 'up' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 11:57:26 anand-Inspiron-13-5378 whoopsie[947]: [11:57:26] online
Feb  3 11:57:27 anand-Inspiron-13-5378 dhclient[3255]: XMT: Info-Request on enx0050b6de9a0e, interval 3940ms.
Feb  3 11:57:28 anand-Inspiron-13-5378 kernel: [ 1682.852990] acpi INT3400:00: Unsupported event [0x86]
Feb  3 11:57:31 anand-Inspiron-13-5378 dhclient[3255]: XMT: Info-Request on enx0050b6de9a0e, interval 7590ms.
Feb  3 11:57:33 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175253.3979] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3414
Feb  3 11:57:33 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175253.3989] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3255
Feb  3 11:57:33 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175253.3991] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:57:33 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175253.4016] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:57:33 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175253.4062] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3415
Feb  3 11:57:33 anand-Inspiron-13-5378 dhclient[3415]: XMT: Solicit on enx0050b6de9a0e, interval 1030ms.
Feb  3 11:57:34 anand-Inspiron-13-5378 dhclient[3415]: XMT: Solicit on enx0050b6de9a0e, interval 2080ms.
Feb  3 11:57:36 anand-Inspiron-13-5378 dhclient[3415]: XMT: Solicit on enx0050b6de9a0e, interval 4080ms.
Feb  3 11:57:41 anand-Inspiron-13-5378 dhclient[3415]: XMT: Solicit on enx0050b6de9a0e, interval 8010ms.
Feb  3 11:57:49 anand-Inspiron-13-5378 dhclient[3415]: XMT: Solicit on enx0050b6de9a0e, interval 15220ms.
Feb  3 11:57:52 anand-Inspiron-13-5378 kernel: [ 1707.022355] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:57:52 anand-Inspiron-13-5378 kernel: [ 1707.022380] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:57:52 anand-Inspiron-13-5378 kernel: [ 1707.022382] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:57:52 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 11:58:04 anand-Inspiron-13-5378 dhclient[3415]: XMT: Solicit on enx0050b6de9a0e, interval 30280ms.
Feb  3 11:58:18 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549175298.6271] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 11:58:18 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175298.6272] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 11:58:18 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175298.6295] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3415
Feb  3 11:58:18 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175298.6296] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 11:58:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175320.6704] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:58:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175320.6752] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3444
Feb  3 11:58:41 anand-Inspiron-13-5378 dhclient[3444]: XMT: Info-Request on enx0050b6de9a0e, interval 1000ms.
Feb  3 11:58:42 anand-Inspiron-13-5378 dhclient[3444]: XMT: Info-Request on enx0050b6de9a0e, interval 1940ms.
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.6083] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3445
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.6089] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3444
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.6090] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.6094] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.6104] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3446
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.7700] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3452
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.7710] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3446
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.7712] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.7734] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:58:43 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175323.7776] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3453
Feb  3 11:58:44 anand-Inspiron-13-5378 dhclient[3453]: XMT: Info-Request on enx0050b6de9a0e, interval 970ms.
Feb  3 11:58:45 anand-Inspiron-13-5378 dhclient[3453]: XMT: Info-Request on enx0050b6de9a0e, interval 2000ms.
Feb  3 11:58:47 anand-Inspiron-13-5378 dhclient[3453]: XMT: Info-Request on enx0050b6de9a0e, interval 4010ms.
Feb  3 11:58:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175329.3210] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3454
Feb  3 11:58:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175329.3221] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3453
Feb  3 11:58:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175329.3223] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:58:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175329.3258] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:58:49 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175329.3303] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3455
Feb  3 11:58:49 anand-Inspiron-13-5378 dhclient[3455]: XMT: Solicit on enx0050b6de9a0e, interval 1050ms.
Feb  3 11:58:50 anand-Inspiron-13-5378 dhclient[3455]: XMT: Solicit on enx0050b6de9a0e, interval 2150ms.
Feb  3 11:58:52 anand-Inspiron-13-5378 dhclient[3455]: XMT: Solicit on enx0050b6de9a0e, interval 4340ms.
Feb  3 11:58:55 anand-Inspiron-13-5378 kernel: [ 1770.020991] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:58:55 anand-Inspiron-13-5378 kernel: [ 1770.021052] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:58:55 anand-Inspiron-13-5378 kernel: [ 1770.021067] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:58:55 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 11:58:57 anand-Inspiron-13-5378 dhclient[3455]: XMT: Solicit on enx0050b6de9a0e, interval 8950ms.
Feb  3 11:59:05 anand-Inspiron-13-5378 dhclient[3455]: XMT: Solicit on enx0050b6de9a0e, interval 18770ms.
Feb  3 11:59:06 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175346.9357] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3461
Feb  3 11:59:06 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175346.9367] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3455
Feb  3 11:59:06 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175346.9368] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:59:06 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175346.9389] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:59:06 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175346.9432] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3462
Feb  3 11:59:07 anand-Inspiron-13-5378 dhclient[3462]: XMT: Info-Request on enx0050b6de9a0e, interval 1030ms.
Feb  3 11:59:08 anand-Inspiron-13-5378 dhclient[3462]: XMT: Info-Request on enx0050b6de9a0e, interval 1980ms.
Feb  3 11:59:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175350.0071] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3463
Feb  3 11:59:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175350.0080] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3462
Feb  3 11:59:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175350.0081] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:59:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175350.0099] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:59:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175350.0134] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3464
Feb  3 11:59:10 anand-Inspiron-13-5378 dhclient[3464]: XMT: Solicit on enx0050b6de9a0e, interval 1020ms.
Feb  3 11:59:11 anand-Inspiron-13-5378 dhclient[3464]: XMT: Solicit on enx0050b6de9a0e, interval 1950ms.
Feb  3 11:59:13 anand-Inspiron-13-5378 dhclient[3464]: XMT: Solicit on enx0050b6de9a0e, interval 3800ms.
Feb  3 11:59:17 anand-Inspiron-13-5378 dhclient[3464]: XMT: Solicit on enx0050b6de9a0e, interval 7630ms.
Feb  3 11:59:24 anand-Inspiron-13-5378 dhclient[3464]: XMT: Solicit on enx0050b6de9a0e, interval 15190ms.
Feb  3 11:59:39 anand-Inspiron-13-5378 dhclient[3464]: XMT: Solicit on enx0050b6de9a0e, interval 30360ms.
Feb  3 11:59:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175388.0178] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3492
Feb  3 11:59:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175388.0187] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3464
Feb  3 11:59:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175388.0189] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:59:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175388.0208] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:59:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175388.0251] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3493
Feb  3 11:59:48 anand-Inspiron-13-5378 dhclient[3493]: XMT: Info-Request on enx0050b6de9a0e, interval 1070ms.
Feb  3 11:59:49 anand-Inspiron-13-5378 dhclient[3493]: XMT: Info-Request on enx0050b6de9a0e, interval 2180ms.
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.1771] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3494
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.1782] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3493
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.1783] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.1806] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.1851] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3495
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.3688] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3501
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.3698] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3495
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.3700] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.3724] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:59:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175391.3771] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3502
Feb  3 11:59:52 anand-Inspiron-13-5378 dhclient[3502]: XMT: Info-Request on enx0050b6de9a0e, interval 1050ms.
Feb  3 11:59:53 anand-Inspiron-13-5378 dhclient[3502]: XMT: Info-Request on enx0050b6de9a0e, interval 2030ms.
Feb  3 11:59:55 anand-Inspiron-13-5378 dhclient[3502]: XMT: Info-Request on enx0050b6de9a0e, interval 4120ms.
Feb  3 11:59:56 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175396.9125] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3505
Feb  3 11:59:56 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175396.9133] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3502
Feb  3 11:59:56 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175396.9134] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 11:59:56 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175396.9138] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 11:59:56 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175396.9147] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3506
Feb  3 11:59:57 anand-Inspiron-13-5378 dhclient[3506]: XMT: Solicit on enx0050b6de9a0e, interval 1010ms.
Feb  3 11:59:58 anand-Inspiron-13-5378 kernel: [ 1833.022283] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 11:59:58 anand-Inspiron-13-5378 kernel: [ 1833.022375] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 11:59:58 anand-Inspiron-13-5378 kernel: [ 1833.022388] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 11:59:58 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 11:59:58 anand-Inspiron-13-5378 dhclient[3506]: XMT: Solicit on enx0050b6de9a0e, interval 1940ms.
Feb  3 12:00:00 anand-Inspiron-13-5378 dhclient[3506]: XMT: Solicit on enx0050b6de9a0e, interval 3890ms.
Feb  3 12:00:04 anand-Inspiron-13-5378 dhclient[3506]: XMT: Solicit on enx0050b6de9a0e, interval 7630ms.
Feb  3 12:00:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175410.3868] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3511
Feb  3 12:00:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175410.3879] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3506
Feb  3 12:00:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175410.3881] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:00:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175410.3905] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:00:10 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175410.3950] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3512
Feb  3 12:00:11 anand-Inspiron-13-5378 dhclient[3512]: XMT: Info-Request on enx0050b6de9a0e, interval 1040ms.
Feb  3 12:00:12 anand-Inspiron-13-5378 dhclient[3512]: XMT: Info-Request on enx0050b6de9a0e, interval 2100ms.
Feb  3 12:00:14 anand-Inspiron-13-5378 dhclient[3512]: XMT: Info-Request on enx0050b6de9a0e, interval 4080ms.
Feb  3 12:00:14 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175414.6727] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3514
Feb  3 12:00:14 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175414.6738] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3512
Feb  3 12:00:14 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175414.6739] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:00:14 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175414.6755] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:00:14 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175414.6766] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3515
Feb  3 12:00:15 anand-Inspiron-13-5378 dhclient[3515]: XMT: Solicit on enx0050b6de9a0e, interval 1080ms.
Feb  3 12:00:16 anand-Inspiron-13-5378 dhclient[3515]: XMT: Solicit on enx0050b6de9a0e, interval 2160ms.
Feb  3 12:00:18 anand-Inspiron-13-5378 dhclient[3515]: XMT: Solicit on enx0050b6de9a0e, interval 4270ms.
Feb  3 12:00:22 anand-Inspiron-13-5378 dhclient[3515]: XMT: Solicit on enx0050b6de9a0e, interval 8510ms.
Feb  3 12:00:31 anand-Inspiron-13-5378 dhclient[3515]: XMT: Solicit on enx0050b6de9a0e, interval 17370ms.
Feb  3 12:00:48 anand-Inspiron-13-5378 dhclient[3515]: XMT: Solicit on enx0050b6de9a0e, interval 35370ms.
Feb  3 12:00:59 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549175459.6308] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:00:59 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175459.6310] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:00:59 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175459.6335] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3515
Feb  3 12:00:59 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175459.6336] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:01:01 anand-Inspiron-13-5378 kernel: [ 1896.022486] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:01:01 anand-Inspiron-13-5378 kernel: [ 1896.022634] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:01:01 anand-Inspiron-13-5378 kernel: [ 1896.022641] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:01:01 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:01:37 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175497.3140] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:01:37 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175497.3152] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3545
Feb  3 12:01:38 anand-Inspiron-13-5378 dhclient[3545]: XMT: Info-Request on enx0050b6de9a0e, interval 930ms.
Feb  3 12:01:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175498.5673] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3547
Feb  3 12:01:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175498.5688] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3545
Feb  3 12:01:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175498.5690] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:01:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175498.5723] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:01:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175498.5774] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3548
Feb  3 12:01:39 anand-Inspiron-13-5378 dhclient[3548]: XMT: Solicit on enx0050b6de9a0e, interval 1030ms.
Feb  3 12:01:40 anand-Inspiron-13-5378 dhclient[3548]: XMT: Solicit on enx0050b6de9a0e, interval 2060ms.
Feb  3 12:01:42 anand-Inspiron-13-5378 dhclient[3548]: XMT: Solicit on enx0050b6de9a0e, interval 4250ms.
Feb  3 12:01:46 anand-Inspiron-13-5378 dhclient[3548]: XMT: Solicit on enx0050b6de9a0e, interval 8230ms.
Feb  3 12:01:54 anand-Inspiron-13-5378 dhclient[3548]: XMT: Solicit on enx0050b6de9a0e, interval 16500ms.
Feb  3 12:02:04 anand-Inspiron-13-5378 kernel: [ 1959.021133] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:02:04 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:02:04 anand-Inspiron-13-5378 kernel: [ 1959.021297] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:02:04 anand-Inspiron-13-5378 kernel: [ 1959.021312] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:02:11 anand-Inspiron-13-5378 dhclient[3548]: XMT: Solicit on enx0050b6de9a0e, interval 32190ms.
Feb  3 12:02:23 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549175543.6261] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:02:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175543.6262] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:02:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175543.6287] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3548
Feb  3 12:02:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175543.6288] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:03:07 anand-Inspiron-13-5378 kernel: [ 2022.021080] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:03:07 anand-Inspiron-13-5378 kernel: [ 2022.021184] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:03:07 anand-Inspiron-13-5378 kernel: [ 2022.021215] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:03:07 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:04:10 anand-Inspiron-13-5378 kernel: [ 2085.022361] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:04:10 anand-Inspiron-13-5378 kernel: [ 2085.022451] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:04:10 anand-Inspiron-13-5378 kernel: [ 2085.022464] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:04:10 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:05:02 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175702.8461] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:05:02 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175702.8509] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3626
Feb  3 12:05:03 anand-Inspiron-13-5378 dhclient[3626]: XMT: Info-Request on enx0050b6de9a0e, interval 1010ms.
Feb  3 12:05:04 anand-Inspiron-13-5378 dhclient[3626]: XMT: Info-Request on enx0050b6de9a0e, interval 2080ms.
Feb  3 12:05:06 anand-Inspiron-13-5378 dhclient[3626]: XMT: Info-Request on enx0050b6de9a0e, interval 4330ms.
Feb  3 12:05:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175709.4336] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3627
Feb  3 12:05:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175709.4347] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3626
Feb  3 12:05:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175709.4348] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:05:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175709.4369] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:05:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175709.4418] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3628
Feb  3 12:05:09 anand-Inspiron-13-5378 dhclient[3628]: XMT: Solicit on enx0050b6de9a0e, interval 1010ms.
Feb  3 12:05:11 anand-Inspiron-13-5378 dhclient[3628]: XMT: Solicit on enx0050b6de9a0e, interval 2000ms.
Feb  3 12:05:13 anand-Inspiron-13-5378 dhclient[3628]: XMT: Solicit on enx0050b6de9a0e, interval 3890ms.
Feb  3 12:05:13 anand-Inspiron-13-5378 kernel: [ 2148.024177] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:05:13 anand-Inspiron-13-5378 kernel: [ 2148.024269] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:05:13 anand-Inspiron-13-5378 kernel: [ 2148.024284] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:05:13 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:05:16 anand-Inspiron-13-5378 dhclient[3628]: XMT: Solicit on enx0050b6de9a0e, interval 7460ms.
Feb  3 12:05:24 anand-Inspiron-13-5378 dhclient[3628]: XMT: Solicit on enx0050b6de9a0e, interval 14630ms.
Feb  3 12:05:39 anand-Inspiron-13-5378 dhclient[3628]: XMT: Solicit on enx0050b6de9a0e, interval 28570ms.
Feb  3 12:05:54 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549175754.6260] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:05:54 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175754.6262] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:05:54 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175754.6292] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3628
Feb  3 12:05:54 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175754.6294] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:06:16 anand-Inspiron-13-5378 kernel: [ 2211.021128] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:06:16 anand-Inspiron-13-5378 kernel: [ 2211.021175] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:06:16 anand-Inspiron-13-5378 kernel: [ 2211.021182] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:06:16 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:07:19 anand-Inspiron-13-5378 kernel: [ 2274.021000] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:07:19 anand-Inspiron-13-5378 kernel: [ 2274.021046] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:07:19 anand-Inspiron-13-5378 kernel: [ 2274.021056] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:07:19 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:07:34 anand-Inspiron-13-5378 systemd-timesyncd[586]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Feb  3 12:07:44 anand-Inspiron-13-5378 systemd-timesyncd[586]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Feb  3 12:07:54 anand-Inspiron-13-5378 systemd-timesyncd[586]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Feb  3 12:08:05 anand-Inspiron-13-5378 systemd-timesyncd[586]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
Feb  3 12:08:15 anand-Inspiron-13-5378 systemd-timesyncd[586]: Timed out waiting for reply from [2001:67c:1560:8003::c8]:123 (ntp.ubuntu.com).
Feb  3 12:08:22 anand-Inspiron-13-5378 kernel: [ 2337.026572] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:08:22 anand-Inspiron-13-5378 kernel: [ 2337.026649] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:08:22 anand-Inspiron-13-5378 kernel: [ 2337.026677] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:08:22 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:08:25 anand-Inspiron-13-5378 systemd-timesyncd[586]: Timed out waiting for reply from [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com).
Feb  3 12:08:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175918.1874] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:08:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175918.1919] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3683
Feb  3 12:08:39 anand-Inspiron-13-5378 dhclient[3683]: XMT: Info-Request on enx0050b6de9a0e, interval 910ms.
Feb  3 12:08:39 anand-Inspiron-13-5378 dhclient[3683]: XMT: Info-Request on enx0050b6de9a0e, interval 1750ms.
Feb  3 12:08:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175920.1199] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3684
Feb  3 12:08:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175920.1215] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3683
Feb  3 12:08:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175920.1216] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:08:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175920.1248] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:08:40 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175920.1292] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3685
Feb  3 12:08:40 anand-Inspiron-13-5378 dhclient[3685]: XMT: Solicit on enx0050b6de9a0e, interval 1050ms.
Feb  3 12:08:41 anand-Inspiron-13-5378 dhclient[3685]: XMT: Solicit on enx0050b6de9a0e, interval 2200ms.
Feb  3 12:08:44 anand-Inspiron-13-5378 dhclient[3685]: XMT: Solicit on enx0050b6de9a0e, interval 4410ms.
Feb  3 12:08:44 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175924.7044] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3691
Feb  3 12:08:44 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175924.7055] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3685
Feb  3 12:08:44 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175924.7057] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:08:44 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175924.7081] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:08:44 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175924.7130] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3692
Feb  3 12:08:45 anand-Inspiron-13-5378 dhclient[3692]: XMT: Info-Request on enx0050b6de9a0e, interval 950ms.
Feb  3 12:08:45 anand-Inspiron-13-5378 dhclient[3692]: RCV: Reply message on enx0050b6de9a0e from fe80::e9f5:90b3:7aa2:10f1.
Feb  3 12:08:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175925.4805]   nameserver 'fe80::e9f5:90b3:7aa2:10f1'
Feb  3 12:08:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175925.4807]   domain search 'mshome.net.'
Feb  3 12:08:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175925.4807] dhcp6 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 12:08:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175925.4831] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:08:45 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:08:45 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:08:45 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:08:45 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver fe80::e9f5:90b3:7aa2:10f1%enx0050b6de9a0e#53
Feb  3 12:08:45 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 12:08:45 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 12:08:45 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 12:08:45 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 12:08:45 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 12:08:45 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 12:08:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175925.6445] dhcp6 (enx0050b6de9a0e): client pid 3692 exited with status 0
Feb  3 12:08:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175925.6446] dhcp6 (enx0050b6de9a0e): state changed bound -> done
Feb  3 12:08:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175931.0338] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3741
Feb  3 12:08:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175931.0347] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction
Feb  3 12:08:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175931.0361] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:08:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175931.0395] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3742
Feb  3 12:08:51 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175931.0412] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:08:51 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:08:51 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:08:51 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:08:51 anand-Inspiron-13-5378 dhclient[3742]: XMT: Solicit on enx0050b6de9a0e, interval 1010ms.
Feb  3 12:08:52 anand-Inspiron-13-5378 dhclient[3742]: XMT: Solicit on enx0050b6de9a0e, interval 2070ms.
Feb  3 12:08:54 anand-Inspiron-13-5378 dhclient[3742]: XMT: Solicit on enx0050b6de9a0e, interval 4310ms.
Feb  3 12:08:59 anand-Inspiron-13-5378 dhclient[3742]: XMT: Solicit on enx0050b6de9a0e, interval 8490ms.
Feb  3 12:09:07 anand-Inspiron-13-5378 dhclient[3742]: XMT: Solicit on enx0050b6de9a0e, interval 16910ms.
Feb  3 12:09:19 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175959.5393] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3789
Feb  3 12:09:19 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175959.5403] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3742
Feb  3 12:09:19 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175959.5404] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:09:19 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175959.5425] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:09:19 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175959.5465] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3790
Feb  3 12:09:20 anand-Inspiron-13-5378 dhclient[3790]: XMT: Info-Request on enx0050b6de9a0e, interval 1000ms.
Feb  3 12:09:20 anand-Inspiron-13-5378 dhclient[3790]: RCV: Reply message on enx0050b6de9a0e from fe80::e9f5:90b3:7aa2:10f1.
Feb  3 12:09:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175960.1482]   nameserver 'fe80::e9f5:90b3:7aa2:10f1'
Feb  3 12:09:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175960.1490]   domain search 'mshome.net.'
Feb  3 12:09:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175960.1491] dhcp6 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 12:09:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175960.1513] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:09:20 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:09:20 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:09:20 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:09:20 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver fe80::e9f5:90b3:7aa2:10f1%enx0050b6de9a0e#53
Feb  3 12:09:20 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 12:09:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175960.2313] dhcp6 (enx0050b6de9a0e): client pid 3790 exited with status 0
Feb  3 12:09:20 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175960.2313] dhcp6 (enx0050b6de9a0e): state changed bound -> done
Feb  3 12:09:20 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 12:09:20 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 12:09:20 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 12:09:20 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 12:09:20 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 12:09:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175963.3394] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3840
Feb  3 12:09:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175963.3405] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction
Feb  3 12:09:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175963.3428] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:09:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175963.3479] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3841
Feb  3 12:09:23 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549175963.3516] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:09:23 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:09:23 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:09:23 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:09:24 anand-Inspiron-13-5378 dhclient[3841]: XMT: Solicit on enx0050b6de9a0e, interval 1060ms.
Feb  3 12:09:25 anand-Inspiron-13-5378 dhclient[3841]: XMT: Solicit on enx0050b6de9a0e, interval 2100ms.
Feb  3 12:09:25 anand-Inspiron-13-5378 kernel: [ 2400.020062] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:09:25 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:09:25 anand-Inspiron-13-5378 kernel: [ 2400.020430] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:09:25 anand-Inspiron-13-5378 kernel: [ 2400.020439] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:09:27 anand-Inspiron-13-5378 dhclient[3841]: XMT: Solicit on enx0050b6de9a0e, interval 4310ms.
Feb  3 12:09:31 anand-Inspiron-13-5378 dhclient[3841]: XMT: Solicit on enx0050b6de9a0e, interval 8400ms.
Feb  3 12:09:40 anand-Inspiron-13-5378 dhclient[3841]: XMT: Solicit on enx0050b6de9a0e, interval 17090ms.
Feb  3 12:09:57 anand-Inspiron-13-5378 dhclient[3841]: XMT: Solicit on enx0050b6de9a0e, interval 34320ms.
Feb  3 12:10:08 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549176008.6309] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:10:08 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176008.6310] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:10:08 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176008.6323] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3841
Feb  3 12:10:08 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176008.6325] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:10:28 anand-Inspiron-13-5378 kernel: [ 2463.023777] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:10:28 anand-Inspiron-13-5378 kernel: [ 2463.023826] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:10:28 anand-Inspiron-13-5378 kernel: [ 2463.023838] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:10:28 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.2628] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.2678] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3891
Feb  3 12:10:58 anand-Inspiron-13-5378 dhclient[3891]: XMT: Info-Request on enx0050b6de9a0e, interval 1060ms.
Feb  3 12:10:58 anand-Inspiron-13-5378 dhclient[3891]: RCV: Reply message on enx0050b6de9a0e from fe80::e9f5:90b3:7aa2:10f1.
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.3904]   nameserver 'fe80::e9f5:90b3:7aa2:10f1'
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.3906]   domain search 'mshome.net.'
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.3907] dhcp6 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.3931] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:10:58 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:10:58 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:10:58 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:10:58 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver fe80::e9f5:90b3:7aa2:10f1%enx0050b6de9a0e#53
Feb  3 12:10:58 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 12:10:58 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.5785] dhcp6 (enx0050b6de9a0e): client pid 3891 exited with status 0
Feb  3 12:10:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176058.5785] dhcp6 (enx0050b6de9a0e): state changed bound -> done
Feb  3 12:10:58 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 12:10:58 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 12:10:58 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 12:10:58 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 12:11:03 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176063.1951] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3941
Feb  3 12:11:03 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176063.1959] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction
Feb  3 12:11:03 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176063.1970] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:11:03 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176063.1993] dhcp6 (enx0050b6de9a0e): dhclient started with pid 3942
Feb  3 12:11:03 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176063.2012] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:11:03 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:11:03 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:11:03 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:11:03 anand-Inspiron-13-5378 dhclient[3942]: XMT: Solicit on enx0050b6de9a0e, interval 1060ms.
Feb  3 12:11:04 anand-Inspiron-13-5378 dhclient[3942]: XMT: Solicit on enx0050b6de9a0e, interval 2140ms.
Feb  3 12:11:06 anand-Inspiron-13-5378 dhclient[3942]: XMT: Solicit on enx0050b6de9a0e, interval 4400ms.
Feb  3 12:11:11 anand-Inspiron-13-5378 dhclient[3942]: XMT: Solicit on enx0050b6de9a0e, interval 8550ms.
Feb  3 12:11:19 anand-Inspiron-13-5378 dhclient[3942]: XMT: Solicit on enx0050b6de9a0e, interval 16420ms.
Feb  3 12:11:31 anand-Inspiron-13-5378 kernel: [ 2526.023554] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:11:31 anand-Inspiron-13-5378 kernel: [ 2526.023668] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:11:31 anand-Inspiron-13-5378 kernel: [ 2526.023683] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:11:31 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:11:36 anand-Inspiron-13-5378 dhclient[3942]: XMT: Solicit on enx0050b6de9a0e, interval 34120ms.
Feb  3 12:11:48 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549176108.6333] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:11:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176108.6334] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:11:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176108.6346] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 3942
Feb  3 12:11:48 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176108.6346] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:12:34 anand-Inspiron-13-5378 kernel: [ 2589.028517] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:12:34 anand-Inspiron-13-5378 kernel: [ 2589.028590] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:12:34 anand-Inspiron-13-5378 kernel: [ 2589.028601] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:12:34 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:12:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176158.4765] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:12:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176158.4814] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4029
Feb  3 12:12:38 anand-Inspiron-13-5378 dhclient[4029]: XMT: Info-Request on enx0050b6de9a0e, interval 1070ms.
Feb  3 12:12:38 anand-Inspiron-13-5378 dhclient[4029]: RCV: Reply message on enx0050b6de9a0e from fe80::e9f5:90b3:7aa2:10f1.
Feb  3 12:12:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176158.9411]   nameserver 'fe80::e9f5:90b3:7aa2:10f1'
Feb  3 12:12:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176158.9413]   domain search 'mshome.net.'
Feb  3 12:12:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176158.9414] dhcp6 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 12:12:38 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176158.9432] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:12:38 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:12:38 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:12:38 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:12:38 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver fe80::e9f5:90b3:7aa2:10f1%enx0050b6de9a0e#53
Feb  3 12:12:39 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 12:12:39 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 12:12:39 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176159.0632] dhcp6 (enx0050b6de9a0e): client pid 4029 exited with status 0
Feb  3 12:12:39 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176159.0632] dhcp6 (enx0050b6de9a0e): state changed bound -> done
Feb  3 12:12:39 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 12:12:39 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 12:12:39 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 12:12:39 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 12:12:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176165.9751] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4080
Feb  3 12:12:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176165.9761] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction
Feb  3 12:12:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176165.9782] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:12:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176165.9835] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4081
Feb  3 12:12:45 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176165.9902] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:12:45 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:12:45 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:12:45 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:12:46 anand-Inspiron-13-5378 dhclient[4081]: XMT: Solicit on enx0050b6de9a0e, interval 1010ms.
Feb  3 12:12:47 anand-Inspiron-13-5378 dhclient[4081]: XMT: Solicit on enx0050b6de9a0e, interval 1940ms.
Feb  3 12:12:49 anand-Inspiron-13-5378 dhclient[4081]: XMT: Solicit on enx0050b6de9a0e, interval 3750ms.
Feb  3 12:12:53 anand-Inspiron-13-5378 dhclient[4081]: XMT: Solicit on enx0050b6de9a0e, interval 7370ms.
Feb  3 12:13:00 anand-Inspiron-13-5378 dhclient[4081]: XMT: Solicit on enx0050b6de9a0e, interval 14740ms.
Feb  3 12:13:15 anand-Inspiron-13-5378 dhclient[4081]: XMT: Solicit on enx0050b6de9a0e, interval 28910ms.
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.4346] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4127
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.4356] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 4081
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.4358] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.4379] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.4453] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4128
Feb  3 12:13:15 anand-Inspiron-13-5378 dhclient[4128]: XMT: Info-Request on enx0050b6de9a0e, interval 980ms.
Feb  3 12:13:15 anand-Inspiron-13-5378 dhclient[4128]: RCV: Reply message on enx0050b6de9a0e from fe80::e9f5:90b3:7aa2:10f1.
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.5540]   nameserver 'fe80::e9f5:90b3:7aa2:10f1'
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.5541]   domain search 'mshome.net.'
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.5541] dhcp6 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.5552] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:13:15 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:13:15 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:13:15 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:13:15 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver fe80::e9f5:90b3:7aa2:10f1%enx0050b6de9a0e#53
Feb  3 12:13:15 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 12:13:15 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.6722] dhcp6 (enx0050b6de9a0e): client pid 4128 exited with status 0
Feb  3 12:13:15 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176195.6722] dhcp6 (enx0050b6de9a0e): state changed bound -> done
Feb  3 12:13:15 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 12:13:15 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 12:13:15 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 12:13:15 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 12:13:24 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176204.0844] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4180
Feb  3 12:13:24 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176204.0856] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction
Feb  3 12:13:24 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176204.0882] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:13:24 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176204.0931] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4181
Feb  3 12:13:24 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176204.0969] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:13:24 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:13:24 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:13:24 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:13:24 anand-Inspiron-13-5378 dhclient[4181]: XMT: Solicit on enx0050b6de9a0e, interval 1020ms.
Feb  3 12:13:25 anand-Inspiron-13-5378 dhclient[4181]: XMT: Solicit on enx0050b6de9a0e, interval 2030ms.
Feb  3 12:13:27 anand-Inspiron-13-5378 dhclient[4181]: XMT: Solicit on enx0050b6de9a0e, interval 3990ms.
Feb  3 12:13:31 anand-Inspiron-13-5378 dhclient[4181]: XMT: Solicit on enx0050b6de9a0e, interval 8180ms.
Feb  3 12:13:37 anand-Inspiron-13-5378 kernel: [ 2652.022438] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:13:37 anand-Inspiron-13-5378 kernel: [ 2652.022542] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:13:37 anand-Inspiron-13-5378 kernel: [ 2652.022565] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:13:37 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:13:39 anand-Inspiron-13-5378 dhclient[4181]: XMT: Solicit on enx0050b6de9a0e, interval 15910ms.
Feb  3 12:13:55 anand-Inspiron-13-5378 dhclient[4181]: XMT: Solicit on enx0050b6de9a0e, interval 32590ms.
Feb  3 12:14:09 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549176249.6278] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:14:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176249.6280] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:14:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176249.6296] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 4181
Feb  3 12:14:09 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176249.6297] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:14:40 anand-Inspiron-13-5378 kernel: [ 2715.024846] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:14:40 anand-Inspiron-13-5378 kernel: [ 2715.024963] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:14:40 anand-Inspiron-13-5378 kernel: [ 2715.024983] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:14:40 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:15:43 anand-Inspiron-13-5378 kernel: [ 2778.022312] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:15:43 anand-Inspiron-13-5378 kernel: [ 2778.022360] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:15:43 anand-Inspiron-13-5378 kernel: [ 2778.022367] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:15:43 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:16:04 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176364.5847] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:16:04 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176364.5862] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4233
Feb  3 12:16:05 anand-Inspiron-13-5378 dhclient[4233]: XMT: Info-Request on enx0050b6de9a0e, interval 1060ms.
Feb  3 12:16:05 anand-Inspiron-13-5378 dhclient[4233]: RCV: Reply message on enx0050b6de9a0e from fe80::e9f5:90b3:7aa2:10f1.
Feb  3 12:16:05 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176365.0702]   nameserver 'fe80::e9f5:90b3:7aa2:10f1'
Feb  3 12:16:05 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176365.0702]   domain search 'mshome.net.'
Feb  3 12:16:05 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176365.0703] dhcp6 (enx0050b6de9a0e): state changed unknown -> bound
Feb  3 12:16:05 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176365.0707] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:16:05 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:16:05 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:16:05 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:16:05 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver fe80::e9f5:90b3:7aa2:10f1%enx0050b6de9a0e#53
Feb  3 12:16:05 anand-Inspiron-13-5378 dbus[728]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb  3 12:16:05 anand-Inspiron-13-5378 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb  3 12:16:05 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176365.1150] dhcp6 (enx0050b6de9a0e): client pid 4233 exited with status 0
Feb  3 12:16:05 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176365.1150] dhcp6 (enx0050b6de9a0e): state changed bound -> done
Feb  3 12:16:05 anand-Inspiron-13-5378 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  3 12:16:05 anand-Inspiron-13-5378 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb  3 12:16:05 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: new request (1 scripts)
Feb  3 12:16:05 anand-Inspiron-13-5378 nm-dispatcher: req:1 'dhcp6-change' [enx0050b6de9a0e]: start running ordered scripts...
Feb  3 12:16:13 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176373.1988] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4283
Feb  3 12:16:13 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176373.1999] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction
Feb  3 12:16:13 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176373.2025] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:16:13 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176373.2068] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4284
Feb  3 12:16:13 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176373.2111] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb  3 12:16:13 anand-Inspiron-13-5378 dnsmasq[3266]: setting upstream servers from DBus
Feb  3 12:16:13 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.193#53(via enx0050b6de9a0e)
Feb  3 12:16:13 anand-Inspiron-13-5378 dnsmasq[3266]: using nameserver 10.24.0.194#53(via enx0050b6de9a0e)
Feb  3 12:16:13 anand-Inspiron-13-5378 dhclient[4284]: XMT: Solicit on enx0050b6de9a0e, interval 1090ms.
Feb  3 12:16:14 anand-Inspiron-13-5378 dhclient[4284]: XMT: Solicit on enx0050b6de9a0e, interval 2160ms.
Feb  3 12:16:17 anand-Inspiron-13-5378 dhclient[4284]: XMT: Solicit on enx0050b6de9a0e, interval 4300ms.
Feb  3 12:16:21 anand-Inspiron-13-5378 dhclient[4284]: XMT: Solicit on enx0050b6de9a0e, interval 8300ms.
Feb  3 12:16:29 anand-Inspiron-13-5378 dhclient[4284]: XMT: Solicit on enx0050b6de9a0e, interval 16280ms.
Feb  3 12:16:46 anand-Inspiron-13-5378 dhclient[4284]: XMT: Solicit on enx0050b6de9a0e, interval 32540ms.
Feb  3 12:16:46 anand-Inspiron-13-5378 kernel: [ 2841.021699] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:16:46 anand-Inspiron-13-5378 kernel: [ 2841.021817] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:16:46 anand-Inspiron-13-5378 kernel: [ 2841.021845] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:16:46 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:16:58 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549176418.6275] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:16:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176418.6276] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:16:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176418.6295] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 4284
Feb  3 12:16:58 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176418.6295] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:17:01 anand-Inspiron-13-5378 CRON[4340]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  3 12:17:29 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176449.5775] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:17:29 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176449.5788] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4368
Feb  3 12:17:29 anand-Inspiron-13-5378 dhclient[4368]: XMT: Info-Request on enx0050b6de9a0e, interval 970ms.
Feb  3 12:17:30 anand-Inspiron-13-5378 dhclient[4368]: XMT: Info-Request on enx0050b6de9a0e, interval 2000ms.
Feb  3 12:17:31 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176451.9722] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4378
Feb  3 12:17:31 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176451.9733] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 4368
Feb  3 12:17:31 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176451.9735] dhcp6 (enx0050b6de9a0e): state changed unknown -> done
Feb  3 12:17:31 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176451.9753] dhcp6 (enx0050b6de9a0e): activation: beginning transaction (timeout in 45 seconds)
Feb  3 12:17:31 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176451.9763] dhcp6 (enx0050b6de9a0e): dhclient started with pid 4379
Feb  3 12:17:32 anand-Inspiron-13-5378 dhclient[4379]: XMT: Solicit on enx0050b6de9a0e, interval 1020ms.
Feb  3 12:17:33 anand-Inspiron-13-5378 dhclient[4379]: XMT: Solicit on enx0050b6de9a0e, interval 1990ms.
Feb  3 12:17:35 anand-Inspiron-13-5378 dhclient[4379]: XMT: Solicit on enx0050b6de9a0e, interval 3850ms.
Feb  3 12:17:39 anand-Inspiron-13-5378 dhclient[4379]: XMT: Solicit on enx0050b6de9a0e, interval 7460ms.
Feb  3 12:17:46 anand-Inspiron-13-5378 dhclient[4379]: XMT: Solicit on enx0050b6de9a0e, interval 14260ms.
Feb  3 12:17:49 anand-Inspiron-13-5378 kernel: [ 2904.030797] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:17:49 anand-Inspiron-13-5378 kernel: [ 2904.030933] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:17:49 anand-Inspiron-13-5378 kernel: [ 2904.030961] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:17:49 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
Feb  3 12:18:00 anand-Inspiron-13-5378 dhclient[4379]: XMT: Solicit on enx0050b6de9a0e, interval 28120ms.
Feb  3 12:18:17 anand-Inspiron-13-5378 NetworkManager[3022]: <warn>  [1549176497.6309] dhcp6 (enx0050b6de9a0e): request timed out
Feb  3 12:18:17 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176497.6310] dhcp6 (enx0050b6de9a0e): state changed unknown -> timeout
Feb  3 12:18:17 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176497.6318] dhcp6 (enx0050b6de9a0e): canceled DHCP transaction, DHCP client pid 4379
Feb  3 12:18:17 anand-Inspiron-13-5378 NetworkManager[3022]: <info>  [1549176497.6318] dhcp6 (enx0050b6de9a0e): state changed timeout -> done
Feb  3 12:18:52 anand-Inspiron-13-5378 kernel: [ 2967.026438] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:18:52 anand-Inspiron-13-5378 kernel: [ 2967.026478] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:18:52 anand-Inspiron-13-5378 kernel: [ 2967.026482] iwlwifi 0000:01:00.0: Scan failed! ret -5
Feb  3 12:18:52 anand-Inspiron-13-5378 wpa_supplicant[933]: wlp1s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
^[[1;2AFeb  3 12:19:55 anand-Inspiron-13-5378 kernel: [ 3030.022133] iwlwifi 0000:01:00.0: Failed to wake NIC for hcmd
Feb  3 12:19:55 anand-Inspiron-13-5378 kernel: [ 3030.022150] iwlwifi 0000:01:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
Feb  3 12:19:55 anand-Inspiron-13-5378 kernel: [ 3030.022154] iwlwifi 0000:01:00.0: Scan failed! ret -5
```

---

### Post by jeremy31 on 2019-02-03
Post split from another thread to its own topic and code tags added

---

