---
title: "avm fritz wlan n v2 (8501), 14.10"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by rschupi on 2015-01-27
My new Fritz wlan stick n v2 does not run under ubuntu 14.10, which it should according to the (german) cards wiki
([http://wiki.ubuntuusers.de/WLAN/Karten](http://wiki.ubuntuusers.de/WLAN/Karten)).

Edit January 31
Problem is gone, stick works fine, with nothing changed.
Well, I won't complain.

---

### Post by rschupi on 2015-01-31
Today, January 31, the problem is gone, with nothing changed. No idea why. Anyway, that's fine with me.

---

### Post by rschupi on 2015-02-17
> **rschupi said:**
> Today, January 31, the problem is gone, with nothing changed. No idea why. Anyway, that's fine with me.

Well, actually, the problem was back the next day. After hoping for some time it would go away again, I'll give the forum another try.

What happens: The stick is recognized, gives me a menu of available networks, when I click on my network and give it the wpa-password, the yellow LED blinks for a little while, then I'm asked for the password again and again and again...
The critical point seems to be the 4-way-handshake.
A different stick (netgear, fairly old) associates with no problem (it has another problem, after 5 or so minutes it gets warm and hangs up, that's why I bought the nwe one) 

Here is the syslog:
Feb 17 17:53:15 ogar2 kernel: [ 1084.512084] usb 1-2: new high-speed USB device number 6 using ehci-pci
Feb 17 17:53:15 ogar2 kernel: [ 1084.647979] usb 1-2: New USB device found, idVendor=057c, idProduct=62ff
Feb 17 17:53:15 ogar2 kernel: [ 1084.647989] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 17 17:53:15 ogar2 kernel: [ 1084.647996] usb 1-2: Product: FRITZ!WLAN USB Stick N v2
Feb 17 17:53:15 ogar2 kernel: [ 1084.648037] usb 1-2: Manufacturer: AVM Berlin
Feb 17 17:53:15 ogar2 kernel: [ 1084.648054] usb 1-2: SerialNumber: 246511430E72
Feb 17 17:53:15 ogar2 mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Feb 17 17:53:15 ogar2 mtp-probe: bus: 1, device: 6 was not an MTP device
Feb 17 17:53:16 ogar2 kernel: [ 1084.942479] usb-storage 1-2:1.0: USB Mass Storage device detected
Feb 17 17:53:16 ogar2 kernel: [ 1084.954513] scsi4 : usb-storage 1-2:1.0
Feb 17 17:53:16 ogar2 kernel: [ 1084.955119] usbcore: registered new interface driver usb-storage
Feb 17 17:53:17 ogar2 kernel: [ 1085.953079] scsi 4:0:0:0: CD-ROM            FRITZ!   WLAN selfinstall 1.00 PQ: 0 ANSI: 0 CCS
Feb 17 17:53:17 ogar2 kernel: [ 1085.962126] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Feb 17 17:53:17 ogar2 kernel: [ 1085.962921] sr 4:0:0:0: Attached scsi CD-ROM sr1
Feb 17 17:53:17 ogar2 kernel: [ 1085.963691] sr 4:0:0:0: Attached scsi generic sg2 type 5
Feb 17 17:53:17 ogar2 usb_modeswitch: switch device 057c:62ff on 001/006
Feb 17 17:53:17 ogar2 kernel: [ 1086.313073] usb 1-2: USB disconnect, device number 6
Feb 17 17:53:18 ogar2 kernel: [ 1087.500077] usb 1-2: new high-speed USB device number 7 using ehci-pci
Feb 17 17:53:18 ogar2 kernel: [ 1087.636449] usb 1-2: New USB device found, idVendor=057c, idProduct=8501
Feb 17 17:53:18 ogar2 kernel: [ 1087.636459] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 17 17:53:18 ogar2 kernel: [ 1087.636466] usb 1-2: Product: FRITZ!WLAN USB Stick N v2
Feb 17 17:53:18 ogar2 kernel: [ 1087.636472] usb 1-2: Manufacturer: AVM Berlin
Feb 17 17:53:18 ogar2 kernel: [ 1087.636478] usb 1-2: SerialNumber: 246511430E72
Feb 17 17:53:18 ogar2 kernel: [ 1087.752080] usb 1-2: reset high-speed USB device number 7 using ehci-pci
Feb 17 17:53:19 ogar2 kernel: [ 1087.886454] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 5592, rev 0222 detected
Feb 17 17:53:19 ogar2 kernel: [ 1087.914582] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 000f detected
Feb 17 17:53:19 ogar2 kernel: [ 1087.923379] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
Feb 17 17:53:19 ogar2 mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Feb 17 17:53:19 ogar2 mtp-probe: bus: 1, device: 7 was not an MTP device
Feb 17 17:53:19 ogar2 usb_modeswitch[3848]: usb_modeswitch: switched to 057c:8501 on 1/7
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/ieee80211/phy2/rfkill2) (driver rt2800usb)
Feb 17 17:53:20 ogar2 kernel: [ 1089.157190] systemd-udevd[3891]: renamed network interface wlan0 to wlan1
Feb 17 17:53:20 ogar2 NetworkManager[865]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/net/wlan1, iface: wlan1)
Feb 17 17:53:20 ogar2 NetworkManager[865]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): using nl80211 for WiFi device control
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): driver supports Access Point (AP) mode
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 6)
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/3
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): bringing up device.
Feb 17 17:53:20 ogar2 kernel: [ 1089.180207] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
Feb 17 17:53:20 ogar2 kernel: [ 1089.222679] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
Feb 17 17:53:20 ogar2 kernel: [ 1089.223513] ieee80211 phy2: rt2800usb_write_firmware: Info - Firmware loading not required - NIC in AutoRun mode
Feb 17 17:53:20 ogar2 kernel: [ 1089.531941] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): preparing device.
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): deactivating device (reason 'managed') [2]
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1) supports 4 scan SSIDs
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: starting -> ready
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 17 17:53:20 ogar2 NetworkManager[865]: <warn> Trying to remove a non-existant call id.
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: ready -> disconnected
Feb 17 17:52:21 ogar2 wpa_supplicant[915]: wlan0: CTRL-EVENT-SCAN-STARTED 
Feb 17 17:53:20 ogar2 wpa_supplicant[915]: wlan1: CTRL-EVENT-SCAN-STARTED 
Feb 17 17:53:20 ogar2 NetworkManager[865]: <info> (wlan1) supports 4 scan SSIDs
Feb 17 17:53:20 ogar2 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 17 17:53:22 ogar2 ModemManager[776]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2': not supported by any plugin
Feb 17 17:53:24 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: disconnected -> inactive
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) starting connection 'Klimbim'
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1/wireless): access point 'Klimbim' has security, but secrets are required.
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 17 17:54:34 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Feb 17 17:54:49 ogar2 NetworkManager[865]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1/wireless): connection 'Klimbim' has security, and secrets exist.  No new secrets needed.
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Config: added 'ssid' value 'Klimbim'
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Config: added 'scan_ssid' value '1'
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Config: added 'psk' value '<omitted>'
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> Config: set interface ap_scan to 1
Feb 17 17:54:49 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: inactive -> scanning
Feb 17 17:54:49 ogar2 wpa_supplicant[915]: message repeated 4 times: [ wlan1: CTRL-EVENT-SCAN-STARTED ]
Feb 17 17:54:53 ogar2 wpa_supplicant[915]: wlan1: SME: Trying to authenticate with 34:31:c4:19:0f:5e (SSID='Klimbim' freq=2462 MHz)
Feb 17 17:54:53 ogar2 kernel: [ 1182.518755] wlan1: authenticate with 34:31:c4:19:0f:5e
Feb 17 17:54:53 ogar2 kernel: [ 1182.597201] wlan1: send auth to 34:31:c4:19:0f:5e (try 1/3)
Feb 17 17:54:53 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: scanning -> authenticating
Feb 17 17:54:53 ogar2 wpa_supplicant[915]: wlan1: Trying to associate with 34:31:c4:19:0f:5e (SSID='Klimbim' freq=2462 MHz)
Feb 17 17:54:53 ogar2 kernel: [ 1182.602949] wlan1: authenticated
Feb 17 17:54:53 ogar2 kernel: [ 1182.604430] wlan1: associate with 34:31:c4:19:0f:5e (try 1/3)
Feb 17 17:54:53 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: authenticating -> associating
Feb 17 17:54:53 ogar2 kernel: [ 1182.615509] wlan1: RX AssocResp from 34:31:c4:19:0f:5e (capab=0x431 status=0 aid=3)
Feb 17 17:54:53 ogar2 kernel: [ 1182.626082] wlan1: associated
Feb 17 17:54:53 ogar2 kernel: [ 1182.626174] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Feb 17 17:54:53 ogar2 kernel: [ 1182.626406] cfg80211: Calling CRDA for country: DE
Feb 17 17:54:53 ogar2 wpa_supplicant[915]: wlan1: Associated with 34:31:c4:19:0f:5e
Feb 17 17:54:53 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: associating -> 4-way handshake
Feb 17 17:54:53 ogar2 kernel: [ 1182.701217] cfg80211: Regulatory domain changed to country: DE
Feb 17 17:54:53 ogar2 kernel: [ 1182.701226] cfg80211:  DFS Master region: unset
Feb 17 17:54:53 ogar2 kernel: [ 1182.701231] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 17 17:54:53 ogar2 kernel: [ 1182.701239] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 17:54:53 ogar2 kernel: [ 1182.701245] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 17:54:53 ogar2 kernel: [ 1182.701251] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Feb 17 17:54:53 ogar2 kernel: [ 1182.701257] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm), (0 s)
Feb 17 17:54:53 ogar2 kernel: [ 1182.701263] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Feb 17 17:54:55 ogar2 avahi-daemon[795]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::2665:11ff:fe43:e72.
Feb 17 17:54:55 ogar2 avahi-daemon[795]: New relevant interface wlan1.IPv6 for mDNS.
Feb 17 17:54:55 ogar2 avahi-daemon[795]: Registering new address record for fe80::2665:11ff:fe43:e72 on wlan1.*.
Feb 17 17:54:57 ogar2 kernel: [ 1186.622484] wlan1: disassociated from 34:31:c4:19:0f:5e (Reason: 2)
Feb 17 17:54:57 ogar2 wpa_supplicant[915]: wlan1: CTRL-EVENT-DISCONNECTED bssid=34:31:c4:19:0f:5e reason=2
Feb 17 17:54:57 ogar2 wpa_supplicant[915]: wlan1: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Feb 17 17:54:57 ogar2 wpa_supplicant[915]: wlan1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Klimbim" auth_failures=1 duration=10
Feb 17 17:54:57 ogar2 kernel: [ 1186.688112] cfg80211: Calling CRDA to update world regulatory domain
Feb 17 17:54:57 ogar2 NetworkManager[865]: <warn> Connection disconnected (reason 2)
Feb 17 17:54:57 ogar2 NetworkManager[865]: <info> (wlan1): supplicant interface state: 4-way handshake -> disconnected
Feb 17 17:54:57 ogar2 NetworkManager[865]: <info> Activation (wlan1/wireless): disconnected during association, asking for new key.

---

