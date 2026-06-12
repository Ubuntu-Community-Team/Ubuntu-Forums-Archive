---
title: "ipw2200 can't get in monitor mode on fresh 7.10 install"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by BuiZe on 2007-10-19
Every year I upgrade my laptop to the latest Ubuntu version and follow the same procedure to use Kismet with my 2200BG wifi adaptor, but this time, I'm a bit stuck. I followed all INSTALL and README docs as usual, the new driver versions seem to be loaded, but monitor mode is still not available.
Could someone point out what I'm doing wrong this time? (Is the firmware in the wrong place?)


Downloaded archives:
- ieee80211-1.2.18
- ipw2200-1.2.2
- ipw2200-fw-3.0
(+ installed linux headers)

1) I ran the remove-old scripts to remove any ieee80211* and ipw2200* files (+manual check)

2) Installed ieee80211-1.2.18:
```
sudo make
sudo make install

/lib/modules/2.6.22-14-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.22-14-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.22-14-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.22-14-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.22-14-generic/net/ieee80211/ieee80211.ko

/lib/modules/2.6.22-14-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.22-14-generic/include/net/ieee80211.h
/lib/modules/2.6.22-14-generic/include/net/ieee80211_radiotap.h
```

3) Installed ipw2200
```
sudo make
sudo make install

 /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ipw2200.ko
```

4) Put the firmware in place:
```
/lib/firmware/2.6.22-14-generic/ipw2200-bss.fw
/lib/firmware/2.6.22-14-generic/ipw2200-ibss.fw
/lib/firmware/2.6.22-14-generic/ipw2200-sniffer.fw
```

5) dmesg output:
```
[   15.840000] ieee80211_crypt: registered algorithm 'NULL'
[   15.892000] ieee80211: 802.11 data/management/control stack, 1.2.18
[   15.892000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

[   16.060000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
[   16.060000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.144000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.404000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
```

modinfo:
```
modinfo ieee80211
filename:       /lib/modules/2.6.22-14-generic/net/ieee80211/ieee80211.ko
license:        GPL
author:         Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
version:        1.2.18
srcversion:     AB99453653BD7F777060A64
depends:        ieee80211_crypt
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           debug:debug output mask (int)

modinfo ipw2200 
filename:       /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ipw2200.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     290D33C3FA58931CBA60C75
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
...
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
depends:        ieee80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default on) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 0 off)
 (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           mode:network mode (0=BSS,1=IBSS) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)
```

sudo iwconfig eth1 mode monitor
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
```

kismet
```
kismet
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to buize (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
Source 0 (ipw2200): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
```

---

### Post by Sweevo on 2007-10-19
This post: [http://ubuntuforums.org/showpost.php?p=396906&postcount=9]("http://ubuntuforums.org/showpost.php?p=396906&postcount=9") sorted the problem out for me.

Hope it helps you...

Sweevo

---

### Post by BuiZe on 2007-10-20
Thanks for your fast reply, and indeed, it works like a charm now!

---

