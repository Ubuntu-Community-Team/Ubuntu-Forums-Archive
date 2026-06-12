---
title: "Ubuntu 12.04 problem connecting to wireless or wired connection - HP Elitebook 8570w"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by alan.mcnally on 2013-12-04
HI

I know there are a few posts on this topic however the cure seems rather hardware specific. I ran the following:

dmesg | grep iwl
[   10.415943] iwlwifi 0000:25:00.0: irq 49 for MSI/MSI-X
[   10.451529] iwlwifi 0000:25:00.0: loaded firmware version 9.221.4.1 build 25532
[   10.824330] iwlwifi 0000:25:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.824333] iwlwifi 0000:25:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.824335] iwlwifi 0000:25:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.824336] iwlwifi 0000:25:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.824337] iwlwifi 0000:25:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.824339] iwlwifi 0000:25:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   10.824409] iwlwifi 0000:25:00.0: L1 Disabled; Enabling L0S
[   10.831315] iwlwifi 0000:25:00.0: RF_KILL bit toggled to enable radio.
[   10.876684] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.988810] iwlwifi 0000:25:00.0: L1 Disabled; Enabling L0S
[   16.996137] iwlwifi 0000:25:00.0: Radio type=0x0-0x3-0x1
[   17.360594] iwlwifi 0000:25:00.0: L1 Disabled; Enabling L0S
[   17.367497] iwlwifi 0000:25:00.0: Radio type=0x0-0x3-0x1
zong@zong-HP-EliteBook-8570w:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no



Any help would be greatly appreciated

Alan

---

### Post by varunendra on 2013-12-07
Welcome to the forums Alan !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

