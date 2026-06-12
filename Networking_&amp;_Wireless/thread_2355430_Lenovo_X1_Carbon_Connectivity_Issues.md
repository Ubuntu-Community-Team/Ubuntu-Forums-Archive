---
title: "Lenovo X1 Carbon Connectivity Issues"
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by infiniteshadow on 2017-03-12
Hi Everyone, I recently purchased a generation 1 Lenovo X1 carbon and installed ubuntu.

The wifi will work for maybe 5-10 minutes before becoming very unreliable.

Im not sure what to do, but here is my output after doing `dmesg | grep iwl`

```
[    4.677787] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.695927] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.741370] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    4.741372] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    4.741374] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    4.741376] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205S AGN, REV=0xB0
[    4.743849] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.777737] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.026030] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    5.247642] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.248236] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.248323] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.529892] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.536515] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.536600] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  849.983965] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  849.990679] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  849.990780] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  850.271892] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  850.278599] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  850.278698] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  865.586969] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  865.593685] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  865.593785] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  865.876200] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  865.882959] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  865.883059] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
```

Here is the output from bapoumba's script: [http://paste.ubuntu.com/24170485/](http://paste.ubuntu.com/24170485/)

---

