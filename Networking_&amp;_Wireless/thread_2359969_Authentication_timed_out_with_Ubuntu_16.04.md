---
title: "Authentication timed out with Ubuntu 16.04"
date: 2017-04-30
forum: Networking &amp; Wireless
---

### Post by falcon787 on 2017-04-30
I am getting alot of timeout when trying to connect to Wifi netowrks at work and when gets connected, it drops after a while, 

I am having those issues with both cards I have: 
- built-in adapter (RTL8723BE PCIe Wireless Network Adapter) 
- external USB adapter (Netgear A6210)  

Below is the system log snapshot, 

```


Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4181] device (wlan0): supplicant interface state: disconnected -> disabled
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4274] device (wlan0): supplicant interface state: disabled -> disconnected
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4280] device (wlan0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4282] device (wlan0): Activation: (wifi) connection 'STCS' has security, and secrets exist.  No new secrets needed.
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4282] Config: added 'ssid' value 'STCS'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4283] Config: added 'scan_ssid' value '1'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4283] Config: added 'key_mgmt' value 'WPA-EAP'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4283] Config: added 'auth_alg' value 'OPEN'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4283] Config: added 'password' value '<omitted>'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4283] Config: added 'eap' value 'PWD'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4283] Config: added 'fragment_size' value '1266'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4284] Config: added 'identity' value 'stcs\akhaled.c'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4284] Config: added 'bgscan' value 'simple:30:-65:300'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4284] Config: added 'proactive_key_caching' value '1'
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4309] sup-iface[0x25d1a00,wlan0]: config: set interface ap_scan to 1
Apr 30 16:31:21 amr-HP-Notebook NetworkManager[863]: <info>  [1493559081.4429] device (wlan0): supplicant interface state: disconnected -> scanning
Apr 30 16:31:21 amr-HP-Notebook kernel: [19880.245339] TX0 power compensation = 0x38
Apr 30 16:31:21 amr-HP-Notebook kernel: [19880.245468] TX1 power compensation = 0x38
Apr 30 16:31:28 amr-HP-Notebook wpa_supplicant[1450]: wlan0: Trying to associate with 0c:d9:96:4d:8e:08 (SSID='STCS' freq=2412 MHz)
Apr 30 16:31:28 amr-HP-Notebook kernel: [19886.985067] 80211> Connect bssid 0c:d9:96:4d:8e:08
Apr 30 16:31:28 amr-HP-Notebook NetworkManager[863]: <info>  [1493559088.2376] device (wlan0): supplicant interface state: scanning -> associating
[B]Apr 30 16:31:38 amr-HP-Notebook wpa_supplicant[1450]: wlan0: Authentication with 0c:d9:96:4d:8e:08 timed out.
[/B]Apr 30 16:31:38 amr-HP-Notebook wpa_supplicant[1450]: wlan0: CTRL-EVENT-DISCONNECTED bssid=0c:d9:96:4d:8e:08 reason=3 locally_generated=1
Apr 30 16:31:38 amr-HP-Notebook wpa_supplicant[1450]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="STCS" auth_failures=1 duration=10 reason=CONN_FAILED
Apr 30 16:31:38 amr-HP-Notebook NetworkManager[863]: <warn>  [1493559098.2363] sup-iface[0x25d1a00,wlan0]: connection disconnected (reason -3)
Apr 30 16:31:38 amr-HP-Notebook NetworkManager[863]: <info>  [1493559098.2411] device (wlan0): supplicant interface state: associating -> disconnected
Apr 30 16:31:38 amr-HP-Notebook NetworkManager[863]: <info>  [1493559098.3418] device (wlan0): supplicant interface state: disconnected -> scanning
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <warn>  [1493559106.8718] device (wlan0): Activation: (wifi) association took too long
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <info>  [1493559106.8719] device (wlan0): state change: config -> failed (reason 'no-secrets') [50 120 7]
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <info>  [1493559106.8723] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <warn>  [1493559106.8734] device (wlan0): Activation: failed for connection 'STCS'
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <info>  [1493559106.8770] device (wlan0): state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.634091] CFG80211DRV_IoctlHandle: CMD_RTPRIV_IOCTL_80211_NETDEV_EVENT
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656036] andes_usb_erasefw
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656104] ==>rlt_wlan_chip_onoff(): OnOff:0, Reset= 0, pAd->WlanFunCtrl:0x20b, Reg-WlanFunCtrl=0x20b
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656389] receive cmd msg fail(-2)
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656397] tx_kickout_fail_count = 0
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656397] tx_timeout_fail_count = 0
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656398] rx_receive_fail_count = 0
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656398] alloc_cmd_msg = 1002
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.656399] free_cmd_msg = 1002
Apr 30 16:31:46 amr-HP-Notebook gnome-session[2200]: (deja-dup-monitor:3471): GLib-CRITICAL **: Source ID 1030 was not found when attempting to remove it
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708469] RTMP_TimerListRelease: release timer obj ffffc900044d34b0!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708474] RTMP_TimerListRelease: release timer obj ffffc900044d3528!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708476] RTMP_TimerListRelease: release timer obj ffffc900044d35a0!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708478] RTMP_TimerListRelease: release timer obj ffffc900044d3438!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708480] RTMP_TimerListRelease: release timer obj ffffc900044d32d0!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708481] RTMP_TimerListRelease: release timer obj ffffc900044d3348!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708483] RTMP_TimerListRelease: release timer obj ffffc90004464fa0!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708485] RTMP_TimerListRelease: release timer obj ffffc90004453d78!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708486] RTMP_TimerListRelease: release timer obj ffffc90004453df8!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708488] RTMP_TimerListRelease: release timer obj ffffc90004465128!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708489] RTMP_TimerListRelease: release timer obj ffffc90004464eb0!
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.708491] RTMP_TimerListRelease: release timer obj ffffc900044650b0!
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <error> [1493559106.9560] platform-linux: do-change-link[4]: failure changing link: failure 99 (Cannot assign requested address)
Apr 30 16:31:46 amr-HP-Notebook NetworkManager[863]: <warn>  [1493559106.9561] device (wlan0): failed to reset MAC address to 00:00:00:00:00:00
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.721317] ==>rlt_wlan_chip_onoff(): OnOff:1, Reset= 0, pAd->WlanFunCtrl:0x208, Reg-WlanFunCtrl=0x209
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.722254] -->RTUSBVendorReset
Apr 30 16:31:46 amr-HP-Notebook kernel: [19905.742160] <--RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.743107] ...........andes_usb_chk_crc
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.832013] andes_usb_reset_wmt
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.852343] -->RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.872268] <--RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.872538] fw version:0.0.00 build:1
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.872540] build time:201406241830____
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.872543] fw for E3 IC
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.872544] ilm length = 59312(bytes)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.872545] dlm length = 32068(bytes)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.873086] loading fw........
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.929743] cfg_mode=5
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.929897] Key1Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.929913] Key2Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.929923] Key3Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.929931] Key4Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.930149] USBAggregation = 1
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.930152] 1. Phy Mode = 31
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.930153] NVM is Efuse and its size =1d[1e0-1fc] 
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945479] get_chl_grp:illegal channel (167)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945481] get_chl_grp:illegal channel (167)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945482] get_chl_grp:illegal channel (169)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945483] get_chl_grp:illegal channel (169)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945484] get_chl_grp:illegal channel (171)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945484] get_chl_grp:illegal channel (171)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945485] get_chl_grp:illegal channel (173)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.945486] get_chl_grp:illegal channel (173)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.946752] Country Region from e2p = ffff
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.953242] mt76x2_get_external_lna_gain::LNA type=0x0, BLNAGain=0xffffff8d, ALNAGain0=0xffffff89, ALNAGain1=0xffffff88, ALNAGain2=0xffffff87
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.953246] 2. Phy Mode = 31
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.953247] 3. Phy Mode = 31
Apr 30 16:31:47 amr-HP-Notebook kernel: [19905.953402] andes_usb_fw_init
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025105] AntCfgInit: primary/secondary ant 0/1
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025110] andes_load_cr:cr_type(2)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025857] ChipStructAssign(): MT76x2 hook !
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025983] ---> InitFrequencyCalibration
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025984] InitFrequencyCalibrationMode:Unknow mode = 3
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025986] InitFrequencyCalibration: frequency offset in the EEPROM = 168
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025987] <--- InitFrequencyCalibration
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025996] RTMPSetPhyMode: channel is out of range, use first channel=1 
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.025998] RTMPSetPhyMode: Update for STA
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028167] MCS Set = ff ff 00 00 01
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028246] 80211> re-init bands...
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028247] 80211> CurTxPower = 20 dBm
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028249] ====> Radar Channel 52
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028250] ====> Radar Channel 54
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028251] ====> Radar Channel 56
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028252] ====> Radar Channel 60
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028252] ====> Radar Channel 62
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028253] ====> Radar Channel 64
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028254] ====> Radar Channel 100
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028255] ====> Radar Channel 104
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028256] 80211> TxStream = 2
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028261] Chan 167 (frq 5835):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028262] Chan 169 (frq 5845):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028263] Chan 171 (frq 5855):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028264] Chan 173 (frq 5865):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028265] Chan 184 (frq 4920):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028266] Chan 188 (frq 4940):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028267] Chan 192 (frq 4960):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028268] Chan 196 (frq 4980):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028269] Chan 208 (frq 6040):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028270] Chan 212 (frq 6060):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028270] Chan 216 (frq 6080):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028272] RTMPDrvOpen(1):Check if PDMA is idle!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.028343] RTMPDrvOpen(2):Check if PDMA is idle!
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <info>  [1493559107.2852] device (wlan0): supplicant interface state: scanning -> disabled
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <info>  [1493559107.2866] device (wlan0): supplicant interface state: disabled -> inactive
Apr 30 16:31:47 amr-HP-Notebook wpa_supplicant[1450]: wlan0: Reject scan trigger since one is already pending
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <warn>  [1493559107.2874] device (wlan0): add_pending_action (2): 'scan' already pending
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: file devices/nm-device.c: line 10056 (nm_device_add_pending_action): should not be reached
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <info>  [1493559107.2900] policy: auto-activating connection 'STCS-Guest'
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <info>  [1493559107.2922] device (wlan0): Activation: starting connection 'STCS-Guest' (81a2ccb5-a793-4627-b472-2d7666b07eec)
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <info>  [1493559107.2942] device (wlan0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <info>  [1493559107.2947] manager: NetworkManager state is now CONNECTING
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.053612] CFG80211DRV_IoctlHandle: CMD_RTPRIV_IOCTL_80211_NETDEV_EVENT
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.085169] TX0 power compensation = 0x38
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.085334] TX1 power compensation = 0x38
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.086348] ERROR mt766u_sta:RTMPSetTimer failed, Halt in Progress!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108363] andes_usb_erasefw
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108417] ==>rlt_wlan_chip_onoff(): OnOff:0, Reset= 0, pAd->WlanFunCtrl:0x20b, Reg-WlanFunCtrl=0x20b
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108704] receive cmd msg fail(-2)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108709] tx_kickout_fail_count = 0
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108709] tx_timeout_fail_count = 0
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108710] rx_receive_fail_count = 0
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108710] alloc_cmd_msg = 25
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.108711] free_cmd_msg = 25
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160628] RTMP_TimerListRelease: release timer obj ffffc900044d34b0!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160633] RTMP_TimerListRelease: release timer obj ffffc900044d3528!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160635] RTMP_TimerListRelease: release timer obj ffffc900044d35a0!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160636] RTMP_TimerListRelease: release timer obj ffffc900044d3438!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160637] RTMP_TimerListRelease: release timer obj ffffc900044d32d0!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160639] RTMP_TimerListRelease: release timer obj ffffc900044d3348!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160640] RTMP_TimerListRelease: release timer obj ffffc90004464fa0!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160641] RTMP_TimerListRelease: release timer obj ffffc90004453d78!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160642] RTMP_TimerListRelease: release timer obj ffffc90004453df8!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160643] RTMP_TimerListRelease: release timer obj ffffc90004465128!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160645] RTMP_TimerListRelease: release timer obj ffffc90004464eb0!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.160646] RTMP_TimerListRelease: release timer obj ffffc900044650b0!
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <error> [1493559107.4070] platform-linux: do-change-link[4]: failure changing link: failure 99 (Cannot assign requested address)
Apr 30 16:31:47 amr-HP-Notebook NetworkManager[863]: <warn>  [1493559107.4071] device (wlan0): failed to set MAC address to 00:00:00:00:00:00
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.171213] ==>rlt_wlan_chip_onoff(): OnOff:1, Reset= 0, pAd->WlanFunCtrl:0x208, Reg-WlanFunCtrl=0x209
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.172129] -->RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.192053] <--RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.192952] ...........andes_usb_chk_crc
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.281742] andes_usb_reset_wmt
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.302051] -->RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.321962] <--RTUSBVendorReset
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.322193] fw version:0.0.00 build:1
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.322194] build time:201406241830____
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.322198] fw for E3 IC
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.322198] ilm length = 59312(bytes)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.322199] dlm length = 32068(bytes)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.322744] loading fw........
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379291] cfg_mode=5
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379389] Key1Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379396] Key2Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379404] Key3Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379411] Key4Str is Invalid key length(0) or Type(0)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379581] USBAggregation = 1
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379583] 1. Phy Mode = 31
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.379584] NVM is Efuse and its size =1d[1e0-1fc] 
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394770] get_chl_grp:illegal channel (167)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394773] get_chl_grp:illegal channel (167)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394774] get_chl_grp:illegal channel (169)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394775] get_chl_grp:illegal channel (169)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394776] get_chl_grp:illegal channel (171)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394777] get_chl_grp:illegal channel (171)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394778] get_chl_grp:illegal channel (173)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.394779] get_chl_grp:illegal channel (173)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.396052] Country Region from e2p = ffff
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.403014] mt76x2_get_external_lna_gain::LNA type=0x0, BLNAGain=0xffffff8d, ALNAGain0=0xffffff89, ALNAGain1=0xffffff88, ALNAGain2=0xffffff87
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.403019] 2. Phy Mode = 31
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.403022] 3. Phy Mode = 31
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.403182] andes_usb_fw_init
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.475866] AntCfgInit: primary/secondary ant 0/1
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.475870] andes_load_cr:cr_type(2)
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476577] ChipStructAssign(): MT76x2 hook !
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476701] ---> InitFrequencyCalibration
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476702] InitFrequencyCalibrationMode:Unknow mode = 3
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476703] InitFrequencyCalibration: frequency offset in the EEPROM = 168
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476705] <--- InitFrequencyCalibration
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476712] RTMPSetPhyMode: channel is out of range, use first channel=1 
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.476714] RTMPSetPhyMode: Update for STA
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478829] MCS Set = ff ff 00 00 01
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478909] 80211> re-init bands...
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478911] 80211> CurTxPower = 20 dBm
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478912] ====> Radar Channel 52
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478913] ====> Radar Channel 54
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478914] ====> Radar Channel 56
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478915] ====> Radar Channel 60
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478916] ====> Radar Channel 62
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478917] ====> Radar Channel 64
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478918] ====> Radar Channel 100
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478919] ====> Radar Channel 104
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478920] 80211> TxStream = 2
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478926] Chan 167 (frq 5835):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478927] Chan 169 (frq 5845):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478928] Chan 171 (frq 5855):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478929] Chan 173 (frq 5865):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478930] Chan 184 (frq 4920):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478931] Chan 188 (frq 4940):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478932] Chan 192 (frq 4960):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478933] Chan 196 (frq 4980):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478934] Chan 208 (frq 6040):	not allowed!
Apr 30 16:31:47 amr-HP-Notebook kernel: [19906.478935] Chan 212 (frq 6060):	not allowed!

```

-------------------------------------------------------------------------------------------------
Update on 2 May 2017, 
The network card seems to be getting disabled by the network manager, 
and to bring it back I have to run below commands, 
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=2
sudo service network-manager restart
 
I already followed the steps here to get the network card to work, [https://ubuntuforums.org/showthread.php?t=2304607&page=6](https://ubuntuforums.org/showthread.php?t=2304607&page=6) 

below is the log, 

```

ay  2 17:47:05 amr-HP-Notebook nm-dispatcher: req:1 'down' [wlo1]: new request (1 scripts)
May  2 17:47:05 amr-HP-Notebook nm-dispatcher: req:1 'down' [wlo1]: start running ordered scripts...
May  2 17:47:05 amr-HP-Notebook gnome-session[2260]: [3399:3442:0502/174705.839229:ERROR:connection_factory_impl.cc(386)] Failed to connect to MCS endpoint with error -106
May  2 17:47:06 amr-HP-Notebook wpa_supplicant[11476]: wlo1: SME: Trying to authenticate with 0c:d9:96:4d:8e:05 (SSID='STCS-Guest' freq=2412 MHz)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.409666] wlo1: authenticate with 0c:d9:96:4d:8e:05
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.434394] wlo1: send auth to 0c:d9:96:4d:8e:05 (try 1/3)
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2439] device (wlo1): supplicant interface state: disconnected -> authenticating
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.447764] wlo1: authenticated
May  2 17:47:06 amr-HP-Notebook wpa_supplicant[11476]: wlo1: Trying to associate with 0c:d9:96:4d:8e:05 (SSID='STCS-Guest' freq=2412 MHz)
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2613] device (wlo1): supplicant interface state: authenticating -> associating
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.452077] wlo1: associate with 0c:d9:96:4d:8e:05 (try 1/3)
May  2 17:47:06 amr-HP-Notebook wpa_supplicant[11476]: wlo1: Associated with 0c:d9:96:4d:8e:05
May  2 17:47:06 amr-HP-Notebook wpa_supplicant[11476]: wlo1: CTRL-EVENT-CONNECTED - Connection to 0c:d9:96:4d:8e:05 completed [id=0 id_str=]
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.460321] wlo1: RX AssocResp from 0c:d9:96:4d:8e:05 (capab=0x1421 status=0 aid=159)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.461638] wlo1: associated
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2759] device (wlo1): supplicant interface state: associating -> completed
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2759] device (wlo1): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'STCS-Guest'.
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2761] device (wlo1): state change: config -> ip-config (reason 'none') [50 70 0]
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2768] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469937] cfg80211: Regulatory domain changed to country: US
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469942] cfg80211:  DFS Master region: FCC
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469945] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469951] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469956] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469961] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469965] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469969] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.469973] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
May  2 17:47:06 amr-HP-Notebook wpa_supplicant[11476]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=US
May  2 17:47:06 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736426.2801] dhcp4 (wlo1): dhclient started with pid 12160
May  2 17:47:06 amr-HP-Notebook dhclient[12160]: DHCPDISCOVER on wlo1 to 255.255.255.255 port 67 interval 3 (xid=0xb709091a)
May  2 17:47:06 amr-HP-Notebook kernel: [ 5095.634688] wlo1: Limiting TX power to 20 dBm as advertised by 0c:d9:96:4d:8e:05
May  2 17:47:07 amr-HP-Notebook avahi-daemon[785]: Joining mDNS multicast group on interface wlo1.IPv6 with address fe80::4daf:251b:ab63:62e3.
May  2 17:47:07 amr-HP-Notebook avahi-daemon[785]: New relevant interface wlo1.IPv6 for mDNS.
May  2 17:47:07 amr-HP-Notebook avahi-daemon[785]: Registering new address record for fe80::4daf:251b:ab63:62e3 on wlo1.*.
May  2 17:47:07 amr-HP-Notebook gnome-session[2260]: [3399:3649:0502/174707.941376:ERROR:get_updates_processor.cc(244)] PostClientToServerMessage() failed during GetUpdates
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: Internet Systems Consortium DHCP Client 4.3.3
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: Copyright 2004-2015 Internet Systems Consortium.
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: All rights reserved.
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: For info, please visit https://www.isc.org/software/dhcp/
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: 
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: Listening on LPF/wlo1/3c:a0:67:de:f3:27
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: Sending on   LPF/wlo1/3c:a0:67:de:f3:27
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: Sending on   Socket/fallback
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: DHCPRELEASE on wlo1 to 192.168.43.1 port 67 (xid=0x67254f99)
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: send_packet: Network is unreachable
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: send_packet: please consult README file regarding broadcast address.
May  2 17:47:08 amr-HP-Notebook dhclient[12182]: dhclient.c:2474: Failed to send 300 byte long packet over fallback interface.
May  2 17:47:08 amr-HP-Notebook root: /etc/dhcp/dhclient-enter-hooks.d/avahi-autoipd returned non-zero exit status 1
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.089274] wlo1: deauthenticating from 0c:d9:96:4d:8e:05 by local choice (Reason: 3=DEAUTH_LEAVING)
May  2 17:47:08 amr-HP-Notebook wpa_supplicant[11476]: wlo1: CTRL-EVENT-DISCONNECTED bssid=0c:d9:96:4d:8e:05 reason=3 locally_generated=1
May  2 17:47:08 amr-HP-Notebook avahi-daemon[785]: Interface wlo1.IPv6 no longer relevant for mDNS.
May  2 17:47:08 amr-HP-Notebook avahi-daemon[785]: Leaving mDNS multicast group on interface wlo1.IPv6 with address fe80::4daf:251b:ab63:62e3.
May  2 17:47:08 amr-HP-Notebook dhclient[12160]: receive_packet failed on wlo1: Network is down
May  2 17:47:08 amr-HP-Notebook NetworkManager[11452]: <warn>  [1493736428.9157] sup-iface[0x14f76f0,wlo1]: connection disconnected (reason -3)
May  2 17:47:08 amr-HP-Notebook avahi-daemon[785]: Withdrawing address record for fe80::4daf:251b:ab63:62e3 on wlo1.
[B]May  2 17:47:08 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736428.9210] device (wlo1): supplicant interface state: completed -> disabled
[/B]May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114106] cfg80211: World regulatory domain updated:
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114109] cfg80211:  DFS Master region: unset
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114111] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114113] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114115] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114116] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114118] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114120] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114122] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114123] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
May  2 17:47:08 amr-HP-Notebook kernel: [ 5098.114124] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
May  2 17:47:08 amr-HP-Notebook gnome-session[2260]: [3399:3649:0502/174708.922078:ERROR:get_updates_processor.cc(244)] PostClientToServerMessage() failed during GetUpdates
May  2 17:47:09 amr-HP-Notebook dhclient[12160]: DHCPDISCOVER on wlo1 to 255.255.255.255 port 67 interval 6 (xid=0xb709091a)
May  2 17:47:09 amr-HP-Notebook dhclient[12160]: send_packet: Network is down
May  2 17:47:09 amr-HP-Notebook dhclient[12160]: dhclient.c:2098: Failed to send 300 byte long packet over wlo1 interface.
May  2 17:47:10 amr-HP-Notebook whoopsie[799]: [17:47:10] Cannot reach: https://daisy.ubuntu.com
May  2 17:47:10 amr-HP-Notebook gnome-session[2260]: [3399:3649:0502/174710.412906:ERROR:get_updates_processor.cc(244)] PostClientToServerMessage() failed during GetUpdates
May  2 17:47:10 amr-HP-Notebook whoopsie[799]: [17:47:10] Cannot reach: https://daisy.ubuntu.com
May  2 17:47:10 amr-HP-Notebook kernel: [ 5099.605040] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: Internet Systems Consortium DHCP Client 4.3.3
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: Copyright 2004-2015 Internet Systems Consortium.
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: All rights reserved.
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: For info, please visit https://www.isc.org/software/dhcp/
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: 
May  2 17:47:10 amr-HP-Notebook wpa_supplicant[11476]: nl80211: deinit ifname=wlo1 disabled_11b_rates=0
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: Listening on LPF/enp2s0/40:b0:34:97:ca:04
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: Sending on   LPF/enp2s0/40:b0:34:97:ca:04
May  2 17:47:10 amr-HP-Notebook dhclient[12219]: Sending on   Socket/fallback
May  2 17:47:10 amr-HP-Notebook wpa_supplicant[11476]: wlo1: CTRL-EVENT-TERMINATING
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736430.5085] supplicant: wpa_supplicant stopped
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736430.5085] device (wlo1): supplicant interface state: disabled -> down
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736430.5087] device (wlo1): state change: ip-config -> unavailable (reason 'supplicant-failed') [70 20 10]
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736430.5411] dhcp4 (wlo1): canceled DHCP transaction, DHCP client pid 12160
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736430.5411] dhcp4 (wlo1): state changed unknown -> done
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736430.5529] manager: NetworkManager state is now CONNECTED_LOCAL
May  2 17:47:10 amr-HP-Notebook NetworkManager[11452]: <warn>  [1493736430.5535] sup-iface: failed to remove network: The name :1.201 was not provided by any .service files
May  2 17:47:10 amr-HP-Notebook kernel: [ 5099.921126] r8169 0000:02:00.0 enp2s0: link down
May  2 17:47:10 amr-HP-Notebook kernel: [ 5099.921309] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
May  2 17:47:20 amr-HP-Notebook NetworkManager[11452]: <info>  [1493736440.7792] supplicant: wpa_supplicant die count reset
May  2 17:47:22 amr-HP-Notebook kernel: [ 5111.447868] rtlwifi:rtl_action_proc():<10000-1> sta is NULL
May  2 17:47:22 amr-HP-Notebook kernel: [ 5111.447877] rtlwifi:rtl_action_proc():<10000-1> sta is NULL
May  2 17:47:27 amr-HP-Notebook gnome-session[2260]: [3399:3399:0502/174727.786223:ERROR:gcm_channel_status_request.cc(127)] GCM channel request failed.
May  2 17:47:32 amr-HP-Notebook kernel: [ 5121.398746] rtlwifi:rtl_action_proc():<10000-1> sta is NULL
May  2 17:47:32 amr-HP-Notebook kernel: [ 5121.398754] rtlwifi:rtl_action_proc():<10000-1> sta is NULL
May  2 17:47:56 amr-HP-Notebook gnome-session[2260]: [3399:3399:0502/174756.578349:ERROR:gcm_channel_status_request.cc(127)] GCM channel request failed.
May  2 17:48:48 amr-HP-Notebook gnome-session[2260]: [3399:3399:0502/174848.815892:ERROR:gcm_channel_status_request.cc(127)] GCM channel request failed.

```

---

