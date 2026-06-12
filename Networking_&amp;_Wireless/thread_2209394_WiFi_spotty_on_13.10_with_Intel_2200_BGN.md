---
title: "WiFi spotty on 13.10 with Intel 2200 BGN"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by ralph-angelus on 2014-03-05
Doesn't connect to certain networks, I've tried the 11n_disable=1 option and bt_coex_active=N neither helps. Here's the dmesg output 

[    2.570093] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.570219] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[    2.607381] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    2.623519] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.623522] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.623524] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.623525] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[    2.623528] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[    2.623639] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    2.665224] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.144423] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    5.152182] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[    5.396344] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    5.404395] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[    5.460807] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    5.461051] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    9.565107] wlan1: authenticate with 00:1a:1e:41:0e:d0
[    9.569918] wlan1: send auth to 00:1a:1e:41:0e:d0 (try 1/3)
[    9.571546] wlan1: authenticated
[    9.571621] wlan1: waiting for beacon from 00:1a:1e:41:0e:d0
[    9.604604] wlan1: associate with 00:1a:1e:41:0e:d0 (try 1/3)
[    9.606911] wlan1: RX AssocResp from 00:1a:1e:41:0e:d0 (capab=0x21 status=17 aid=0)
[    9.606915] wlan1: 00:1a:1e:41:0e:d0 denied association (code=17)
[    9.618512] wlan1: deauthenticating from 00:1a:1e:41:0e:d0 by local choice (reason=3)




[  482.405732] iwlwifi 0000:03:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  482.405796] iwlwifi 0000:03:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  482.405861] iwlwifi 0000:03:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

[ 3931.246534] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 3931.255171] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 3932.636262] iwlwifi 0000:03:00.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 3932.636265] iwlwifi 0000:03:00.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP



Any ideas? Let me know if you need any other logs

---

### Post by varunendra on 2014-03-06
Welcome to the fourms ralph-angelus!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Preferably run it when such networks are around to which you can not connect despite saving the password and encryption type correctly in Network Manager.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

