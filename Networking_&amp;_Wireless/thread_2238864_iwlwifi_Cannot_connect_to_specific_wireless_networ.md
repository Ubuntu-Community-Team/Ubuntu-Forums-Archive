---
title: "iwlwifi: Cannot connect to specific wireless networks (Dell L501x)"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by darius-scerb on 2014-08-10
I have a Dell XPS L501x laptop (running 14.04) and for some reason I cannot connect to specific wireless networks. One example is my uni network (eduroam), another is my current home network. Many other wireless networks, both unencrypted, and WPA2 encrypted work just fine. This is a dual-boot system with Windows, and I can connect just fine to all of them on Windows, so the wireless device is working fine.

The wireless card is:
```

...
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
...

```

and the module used is iwlwifi.
```

darka@bloop:~$ lsmod | grep iwl
iwldvm                243680  0 
mac80211              687021  1 iwldvm
iwlwifi               190534  1 iwldvm
cfg80211              521225  4 iwlwifi,mac80211,rndis_wlan,iwldvm

```

dmesg output when trying to connect:
```

[  116.202460] wlan0: authenticate with 6c:19:8f:01:ea:e6
[  116.208195] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
[  116.409281] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
[  116.613293] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
[  116.817386] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
[  117.351298] wlan0: authenticate with 6c:19:8f:01:ea:e6
[  117.352234] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
[  117.553901] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
[  117.757497] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
[  117.961689] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
[  118.991521] wlan0: authenticate with 6c:19:8f:01:ea:e6
[  118.994858] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
[  119.197664] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
[  119.401632] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
[  119.605655] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
[  121.121561] wlan0: authenticate with 6c:19:8f:01:ea:e6
[  121.122535] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
[  121.325881] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
[  121.529892] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
[  121.733983] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
[  132.651649] wlan0: authenticate with 6c:19:8f:01:ea:e6
[  132.652784] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
[  132.855254] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
[  133.059258] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
[  133.263291] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out

```

/var/log/syslog:
```

Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) starting connection 'Robot-Uprising-v3'
Aug 10 20:25:44 bloop NetworkManager[826]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 10 20:25:44 bloop NetworkManager[826]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0/wireless): connection 'Robot-Uprising-v3' has security, and secrets exist.  No new secrets needed.
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Config: added 'ssid' value 'Robot-Uprising-v3'
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Config: added 'scan_ssid' value '1'
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Config: added 'psk' value '<omitted>'
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 10 20:25:44 bloop NetworkManager[826]: <info> Config: set interface ap_scan to 1
Aug 10 20:25:44 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: inactive -> scanning
Aug 10 20:25:50 bloop wpa_supplicant[884]: message repeated 8 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Aug 10 20:25:50 bloop wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 6c:19:8f:01:ea:e6 (SSID='Robot-Uprising-v3' freq=2437 MHz)
Aug 10 20:25:50 bloop kernel: [  116.202460] wlan0: authenticate with 6c:19:8f:01:ea:e6
Aug 10 20:25:50 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 10 20:25:50 bloop kernel: [  116.208195] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
Aug 10 20:25:50 bloop kernel: [  116.409281] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
Aug 10 20:25:51 bloop kernel: [  116.613293] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
Aug 10 20:25:51 bloop kernel: [  116.817386] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
Aug 10 20:25:51 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 10 20:25:51 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 10 20:25:51 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 10 20:25:51 bloop wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 6c:19:8f:01:ea:e6 (SSID='Robot-Uprising-v3' freq=2437 MHz)
Aug 10 20:25:51 bloop kernel: [  117.351298] wlan0: authenticate with 6c:19:8f:01:ea:e6
Aug 10 20:25:51 bloop kernel: [  117.352234] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
Aug 10 20:25:51 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 10 20:25:52 bloop kernel: [  117.553901] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
Aug 10 20:25:52 bloop kernel: [  117.757497] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
Aug 10 20:25:52 bloop kernel: [  117.961689] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
Aug 10 20:25:52 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 10 20:25:52 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 10 20:25:52 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 10 20:25:53 bloop wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 6c:19:8f:01:ea:e6 (SSID='Robot-Uprising-v3' freq=2437 MHz)
Aug 10 20:25:53 bloop kernel: [  118.991521] wlan0: authenticate with 6c:19:8f:01:ea:e6
Aug 10 20:25:53 bloop kernel: [  118.994858] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
Aug 10 20:25:53 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 10 20:25:53 bloop kernel: [  119.197664] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
Aug 10 20:25:53 bloop kernel: [  119.401632] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
Aug 10 20:25:54 bloop kernel: [  119.605655] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
Aug 10 20:25:54 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 10 20:25:55 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 10 20:25:55 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 10 20:25:55 bloop wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 6c:19:8f:01:ea:e6 (SSID='Robot-Uprising-v3' freq=2437 MHz)
Aug 10 20:25:55 bloop kernel: [  121.121561] wlan0: authenticate with 6c:19:8f:01:ea:e6
Aug 10 20:25:55 bloop kernel: [  121.122535] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
Aug 10 20:25:55 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 10 20:25:55 bloop kernel: [  121.325881] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
Aug 10 20:25:56 bloop kernel: [  121.529892] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
Aug 10 20:25:56 bloop kernel: [  121.733983] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
Aug 10 20:25:56 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Robot-Uprising-v3" auth_failures=1 duration=10
Aug 10 20:25:56 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 10 20:26:01 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 10 20:26:01 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 10 20:26:06 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 10 20:26:07 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="Robot-Uprising-v3"
Aug 10 20:26:07 bloop wpa_supplicant[884]: wlan0: SME: Trying to authenticate with 6c:19:8f:01:ea:e6 (SSID='Robot-Uprising-v3' freq=2437 MHz)
Aug 10 20:26:07 bloop kernel: [  132.651649] wlan0: authenticate with 6c:19:8f:01:ea:e6
Aug 10 20:26:07 bloop kernel: [  132.652784] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 1/3)
Aug 10 20:26:07 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 10 20:26:07 bloop kernel: [  132.855254] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 2/3)
Aug 10 20:26:07 bloop kernel: [  133.059258] wlan0: direct probe to 6c:19:8f:01:ea:e6 (try 3/3)
Aug 10 20:26:07 bloop kernel: [  133.263291] wlan0: authentication with 6c:19:8f:01:ea:e6 timed out
Aug 10 20:26:07 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Robot-Uprising-v3" auth_failures=2 duration=20
Aug 10 20:26:07 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 10 20:26:08 bloop kernel: [  133.975363] ACPI: Failed to switch the brightness
Aug 10 20:26:08 bloop kernel: [  134.152909] ACPI: Failed to switch the brightness
Aug 10 20:26:08 bloop kernel: [  134.331511] ACPI: Failed to switch the brightness
Aug 10 20:26:09 bloop NetworkManager[826]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Aug 10 20:26:09 bloop NetworkManager[826]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Aug 10 20:26:09 bloop NetworkManager[826]: <warn> Activation (wlan0) failed for connection 'Robot-Uprising-v3'
Aug 10 20:26:09 bloop NetworkManager[826]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 10 20:26:09 bloop NetworkManager[826]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 10 20:26:09 bloop wpa_supplicant[884]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 10 20:26:10 bloop NetworkManager[826]: <info> (wlan0): supplicant interface state: disconnected -> inactive

```

I tried updating to the latest kernel but the issue is exactly the same as with the default kernel. :(
```

darka@bloop:~$ uname -a
Linux bloop 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
I've looked for similar problems and tried loading the iwlwifi module with various combinations of 11n_disable=1, bt_coex_active=0 and swcrypto=1 but none of them seem to have worked. The logs give exactly the same errors.

All help is very much appreciated!

---

### Post by praseodym on 2014-08-10
Try to deactivate the N-mode and the network queue:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by darius-scerb on 2014-08-10
Thanks for the quick reply but it didn't help - the errors are exactly the same. :(

---

### Post by praseodym on 2014-08-10
Check the nameservers in

**cat /etc/resolv.conf**

---

### Post by darius-scerb on 2014-08-10
This has nothing to do with nameservers - I can't even connect to the access point.

---

### Post by weatherman2 on 2014-08-10
How is the security of your home wireless access point set up?  (You say you can connect to it in Windows but not Ubuntu right?).  WPA2 + AES?  WPA2 + WPA Mixed?  How is it set up?  Does it allow 802.11n only or also 802.11n + 802.11g?

---

### Post by jeremy31 on 2014-08-10
Anyone know why [COLOR=#000000][FONT=Ubuntu Mono]rndis_wlan is in the lsmod results?[/FONT][/COLOR]

---

### Post by wildmanne39 on 2014-08-10
rndis_wlan is a module loaded for an usb wireless adaptor, it is possibly conflicting with your internal driver that is loaded. You can blacklist it if you do not need it:
```
echo "blacklist rndis_wlan" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by darius-scerb on 2014-08-16
The access point is set up with wireless mode B/G/N and security is set to WPA2 Mode Only (not WPA/WPA2 mixed). I believe rndis_wlan is loaded because I'm tethering wifi over my phone, otherwise I would have no connection at all. As I said, wifi does work fine in Windows. Any other ideas?

---

### Post by varunendra on 2014-08-17
Perhaps run the wireless_script and show us its report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Run the script AFTER the internal card tries to connect and fails, so that the dmesg part of the report also contains the disconnection logs. Preferably, use the "No Internet" method after a fresh boot and a connection attempt WITHOUT tethering the phone, so that we have a clean report (no chance of conflicting modules).

---

### Post by darius-scerb on 2014-08-18
Rebooted the machine and tried connecting to the network (access point is Robot-Uprising-v3). Here's the wireless-info output:

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


bloop 3.16.0-031600-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
Memory : 2743 MB
Uptime : 22:32:48 up 1 min,  2 users,  load average: 2.45, 1.21, 0.46




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1325]
    Kernel driver in use: iwlwifi
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:046e]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwldvm                243680  0 
dell_wmi               12681  0 
mac80211              687021  1 iwldvm
sparse_keymap          13890  1 dell_wmi
iwlwifi               190534  1 iwldvm
cfg80211              521225  3 iwlwifi,mac80211,iwldvm
wmi                    19379  1 dell_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (12): 11n_disable=1 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | uapsd_disable=N | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | iwlwifi | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    BTWifi-X:        Infra, <MAC C-09 BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2 Enterprise
    BTHub3-HZWH:     Infra, <MAC C-07 BTHub3-HZWH>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    BTHub5-HNQ9:     Infra, <MAC C-02 BTHub5-HNQ9>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    ozcctv & sat:    Infra, <MAC C-04 ozcctv <MAC C-NA ozcctv <MAC ID removed> sat 1> sat>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    virginmedia9502101: Infra, <MAC C-05 virginmedia9502101>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA2
    SKY4D30C:        Infra, <MAC C-01 SKY4D30C>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTHub4-QPJK:     Infra, <MAC C-18 BTHub4-QPJK>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTWifi-with-FON: Infra, <MAC C-08 BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75
    BTWiFi-with-FON: Infra, <MAC C-03 BTWiFi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    BTWifi-with-FON: Infra, <MAC C-17 BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    SKYF6849:        Infra, <MAC C-20 SKYF6849>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    TALKTALK-2EC314: Infra, <MAC C-NA TALKTALK-2EC314 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Suga:            Infra, <MAC C-22 Suga>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    HTC Windows Phone 8S by HTC3210: Infra, <MAC C-NA HTC Windows Phone 8S by HTC3210 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BTWiFi-with-FON: Infra, <MAC C-10 BTWiFi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    BTHub5-X2Z5:     Infra, <MAC C-12 BTHub5-X2Z5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BTHub3-5FSC:     Infra, <MAC C-11 BTHub3-5FSC>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC C-13 BTWiFi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    BTWiFi-with-FON: Infra, <MAC C-NA BTWiFi-with-FON 4>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    virginmedia5580871: Infra, <MAC C-14 virginmedia5580871>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Tafari:          Infra, <MAC C-NA Tafari 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTHub5-2M6M:     Infra, <MAC C-15 BTHub5-2M6M>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    TALKTALK-EAEC48: Infra, <MAC C-16 TALKTALK-EAEC48>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Robot-Uprising-v3: Infra, <MAC C-23 Robot-Uprising-v3>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    EE-BrightBox-fsebke: Infra, <MAC C-19 EE-BrightBox-fsebke>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTHub3-5JF2:     Infra, <MAC C-NA BTHub3-5JF2 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    TALKTALK-378148: Infra, <MAC C-21 TALKTALK-378148>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    TALKTALK-382A1C: Infra, <MAC C-24 TALKTALK-382A1C>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


Campus               : ssid=Campus | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CampusGuest          : ssid=CampusGuest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Candy Van            : ssid=Candy Van | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
central              : ssid=central | mac-address=<MAC wlan0> | ipv6=ignore | ipv4=auto 
central 1            : ssid=central | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ClubWorkspace        : ssid=ClubWorkspace | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
eduroam              : ssid=eduroam | mac-address=<MAC wlan0> | ca-cert=/home/darka/tmp/UTN-USERFirst-Hardware-der.crt system-ca-certs=true | ipv4=auto 
GWLAN                : ssid=GWLAN | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HTC Portable Hotspot : ssid=HTC Portable Hotspot | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Robot Uprising       : ssid=Robot Uprising | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Robot-Uprising-v3    : ssid=Robot-Uprising-v3 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SKYD40C2             : ssid=SKYD40C2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
UPC1377334           : ssid=UPC1377334 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IE.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 SKY4D30C>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SKY4D30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002337b2a9ba2
                    Extra: Last beacon: 12656ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 BTHub5-HNQ9>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-HNQ9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016855d0370a
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 BTWiFi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016855d11cfc
                    Extra: Last beacon: 60ms ago
          Cell 04 - Address: <MAC C-04 ozcctv <MAC C-NA ozcctv <MAC ID removed> sat 1> sat>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ozcctv & sat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f2383f16f
                    Extra: Last beacon: 27420ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 virginmedia9502101>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"virginmedia9502101"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000031ff59c
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Carlos Ortiz>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Carlos Ortiz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 BTHub3-HZWH>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-HZWH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000030606d64a5
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000030606e3ed2
                    Extra: Last beacon: 60ms ago
          Cell 09 - Address: <MAC C-09 BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000030606e51e9
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC C-10 BTWiFi-with-FON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006419016f6
                    Extra: Last beacon: 60ms ago
          Cell 11 - Address: <MAC C-11 BTHub3-5FSC>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-5FSC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004e82f1b834
                    Extra: Last beacon: 432ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 BTHub5-X2Z5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-X2Z5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006418f4124
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 BTWiFi-with-FON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000063ff38180
                    Extra: Last beacon: 27352ms ago
          Cell 14 - Address: <MAC C-14 virginmedia5580871>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"virginmedia5580871"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000081490a36a9
                    Extra: Last beacon: 15948ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 BTHub5-2M6M>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-2M6M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000640113555
                    Extra: Last beacon: 25356ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 TALKTALK-EAEC48>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-EAEC48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039c4642148
                    Extra: Last beacon: 12736ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006240548b4a
                    Extra: Last beacon: 60ms ago
          Cell 18 - Address: <MAC C-18 BTHub4-QPJK>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-QPJK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006240547525
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC C-19 EE-BrightBox-fsebke>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"EE-BrightBox-fsebke"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001396ed4a183
                    Extra: Last beacon: 332ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC C-20 SKYF6849>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SKYF6849"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c5efa6fbb
                    Extra: Last beacon: 19004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC C-21 TALKTALK-378148>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-378148"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000108c54170
                    Extra: Last beacon: 19172ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC C-22 Suga>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Suga"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013009fc183
                    Extra: Last beacon: 19164ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC C-23 Robot-Uprising-v3>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Robot-Uprising-v3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000055d5709e8
                    Extra: Last beacon: 15824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC C-24 TALKTALK-382A1C>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-382A1C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002dccc95156
                    Extra: Last beacon: 15720ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC C-25 TALKTALK-4A727C>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-4A727C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000140fd89166
                    Extra: Last beacon: 208ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwldvm]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     730E17C75BE53916FEA875B
depends:        iwlwifi,mac80211,cfg80211


[dell_wmi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     25903BF68FE916DB1314466
depends:        wmi,sparse-keymap


[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     CD2FA2DD36A6D738B95D00F
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
srcversion:     D86AFD97E7F71C59777C05F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modules]
loop


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
                    options iwlwifi bt_coex_active=0
                    options iwlwifi wd_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en
nvidia-installer-disable-nouveau.conf: blacklist nouveau
                    options nouveau modeset=0
qemu-system-x86.conf: options kvm_intel nested=1




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.16.0-031600-generic root=UUID=cd744d40-f55e-4663-a52a-cc616ee74d52 ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.025984] Initializing cgroup subsys net_cls
[    0.025997] Initializing cgroup subsys net_prio
[    0.676733] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.677191] audit: initializing netlink subsys (disabled)
[    1.215395] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   13.059393] wmi: Mapper loaded
[   13.614073] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.614226] iwlwifi 0000:04:00.0: irq 49 for MSI/MSI-X
[   14.061936] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   15.536347] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.536352] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.536355] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.536358] iwlwifi 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   15.536493] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   15.666557] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.782548] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.032089] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   24.039383] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   24.077958] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   24.085279] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   24.123159] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.491343] wlan0: authenticate with <MAC C-23 Robot-Uprising-v3>
[   73.498362] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 1/3)
[   73.702450] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 2/3)
[   73.906573] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 3/3)
[   74.110747] wlan0: authentication with <MAC C-23 Robot-Uprising-v3> timed out
[   85.494977] wlan0: authenticate with <MAC C-23 Robot-Uprising-v3>
[   85.496067] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 1/3)
[   85.697899] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 2/3)
[   85.902052] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 3/3)
[   86.106194] wlan0: authentication with <MAC C-23 Robot-Uprising-v3> timed out
[   87.031538] wlan0: authenticate with <MAC C-23 Robot-Uprising-v3>
[   87.034728] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 1/3)
[   87.238859] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 2/3)
[   87.442958] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 3/3)
[   87.647078] wlan0: authentication with <MAC C-23 Robot-Uprising-v3> timed out
[   89.089256] wlan0: authenticate with <MAC C-23 Robot-Uprising-v3>
[   89.090404] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 1/3)
[   89.292161] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 2/3)
[   89.496285] wlan0: direct probe to <MAC C-23 Robot-Uprising-v3> (try 3/3)
[   89.700402] wlan0: authentication with <MAC C-23 Robot-Uprising-v3> timed out


    ======== Done ========

```

---

### Post by varunendra on 2014-08-19
> **darius-scerb said:**
> ```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   **[COLOR="#FF0000"]Tx-Power=14 dBm[/COLOR]**   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
....
(Region : "en_IE.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
....
....
          Cell 23 - Address: <MAC C-23 Robot-Uprising-v3>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    **ESSID:"Robot-Uprising-v3"**
                    ....
                        **[COLOR="#FF0000"]Group Cipher : TKIP[/COLOR]**
....

```

The above are what I believe points of major concern at the moment. The regdomain settings for IE (Ireland) as well as the defaulted '00' (which is currently set) both allow Transmitting signal strengths upto 20 dBm, but your card is transmitting at 14 dBm only. Then there is that unusual combination of WPA2 with TKIP in the router's signal encryption.

Please try these for now -

[INDENT]**1)** Change the encryption algorithm in your router to AES (CCMP). Leave the encryption type to WPA2, it is the best, but TKIP is problematic. Remember - pure WPA2, no WPA, no WPA/WPA2 mixed mode. Reboot the router after saving the change.

**2)** In Ubuntu, try explicitly defining the Country Code for RegDomain settings. Assuming from the Regional Language setting that you are in Ireland -
```
sudo sed -i 's/^REG.*=$/&IE/' /etc/default/crda
```
This will take effect after a reboot. To force "IE" immediately without rebooting, you may try -
```
sudo reg set IE
```
If you are in some place other than Ireland, please replace "IE" with its country-code. Refer to this table to find country codes : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

**3)** After having above implemented, see if your card can accept a forced Tx value -
```
sudo iwconfig wlan0 txpower 20
```
If it returns some error, or seems to silently reject it, you may try other values between 14-20.[/INDENT]

Let us know if any of it works (or not), and accordingly I may try to play with module parameters you have used/not used.

---

### Post by darius-scerb on 2014-08-19
1) My router settings are already set to AES and WPA2 Only. I took a quick look at the rest of the wireless access points available (the scan output) and not a single one says AES, so I assume it's just not mentioned in scan output? In any case re-saving configuration and rebooting the router did not help.

2) I'm based in London, but I installed Ubuntu while in Ireland, so that's the reason for the wrong locale setting. I now changed it to GB, and ran all of the commands you listed. The problem remains the same after rebooting.

3) I don't get any errors when running the command, but Tx value doesn't seem to change. Running 'iw-config' still shows Tx-Power=14. I tried other values as well, but it always stays at 14.

Any other ideas?

---

### Post by varunendra on 2014-08-19
> **darius-scerb said:**
> 1) My router settings are already set to AES and WPA2 Only.

I can bet all my beans and user title, and the laptop I'm typing on that it is not. Did you read the "CCMP" typed in capital in brackets just after AES? That's what *some* router interfaces may call it.

Regarding this -
> **darius-scerb said:**
> I took a quick look at the rest of the wireless access points available (the scan output) and not a single one says AES, so I assume it's just not mentioned in scan output?
Did you see the encryption setting in Cell-5 of your output? Or 20?

Using TKIP with WPA/WPA2 mixed mode is understandable (TKIP is essential requirement for WPA(1)), but those three others (Cell - 2, 12, 15) using it with WPA2 suggest to me that something is wrong with either the tech-support guy in your area, or the diet you get there.

While WPA2 supports TKIP, the 'Standard' combination is : AES (CCMP) with WPA2, TKIP with WPA (1). And some drivers may get confused if you deviate from 'standards'. Even if it is not the cause of the problem, it will certainly be making it worse.

---

### Post by darius-scerb on 2014-08-19
> **varunendra said:**
> I can bet all my beans and user title, and the laptop I'm typing on that it is not. Did you read the "CCMP" typed in capital in brackets just after AES? That's what *some* router interfaces may call it.


I attached a picture of the current router configuration. The router is D-Link DSL-3680. I'm guessing the WPA section is then pure lies since it doesn't match the scan output?

> **varunendra said:**
> 
Did you see the encryption setting in Cell-5 of your output? Or 20?

Ok, you're right.

---

### Post by varunendra on 2014-08-19
So it seems it selects the encryption algorithm itself in the background, depending on the selected encryption protocol, and is *supposed* to do that correctly (the description it gives under "WPA" section is excellent). But if the scan report was taken while the settings were already as shown in the screen shot, then its implementation in the router is definitely buggy.

If you changed it just before running the script, maybe try a low update interval value, like 10 seconds just to see if it changes the output in "sudo iwlist scan" result. Reset the value to 3600 second (1 hr) after the test.

As an alternative (less secure, inefficient, but at least consistent with standards), you may try selecting WPA only mode > save > reboot the router and see if the scan result now shows WPA with TKIP only. If yes, does it help connectivity? Does the setting becomes the same as now if resetting back to WPA2 only mode?

I just did a search (on duckduckgo.com) with keyword "D-Link DSL-3680", and instead of production description, 10+ top links that appeared were about connectivity problems. This, to me suggests that this router/modem is indeed problematic. Check its firmware version and make sure it is the latest.

It seems the firmware for it is not directly provided by D-Link, but by "TalkTalk" (is that your ISP?), and post #2 in [this thread]("http://community.talktalk.co.uk/t5/Unlimited-Broadband/firmware-update-for-dlink-DSL-3680/td-p/1113818") on their forum talks about some "TR609" service within the router settings that auto-updates the firmware. If you can't get the issue solved by suggestion found here, perhaps register a complain with them instead (you have a valid concern about that WPA2/TKIP combination).

---

### Post by darius-scerb on 2014-08-20
I now tried WPA only mode, and it did show WPA v1 and TKIP only when doing "iwlist scan", but the connectivity problems remained the same with the exact same errors in dmesg output. I changed it back to "WPA2 Only" and, surprise, no more TKIP:

```

          Cell 17 - Address: <MAC C-17 TALKTALK-01EAE6>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-01EAE6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002589618e
                    Extra: Last beacon: 10704ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

(also, the router was reverted back to default factory settings, so the ESSID has changed)

However, none of this has helped, I'm still getting the exact same errors when trying to connect : - (

---

### Post by varunendra on 2014-08-21
Not expecting much, but can you post a fresh wireless_script report please?

**PS:**
Other experts - I'm too stressed out to be regular on the forums, and am already out of my wits here, so.... [SIZE=3]**[COLOR="#800000"][FONT=Comic Sans MS]PLEASE HELP!![/FONT][/COLOR]**[/SIZE]

---

### Post by praseodym on 2014-08-22
> ```
resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~
```

is empty. CHeck my post on page 1

---

### Post by jeremy31 on 2014-08-22
I only have two ideas, edit the /etc/modprobe.d/iwlwifi file and change the bt_coex_active to bt_coex_active=N and 11n_disable=1 to 11n_disable=8
```
sudo gedit /etc/modprobe.d/iwlwifi.conf
``` will bring up the file in the editor, after making changes, save file, exit gedit and reboot

---

### Post by darius-scerb on 2014-08-24
Fresh wireless-info output (access point is now TALKTALK-01EAE6):

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


bloop 3.16.0-031600-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
Memory : 2743 MB
Uptime : 12:27:03 up 2 min,  2 users,  load average: 1.68, 0.97, 0.38




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1325]
    Kernel driver in use: iwlwifi
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:046e]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwldvm                243680  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
mac80211              687021  1 iwldvm
iwlwifi               190534  1 iwldvm
cfg80211              521225  3 iwlwifi,mac80211,iwldvm
wmi                    19379  1 dell_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (12): 11n_disable=1 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | uapsd_disable=N | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | iwlwifi | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    BTHub3-HZWH:     Infra, <MAC C-08 BTHub3-HZWH>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    BTWifi-X:        Infra, <MAC C-10 BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2 Enterprise
    SKY4D30C:        Infra, <MAC C-05 SKY4D30C>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BTHub5-HNQ9:     Infra, <MAC C-01 BTHub5-HNQ9>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    BTHub4-QPJK:     Infra, <MAC C-04 BTHub4-QPJK>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Suga:            Infra, <MAC C-11 Suga>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    BTHub5-2M6M:     Infra, <MAC C-06 BTHub5-2M6M>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    SKYD4F06:        Infra, <MAC C-03 SKYD4F06>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    BTWifi-with-FON: Infra, <MAC C-09 BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 89
    BTWiFi-with-FON: Infra, <MAC C-02 BTWiFi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    BTWiFi-with-FON: Infra, <MAC C-07 BTWiFi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    BTWiFi:          Infra, <MAC C-21 BTWiFi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    ozcctv & sat:    Infra, <MAC C-14 ozcctv <MAC C-NA ozcctv <MAC ID removed> sat 1> sat>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    virginmedia5580871: Infra, <MAC C-12 virginmedia5580871>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    SKY8D121:        Infra, <MAC C-NA SKY8D121 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    BTWifi-with-FON: Infra, <MAC C-13 BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    BTHub5-X2Z5:     Infra, <MAC C-18 BTHub5-X2Z5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    TALKTALK-2EC314: Infra, <MAC C-15 TALKTALK-2EC314>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    TALKTALK-EAEC48: Infra, <MAC C-NA TALKTALK-EAEC48 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BTHub3-5JF2:     Infra, <MAC C-NA BTHub3-5JF2 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC C-19 BTWiFi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    BTHub3-5FSC:     Infra, <MAC C-NA BTHub3-5FSC 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC C-NA BTWiFi-with-FON 5>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    BTWiFi-with-FON: Infra, <MAC C-17 BTWiFi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    TALKTALK-01EAE6: Infra, <MAC C-20 TALKTALK-01EAE6>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA2
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


Campus               : ssid=Campus | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CampusGuest          : ssid=CampusGuest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Candy Van            : ssid=Candy Van | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
central              : ssid=central | mac-address=<MAC wlan0> | ipv6=ignore | ipv4=auto 
central 1            : ssid=central | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ClubWorkspace        : ssid=ClubWorkspace | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
eduroam              : ssid=eduroam | mac-address=<MAC wlan0> | ca-cert=/home/darka/tmp/UTN-USERFirst-Hardware-der.crt system-ca-certs=true | ipv4=auto 
GWLAN                : ssid=GWLAN | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HTC Portable Hotspot : ssid=HTC Portable Hotspot | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Robot Uprising       : ssid=Robot Uprising | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Robot-Uprising-v3    : ssid=Robot-Uprising-v3 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SKYD40C2             : ssid=SKYD40C2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TALKTALK-01EAE6      : ssid=TALKTALK-01EAE6 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
UPC1377334           : ssid=UPC1377334 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_GB.UTF-8")
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 BTHub5-HNQ9>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-HNQ9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005e3f9dd17b
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 BTWiFi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005e3f9eb66e
                    Extra: Last beacon: 40ms ago
          Cell 03 - Address: <MAC C-03 SKYD4F06>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SKYD4F06"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d3582fc2f
                    Extra: Last beacon: 2928ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 BTHub4-QPJK>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-QPJK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d279b2f298
                    Extra: Last beacon: 3352ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 SKY4D30C>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"SKY4D30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000069217d48d4
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 BTHub5-2M6M>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-2M6M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000767e04f074
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 BTWiFi-with-FON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000767e05c647
                    Extra: Last beacon: 40ms ago
          Cell 08 - Address: <MAC C-08 BTHub3-HZWH>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-HZWH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a09c85cca0
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a09c86ad50
                    Extra: Last beacon: 40ms ago
          Cell 10 - Address: <MAC C-10 BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a09c86b860
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC C-11 Suga>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Suga"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000250a1059f7
                    Extra: Last beacon: 3136ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 virginmedia5580871>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"virginmedia5580871"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f1860e4150
                    Extra: Last beacon: 5980ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d279b2e5ae
                    Extra: Last beacon: 29040ms ago
          Cell 14 - Address: <MAC C-14 ozcctv <MAC C-NA ozcctv <MAC ID removed> sat 1> sat>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ozcctv & sat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bf613fe176
                    Extra: Last beacon: 3324ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 TALKTALK-2EC314>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-2EC314"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b26768b80d
                    Extra: Last beacon: 3088ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 Carlos Ortiz>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Carlos Ortiz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 15412ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 BTWiFi-with-FON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b62d8b180
                    Extra: Last beacon: 348ms ago
          Cell 18 - Address: <MAC C-18 BTHub5-X2Z5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-X2Z5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000767cb21863
                    Extra: Last beacon: 21312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC C-19 BTWiFi-with-FON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000767cb2ee40
                    Extra: Last beacon: 21312ms ago
          Cell 20 - Address: <MAC C-20 TALKTALK-01EAE6>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-01EAE6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000150ba5810d
                    Extra: Last beacon: 200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC C-21 BTWiFi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b62ac8eaa
                    Extra: Last beacon: 3240ms ago
          Cell 22 - Address: <MAC C-22 SKYF6849>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"SKYF6849"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000137a1a07a7
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwldvm]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     730E17C75BE53916FEA875B
depends:        iwlwifi,mac80211,cfg80211


[dell_wmi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     25903BF68FE916DB1314466
depends:        wmi,sparse-keymap


[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     CD2FA2DD36A6D738B95D00F
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
srcversion:     D86AFD97E7F71C59777C05F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modules]
loop


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
                    options iwlwifi bt_coex_active=0
                    options iwlwifi wd_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en
nvidia-installer-disable-nouveau.conf: blacklist nouveau
                    options nouveau modeset=0
qemu-system-x86.conf: options kvm_intel nested=1




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.16.0-031600-generic root=UUID=cd744d40-f55e-4663-a52a-cc616ee74d52 ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.026173] Initializing cgroup subsys net_cls
[    0.026186] Initializing cgroup subsys net_prio
[    0.676709] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.677166] audit: initializing netlink subsys (disabled)
[    1.216076] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.398683] wmi: Mapper loaded
[   12.457837] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.457997] iwlwifi 0000:04:00.0: irq 49 for MSI/MSI-X
[   13.021339] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   14.058121] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.058126] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.058128] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.058131] iwlwifi 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   14.058243] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.237547] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.145366] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.788865] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   24.796157] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   24.833515] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   24.840799] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   24.881358] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   99.201944] wlan0: authenticate with <MAC C-20 TALKTALK-01EAE6>
[   99.205723] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 1/3)
[   99.406405] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 2/3)
[   99.610526] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 3/3)
[   99.814643] wlan0: authentication with <MAC C-20 TALKTALK-01EAE6> timed out
[  100.373940] wlan0: authenticate with <MAC C-20 TALKTALK-01EAE6>
[  100.375315] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 1/3)
[  100.579095] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 2/3)
[  100.783301] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 3/3)
[  100.987388] wlan0: authentication with <MAC C-20 TALKTALK-01EAE6> timed out
[  101.878684] wlan0: authenticate with <MAC C-20 TALKTALK-01EAE6>
[  101.879673] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 1/3)
[  102.080105] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 2/3)
[  102.284171] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 3/3)
[  102.488343] wlan0: authentication with <MAC C-20 TALKTALK-01EAE6> timed out
[  109.253374] wlan0: authenticate with <MAC C-20 TALKTALK-01EAE6>
[  109.254573] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 1/3)
[  109.456610] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 2/3)
[  109.660736] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 3/3)
[  109.864865] wlan0: authentication with <MAC C-20 TALKTALK-01EAE6> timed out
[  120.640623] wlan0: authenticate with <MAC C-20 TALKTALK-01EAE6>
[  120.641938] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 1/3)
[  120.843617] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 2/3)
[  121.047737] wlan0: direct probe to <MAC C-20 TALKTALK-01EAE6> (try 3/3)
[  121.251906] wlan0: authentication with <MAC C-20 TALKTALK-01EAE6> timed out


    ======== Done ========



```

> **praseodym said:**
> resolv.conf is empty. CHeck my post on page 1

NetworkManager writes resolv.conf after it connects to wifi. It is empty because I cannot connect to the access point at all.

> **jeremy31 said:**
> I only have two ideas, edit the /etc/modprobe.d/iwlwifi file and change the bt_coex_active to bt_coex_active=N and 11n_disable=1 to 11n_disable=8
```
sudo gedit /etc/modprobe.d/iwlwifi.conf
``` will bring up the file in the editor, after making changes, save file, exit gedit and reboot

Tried loading the iwlwifi module with those options, but the problem remains. Same error output in dmesg.

---

### Post by praseodym on 2014-08-24
**NetworkManager writes resolv.conf after it connects to wifi. It is empty because I cannot connect to the access point at all.**

Obviously, it does not. So, write it on your own!

---

### Post by darius-scerb on 2014-08-24
> **praseodym said:**
> **NetworkManager writes resolv.conf after it connects to wifi. It is empty because I cannot connect to the access point at all.**

Obviously, it does not. So, write it on your own!

It does not because I cannot connect to the access point. The file resolv.conf contains nameserver info, used for translating hostnames to IP addresses. This is only useful when you actually have an internet connection. Writing the file myself would not solve the problem in this case :)

---

### Post by jeremy31 on 2014-08-24
Just wondering why loop is in /etc/modules
Most have lp and rtc

Encrypted disk?

How many kernels do you have?  Do they all have this issue?

---

### Post by darius-scerb on 2014-08-24
Not really sure why loop is there, I don't have an encrypted disk. I did have a few virtual machine image file systems mounted at some point, which I believe the loop module is used for. I don't think this affects the wifi situation though.

I've tried out the default Ubuntu kernel 3.8.0, 3.13.0, 3.15.5 and 3.16.0. All had the same problem.

---

### Post by praseodym on 2014-08-24
...and you cannot connect because there are no nameservers at all. You can add your router IP address accordingly.

---

### Post by darius-scerb on 2014-08-24
That's not really how the internet works :-D Nameservers are used for translating hostnames to IP addresses. Since I cannot connect to my wireless network (on Linux, works perfectly fine on Windows), I can't even access my router via its IP address, let alone the rest of the internet.

Adding my router's IP address does not fix the problem.

Again, resolv.conf is managed by NetworkManager, and it gets automatically populated when connected to a wireless network. In fact, it gets automatically populated if I connect my smartphone and turn on wifi tethering.

---

### Post by praseodym on 2014-08-24
I changed in "IPv4 settings" to "Automatic (DHCP), addresses only", added these nameservers and it looks like
```

cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4
```

---

### Post by darius-scerb on 2014-08-24
Thanks, but it didn't fix the problem. Same error when trying to connect.

---

### Post by praseodym on 2014-08-24
> ```
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : [COLOR="#FF0000"]TKIP[/COLOR] CCMP
                        Authentication Suites (1) : PSK
```
As Varun already mentioned: This is not "healthy". Is your router firmware up-to-date? Please show now
```

sudo service network-manager restart
arp -v
route -n
iwconfig
ifconfig -a
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11
iwlist chan
sudo iwlist scan
dmesg | grep iwl 
```

---

### Post by darius-scerb on 2014-08-24
> **praseodym said:**
> As Varun already mentioned: This is not "healthy".


This is no longer the case. Please see the output in [http://ubuntuforums.org/showthread.php?t=2238864&p=13106558#post13106558](http://ubuntuforums.org/showthread.php?t=2238864&p=13106558#post13106558)
My access point info:
```

          Cell 20 - Address: <MAC C-20 TALKTALK-01EAE6>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-01EAE6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000150ba5810d
                    Extra: Last beacon: 200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

> **praseodym said:**
> 
Is your router firmware up-to-date? 

Yes, made sure it is.

> **praseodym said:**
> 
Please show now
```

sudo service network-manager restart
arp -v
route -n
iwconfig
ifconfig -a
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11
iwlist chan
sudo iwlist scan
dmesg | grep iwl 
```
```

darka@bloop:~$ sudo service network-manager restart
[sudo] password for darka: 
network-manager stop/waiting
network-manager start/running, process 3027
darka@bloop:~$ arp -v
Entries: 0    Skipped: 0    Found: 0
darka@bloop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
darka@bloop:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
darka@bloop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:58:14:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25655 (25.6 KB)  TX bytes:25655 (25.6 KB)


wlan0     Link encap:Ethernet  HWaddr 00:26:c7:9a:36:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


darka@bloop:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
darka@bloop:~$ ping -c 2 www.ubuntuusers.de
ping: unknown host www.ubuntuusers.de
darka@bloop:~$ ping -c 2 213.95.41.11
connect: Network is unreachable
darka@bloop:~$ iwlist chan
eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
darka@bloop:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:39:96:AD:5F:7C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-HZWH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a61db276b7
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000B4254487562332D485A5748
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA70050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210002425410230017486F6D652048756220332E30204D756C7469204D6F646510240010425420486F6D652048756220332E3041104200122B3035383732302B4E5133313437333332301054000800060050F204000110110010425420486F6D652048756220332E3041100800020084103C000101
          Cell 02 - Address: 02:39:96:AD:5F:7C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a61db3541f
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201018B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: 22:39:96:AD:5F:7C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a61db35d72
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00084254576966692D58
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201018B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: 7C:4C:A5:90:D7:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SKYD4F06"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000042b6dd00af
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0008534B594434463036
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050100260000
                    IE: Unknown: 2D1AAC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD800050F204104A0001101044000102103B0001031047001079819EA5F05E586F71673E47CBA00A7C1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 6C:19:8F:01:EA:E6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-01EAE6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a8cd6a12e
                    Extra: Last beacon: 188ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D303145414536
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474200010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 06 - Address: CC:33:BB:3E:00:78
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-QPJK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d7fca8824d
                    Extra: Last beacon: 18524ms ago
                    IE: Unknown: 000B4254487562342D51504A4B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706474220010D12
                    IE: Unknown: 200100
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100
                    IE: Unknown: DD2C0050F204104A00011010440001021057000100104700103E38FF94044653BB90C5ADB7901A4D14103C000101
          Cell 07 - Address: 7C:03:4C:94:D3:0D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"SKY4D30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d17247d4
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0008534B593444333043
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A2C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 12:62:2C:63:25:4E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063c0cd345f
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 09 - Address: 00:62:2C:68:FD:A2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-2M6M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bfe21f2f4
                    Extra: Last beacon: 18456ms ago
                    IE: Unknown: 000B4254487562352D324D364D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010ED9E4A9369AC5011B6C510E8B5BC09C2103C000101
          Cell 10 - Address: 4C:17:EB:8C:C4:B6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Tafari"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001cec2ae5186
                    Extra: Last beacon: 18452ms ago
                    IE: Unknown: 0006546166617269
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 02:AC:54:E1:A2:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050e2f1c07a
                    Extra: Last beacon: 18436ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
          Cell 12 - Address: 84:9C:A6:97:99:2D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Carlos Ortiz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c0febf183
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 000C4361726C6F73204F7274697A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 13 - Address: 7C:4C:A5:1F:A2:69
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SKYF6849"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018fb4e7183
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 0008534B594636383439
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: 00:26:5A:0D:75:0B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ozcctv & sat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c4e29b3ebf
                    Extra: Last beacon: 424ms ago
                    IE: Unknown: 000C6F7A63637476202620736174
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545720010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000090127A
                    IE: Unknown: DD1E00904C330E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 15 - Address: 22:81:D8:51:48:5A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000253d34180
                    Extra: Last beacon: 16352ms ago
                    IE: Unknown: 00084254576966692D58
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
          Cell 16 - Address: 00:62:2C:63:25:4E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-HNQ9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063c0cc4ad0
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000B4254487562352D484E5139
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8E0050F204104A000110104400010210570001001041000100103B0001031047001006819EFA4F0D53C8A4FEADE333C7798D10210002425410230005487562203510240009425420487562203541104200122B3036383334332B4E5133343732363034351054000800060050F204000110110010425420486F6D652048756220352E3041100800020084103C000101
          Cell 17 - Address: 4C:8B:EF:EA:EC:50
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-EAEC48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b825cc160
                    Extra: Last beacon: 4724ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D454145433438
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010024
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8804C8BEFEAEC50103C000101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501002E127A
                    IE: Unknown: DD07000C4304000000
          Cell 18 - Address: 00:8A:AE:E1:36:CA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-X2Z5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bff2586a4
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000B4254487562352D58325A35
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8E0050F204104A000110104400010210570001001041000100103B00010310470010183E72B060EC5F4792660AABE8A0C0F310210002425410230005487562203510240009425420487562203541104200122B3036383334332B4E5134313334383339391054000800060050F204000110110010425420486F6D652048756220352E3041100800020084103C000101
          Cell 19 - Address: 32:8A:AE:E1:36:CA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bff265c89
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 20 - Address: 00:AC:54:E1:A2:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-5JF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050e4052180
                    Extra: Last beacon: 336ms ago
                    IE: Unknown: 000B4254487562332D354A4632
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
          Cell 21 - Address: D0:2D:B3:4A:72:84
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-4A727C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000089cd7a6151
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D344137323743
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010046
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880D02DB34A7284103C000101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020091127A
                    IE: Unknown: DD07000C4304000000
          Cell 22 - Address: 7C:4C:A5:84:A9:2D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"SKY8D121"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000328c2701667
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 0008534B593844313231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


darka@bloop:~$ dmesg | grep iwl
[   13.710838] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.710995] iwlwifi 0000:04:00.0: irq 33 for MSI/MSI-X
[   13.870038] iwlwifi 0000:04:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   14.142457] Modules linked in: i915(+) dell_laptop snd_rawmidi joydev dcdbas snd_seq snd_seq_device serio_raw iwlwifi intel_powerclamp coretemp cfg80211 snd_timer drm_kms_helper kvm_intel drm kvm snd soundcore mei_me intel_ips mei video i2c_algo_bit dell_smo8800 wmi lpc_ich mac_hid binfmt_misc parport_pc ppdev lp parport psmouse ahci r8169 libahci mii
[   14.270283] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.270284] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.270285] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.270287] iwlwifi 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   14.270399] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.385057] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.636023] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   21.643295] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   21.680369] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   21.687637] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[  155.833830] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[  155.841161] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3



```

---

### Post by praseodym on 2014-08-24
How many characters does the password have? It should be at least 8, without "strange" characters

---

### Post by darius-scerb on 2014-08-24
It has 8 characters and no strange characters. The password I'm using is correct, as I can connect just fine on windows.

---

### Post by praseodym on 2014-08-24
Can you choose in the BIOS that the network is booted before the respective OS?

---

### Post by darius-scerb on 2014-08-24
Nope, nothing similar is available :/

---

### Post by praseodym on 2014-08-24
Sometimes the firmware is not unloaded correctly after Windows shutdown. Take out the battery for 10 minutes.

---

### Post by varunendra on 2014-08-25
Having lost most of my touch with all the wifi stuff in past few days (and probably also having lost at least half of my mind under the stressful routines), I suspect the problem to be this particular router specific.

Could you ask your ISP to replace it with another one? Just a different model which has no connectivity complains (this one seems to have lots of connectivity complains already on their forums).

---

