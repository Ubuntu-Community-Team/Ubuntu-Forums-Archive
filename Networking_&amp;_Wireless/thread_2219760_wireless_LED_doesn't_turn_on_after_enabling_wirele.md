---
title: "wireless LED doesn't turn on after enabling wireless on HP nx9420"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by rpremuz on 2014-04-25
Hello!

On a **HP Compaq nx9420** laptop with **Ubuntu 14.04 32-bit** installed I have an issue with LED indicator on the wireless on/off button.

uname -a says:
Linux pc 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

lspci shows:
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

By pressing the button I can successfully enable/disable the wireless adapter.
Also when the adapter is enabled the LED indicator blinks on data transfer. :(

As suggested on the forum I added the led_mode option to **/etc/modprobe.d/iwlegacy.conf** in order to stop the LED blinking:
```
options iwlegacy led_mode=1
```
[B]After reboot the wireless adapter is enabled and the LED is on.
When I disable wireless the LED turns off. But if I switch wireless back on the LED stays off.[/B]

Is this a bug or am I doing something wrong?

Here are more info:

```
$ dmesg | grep iwl
[   24.049447] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   24.049452] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   24.049515] iwl3945 0000:10:00.0: can't disable ASPM; OS doesn't have ASPM control
[   24.105764] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   24.105770] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   24.105845] iwl3945 0000:10:00.0: irq 46 for MSI/MSI-X
[   24.121726] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   29.649467] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9

$ modinfo iwlegacy 
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

$ modinfo iwl3945
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     C93C31FCEBBAE1F376E495F
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

```

---

### Post by rpremuz on 2014-06-12
Anyone?

---

### Post by jeremy31 on 2014-06-12
Try ```
cat /sys/module/iwlegacy/parameters/led_mode
``` and see if it returns 1 after turning the switch on and off

---

### Post by rpremuz on 2014-06-13
Jeremy, **/sys/module/iwlegacy/parameters/led_mode** does contain **1** after turning the switch on and off.

---

