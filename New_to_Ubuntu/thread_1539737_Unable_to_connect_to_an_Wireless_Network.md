---
title: "Unable to connect to an Wireless Network"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by shoaibi on 2010-07-26
Details:

specs:
```

Linux home-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

```

Scanning Wireless networks:
```

# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 58:B0:35:70:69:0B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Pluto"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001f9a4ed5
                    Extra: Last beacon: 6400ms ago
                    IE: Unknown: 000B49736861712773204D6163
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706583220010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000

```


Now connecting using Network manager interface:

syslog:
```

Jul 26 23:58:42 home-laptop NetworkManager: <info>  WiFi now enabled by radio killswitch
Jul 26 23:58:42 home-laptop kernel: [  987.080312] b43-phy0: Radio hardware status changed to ENABLED
Jul 26 23:58:42 home-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jul 26 23:58:43 home-laptop kernel: [  987.390288] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Jul 26 23:58:57 home-laptop kernel: [ 1001.211934] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:58:57 home-laptop kernel: [ 1001.215519] wlan0: direct probe responded
Jul 26 23:58:57 home-laptop kernel: [ 1001.215530] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:58:57 home-laptop kernel: [ 1001.217711] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:58:57 home-laptop kernel: [ 1001.221117] wlan0: direct probe responded
Jul 26 23:58:57 home-laptop kernel: [ 1001.221124] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:58:57 home-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jul 26 23:58:57 home-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jul 26 23:59:14 home-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Pluto'
Jul 26 23:59:14 home-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 23:59:14 home-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Pluto' has security, but secrets are required.
Jul 26 23:59:14 home-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jul 26 23:59:14 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 23:59:22 home-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 23:59:22 home-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Pluto' has security, and secrets exist.  No new secrets needed.
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: added 'ssid' value 'Pluto'
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jul 26 23:59:22 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 26 23:59:22 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 23:59:22 home-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 26 23:59:22 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jul 26 23:59:23 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 26 23:59:23 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 26 23:59:23 home-laptop kernel: [ 1027.701875] wlan0: deauthenticating from 58:b0:35:70:69:0b by local choice (reason=3)
Jul 26 23:59:23 home-laptop kernel: [ 1027.720338] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:23 home-laptop kernel: [ 1027.724811] wlan0: direct probe responded
Jul 26 23:59:23 home-laptop kernel: [ 1027.724817] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:33 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 26 23:59:33 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 26 23:59:33 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 26 23:59:34 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 26 23:59:34 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 26 23:59:34 home-laptop kernel: [ 1039.150355] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:34 home-laptop kernel: [ 1039.154011] wlan0: direct probe responded
Jul 26 23:59:34 home-laptop kernel: [ 1039.154017] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:44 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 26 23:59:44 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 26 23:59:44 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 26 23:59:46 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 26 23:59:46 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 26 23:59:46 home-laptop kernel: [ 1050.600345] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:46 home-laptop kernel: [ 1050.603754] wlan0: direct probe responded
Jul 26 23:59:46 home-laptop kernel: [ 1050.603759] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:56 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 26 23:59:56 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 26 23:59:56 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 26 23:59:57 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 26 23:59:57 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 26 23:59:57 home-laptop kernel: [ 1062.060343] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 26 23:59:57 home-laptop kernel: [ 1062.063822] wlan0: direct probe responded
Jul 26 23:59:57 home-laptop kernel: [ 1062.063828] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:04 home-laptop NetworkManager: <info>  wlan0: link timed out.
Jul 27 00:00:07 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:00:07 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:00:07 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:00:09 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:00:09 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:00:09 home-laptop kernel: [ 1073.482876] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:09 home-laptop kernel: [ 1073.486749] wlan0: direct probe responded
Jul 27 00:00:09 home-laptop kernel: [ 1073.486755] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:19 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:00:19 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:00:19 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:00:20 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:00:20 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:00:20 home-laptop kernel: [ 1084.920372] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:20 home-laptop kernel: [ 1084.923780] wlan0: direct probe responded
Jul 27 00:00:20 home-laptop kernel: [ 1084.923785] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:22 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jul 27 00:00:22 home-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jul 27 00:00:22 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jul 27 00:00:22 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 27 00:00:25 home-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 27 00:00:25 home-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Pluto' has security, and secrets exist.  No new secrets needed.
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: added 'ssid' value 'Pluto'
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jul 27 00:00:25 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 27 00:00:25 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 27 00:00:25 home-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 27 00:00:25 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:00:26 home-laptop kernel: [ 1090.619881] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
Jul 27 00:00:26 home-laptop kernel: [ 1090.619889] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Jul 27 00:00:26 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:00:26 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:00:26 home-laptop kernel: [ 1090.940410] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:26 home-laptop kernel: [ 1090.944019] wlan0: direct probe responded
Jul 27 00:00:26 home-laptop kernel: [ 1090.944028] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:36 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:00:36 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:00:36 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:00:38 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:00:38 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:00:38 home-laptop kernel: [ 1102.380375] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:38 home-laptop kernel: [ 1102.383800] wlan0: direct probe responded
Jul 27 00:00:38 home-laptop kernel: [ 1102.383806] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:48 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:00:48 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:00:48 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:00:49 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:00:49 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:00:49 home-laptop kernel: [ 1113.810379] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:49 home-laptop kernel: [ 1113.813800] wlan0: direct probe responded
Jul 27 00:00:49 home-laptop kernel: [ 1113.813806] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:00:59 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:00:59 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:00:59 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:01:01 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:01:01 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:01:01 home-laptop kernel: [ 1125.260316] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:01 home-laptop kernel: [ 1125.263666] wlan0: direct probe responded
Jul 27 00:01:01 home-laptop kernel: [ 1125.263672] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:07 home-laptop NetworkManager: <info>  wlan0: link timed out.
Jul 27 00:01:11 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:01:11 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:01:11 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:01:12 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:01:12 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:01:12 home-laptop kernel: [ 1136.690352] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:12 home-laptop kernel: [ 1136.693706] wlan0: direct probe responded
Jul 27 00:01:12 home-laptop kernel: [ 1136.693712] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:22 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:01:22 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:01:22 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:01:23 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:01:23 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:01:23 home-laptop kernel: [ 1148.131303] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:23 home-laptop kernel: [ 1148.136377] wlan0: direct probe responded
Jul 27 00:01:23 home-laptop kernel: [ 1148.136387] wlan0: authenticate with AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:26 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jul 27 00:01:26 home-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jul 27 00:01:26 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jul 27 00:01:26 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 27 00:01:31 home-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 27 00:01:31 home-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Pluto' has security, and secrets exist.  No new secrets needed.
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: added 'ssid' value 'Pluto'
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jul 27 00:01:31 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 27 00:01:31 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 27 00:01:31 home-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 27 00:01:31 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:01:32 home-laptop wpa_supplicant[1385]: Trying to associate with 58:b0:35:70:69:0b (SSID='Pluto' freq=2462 MHz)
Jul 27 00:01:32 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 27 00:01:32 home-laptop kernel: [ 1156.700375] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 1)
Jul 27 00:01:32 home-laptop kernel: [ 1156.900081] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 2)
Jul 27 00:01:32 home-laptop kernel: [ 1157.100093] wlan0: direct probe to AP 58:b0:35:70:69:0b (try 3)
Jul 27 00:01:33 home-laptop kernel: [ 1157.300103] wlan0: direct probe to AP 58:b0:35:70:69:0b timed out
Jul 27 00:01:42 home-laptop wpa_supplicant[1385]: Authentication with 58:b0:35:70:69:0b timed out.
Jul 27 00:01:42 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 27 00:01:42 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:02:13 home-laptop NetworkManager: <info>  wlan0: link timed out.
Jul 27 00:02:31 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jul 27 00:02:31 home-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jul 27 00:02:31 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jul 27 00:02:31 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 27 00:02:33 home-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 27 00:02:33 home-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Pluto' has security, and secrets exist.  No new secrets needed.
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: added 'ssid' value 'Pluto'
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jul 27 00:02:33 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 27 00:02:33 home-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 27 00:02:33 home-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 27 00:02:33 home-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 27 00:03:34 home-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jul 27 00:03:34 home-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Jul 27 00:03:34 home-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Pluto)
Jul 27 00:03:34 home-laptop NetworkManager: <info>  Marking connection 'Auto Pluto' invalid.
Jul 27 00:03:34 home-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jul 27 00:03:34 home-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jul 27 00:03:34 home-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

```


dmesg:
```

[   34.680272] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   34.878575] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   35.036233] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   35.190265] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

Result:
Wireless Connection never gets established, after every couple of minutes it asks me again for the key and finally gets disconnected e.g. stops trying to make a connection. I know that its a valid network, and valid key because i can connect to it using other boxes in building and even mobiles.

Any ideas?

---

### Post by anewguy on 2010-07-27
What about your access point?  Is it a wireless router?  If so, since it appears you are using WPA, do you also have MAC filtering enabled on the router?  If so, have you added the MAC of this machine to the allowed list in the router?

I ask these because I get the same issue on my netbook because the MAC isn't registered in the router.  Tries to log on for quite a while, then stops and asks for password again. In my case, for some reason the router isn't letting me in to the setup page, even when direct connected (and I set up the dang thing!).  I really don't want to reset the router and put everything in again from scratch.  I have to "spoof" the address of a backup computer (doesn't run backups, simply there to use as a backup if one of the main computers fail), since that address is in the MAC table in the router.

Dave ;)

---

### Post by shoaibi on 2010-07-27
The AP is actually a macbook which has shared its connection to airport/wireless. And there is no MAC address issue as other computer can connect without any issues.

---

### Post by anewguy on 2010-07-28
I asked about MAC filtering because you mentioned that you can connect with other boxes.  If your wireless is working in that you can see wireless networks and try to connect to them, then all things being equal it must be something with this one computer.  The one thing this one computer would have different is the MAC address.  Have you checked the router config page to be sure MAC filtering is off, or are you assuming this because other computers can connect?  Do you own the router?  Can you get in to the config screen for it?

---

### Post by shoaibi on 2010-07-28
the route is actually just a macbook pro that shared its Ethernet to airport/wireless.
And i have checked, there is no mac filtering on router/macbook pro.

---

### Post by shoaibi on 2010-07-29
I got a new NETGEAR WGR614 v9, reset it to factory defaults and try to connect it from my laptop:

```


Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) starting connection 'Auto NETGEAR'
Jul 29 16:58:49 blade NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 29 16:58:49 blade NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto NETGEAR' requires no security.  No secrets needed.
Jul 29 16:58:49 blade NetworkManager: <info>  Config: added 'ssid' value 'NETGEAR'
Jul 29 16:58:49 blade NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 29 16:58:49 blade NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul 29 16:58:49 blade NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 29 16:58:49 blade NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 29 16:58:49 blade NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jul 29 16:58:49 blade NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 29 16:59:04 blade NetworkManager: <info>  wlan0: link timed out.
Jul 29 16:59:49 blade NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.
Jul 29 16:59:49 blade NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)
Jul 29 16:59:49 blade NetworkManager: <info>  Activation (wlan0) failed for access point (NETGEAR)
Jul 29 16:59:49 blade NetworkManager: <info>  Marking connection 'Auto NETGEAR' invalid.
Jul 29 16:59:49 blade NetworkManager: <info>  Activation (wlan0) failed.
Jul 29 16:59:49 blade NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jul 29 16:59:49 blade NetworkManager: <info>  (wlan0): deactivating device (reason: 0).


```

again, other computers can connect to this without any issues as well.

---

