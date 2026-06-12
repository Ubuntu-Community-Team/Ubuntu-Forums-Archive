---
title: "Unsupported wireless device RTL8822BE on Ubuntu 14"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by chegan2 on 2018-01-15
Sorry&#65292;my english is poor&#12290;Thank you for help&#65281;&#65281;&#65281;
&#65288;1&#65289; problem&#65306;
    Unsupported wireless device RTL8822BE on Ubuntu 14
&#65288;2&#65289;Experimental environment&#65306;
   1 kernel&#65306;4.4.0-104-generic
   2 wireless&#65306; RTL8822BE
&#65288;3&#65289;what i do&#65306;
  1 sudo apt update
  2 sudo apt install git &#12289;
  3 git clone [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next)
  4 cd rtlwifi-next 
  5 make    //----&#12299;go wrong&#65292;as the follow&#65306;


ezio@stealth:~/rtlwifi-next$ make
make -C /lib/modules/4.4.0-104-generic/build M=/home/ezio/rtlwifi-next modules
make[1]: Entering directory `/usr/src/linux-headers-4.4.0-104-generic'
  CC [M]  /home/ezio/rtlwifi-next/base.o
In file included from /home/ezio/rtlwifi-next/base.c:26:0:
/home/ezio/rtlwifi-next/wifi.h:1434:40: error: ‘NUM_NL80211_BANDS’ undeclared here (not in a function)
  struct ieee80211_supported_band bands[NUM_NL80211_BANDS];
                                        ^
/home/ezio/rtlwifi-next/base.c: In function ‘rtlwifi_rate_mapping’:
/home/ezio/rtlwifi-next/base.c:1056:25:  warning: comparison between ‘enum nl80211_band’ and ‘enum  ieee80211_band’ [-Wenum-compare]
   if (NL80211_BAND_2GHZ == hw->conf.chandef.chan->band) {
                         ^
make[2]: *** [/home/ezio/rtlwifi-next/base.o] Error 1
make[1]: *** [_module_/home/ezio/rtlwifi-next] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.4.0-104-generic'
make: *** [all] Error 2

---

### Post by chili555 on 2018-01-15
Please check post #21 here: [https://ubuntuforums.org/showthread.php?t=2364383&p=13715520#post13715520](https://ubuntuforums.org/showthread.php?t=2364383&p=13715520#post13715520)

If you need specific step-by-step instructions, post back and I'll try to help.

---

### Post by chegan2 on 2018-01-16
> **chili555 said:**
> Please check post #21 here: [https://ubuntuforums.org/showthread.php?t=2364383&p=13715520#post13715520](https://ubuntuforums.org/showthread.php?t=2364383&p=13715520#post13715520)

If you need specific step-by-step instructions, post back and I'll try to help.

thank you very much !!!!!!!!    i have do amost one week for this.       ^ V ^

---

### Post by chili555 on 2018-01-16
Your response is a bit unclear. In case it should be interpreted as a request for explicit instructions, I will proceed.

Please get a temporary working internet connection by ethernet, tethered or whatever means possible, open a terminal and do:

```
sudo apt-get update
sudo apt-get install build-essential git
git clone https://github.com/rtlwifi-linux/rtlwifi-next
cd rtlwifi-next
nano wifi.h
```

We will make a change in the source code. Find these lines:

```
#ifndef __RTL_WIFI_H__
#define __RTL_WIFI_H__
#define pr_fmt(fmt) KBUILD_MODNAME ": " fmt
```

Add a new line so that the section now reads:

```
#ifndef __RTL_WIFI_H__
#define __RTL_WIFI_H__
#define IEEE80211_NUM_BANDS NUM_NL80211_BANDS
#define pr_fmt(fmt) KBUILD_MODNAME ": " fmt
```

Save the changes (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor. Now we need to change another file:

```
nano base.c
```

Find this section:

```
*****************************************************************************/
#include "wifi.h"
#include "rc.h"
#include "base.h"
```

Add a new line so that it now reads:

```
*****************************************************************************/
#define IEEE80211_NUM_BANDS NUM_NL80211_BANDS
#include "wifi.h"
#include "rc.h"
#include "base.h"
```
Save the changes (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor. Now back to the terminal:

```
make
sudo make install
sudo modprobe rtl8822be
```

Does your wireless spring to life?

---

### Post by chegan2 on 2018-03-24
i am sorry .The [COLOR=#000000]wireless device go wrong again when modprobe. it work good before today . log:
[/COLOR]sudo modprobe rtl8822be
ezio@stealth:~/rtlwifi-next$ sudo modprobe rtl8822be
modprobe: ERROR: could not insert 'rtl8822be': Required key not available

but make is ok . log:

 make

 Building modules, stage 2.
  MODPOST 18 modules
  LD [M]  /home/ezio/rtlwifi-next/btcoexist/btcoexist.ko
  LD [M]  /home/ezio/rtlwifi-next/halmac/halmac.ko
  LD [M]  /home/ezio/rtlwifi-next/phydm/phydm_mod.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8188ee/rtl8188ee.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8192c/rtl8192c-common.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8192ce/rtl8192ce.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8192cu/rtl8192cu.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8192de/rtl8192de.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8192ee/rtl8192ee.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8192se/rtl8192se.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8723ae/rtl8723ae.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8723be/rtl8723be.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8723com/rtl8723-common.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8821ae/rtl8821ae.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl8822be/rtl8822be.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl_pci.ko
  LD [M]  /home/ezio/rtlwifi-next/rtl_usb.ko
  LD [M]  /home/ezio/rtlwifi-next/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-4.4.0-112-generic'

thank you !!!!!!

[COLOR=#000000]
[/COLOR]

---

### Post by chili555 on 2018-03-24
> modprobe: ERROR: could not insert 'rtl8822be': Required key not availablePlease check here: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)> The easiest way to fix this issue is to disable Secure Boot in UEFI (BIOS) settings.



---

### Post by chegan2 on 2018-03-25
> **chili555 said:**
> Please check here: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

thank you&#65281;&#65281;&#65281;&#65281;

---

