---
title: "WIFI weak signal on HP laptop after updating ubuntu 18"
date: 2018-08-31
forum: Networking &amp; Wireless
---

### Post by kanothsiraj on 2018-08-31
i am trying to do make file again and its saying error!



```
~/File/WIFI/rtlwifi_new-rock.new_btcoex$ make
make -C /lib/modules/4.15.0-33-generic/build M=/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-33-generic'
  CC [M]  /home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex/base.o
/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex/base.c: In function &#8216;_rtl_init_deferred_work&#8217;:
/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex/base.c:602:2: error: implicit declaration of function &#8216;setup_timer&#8217;; did you mean &#8216;sk_stop_timer&#8217;? [-Werror=implicit-function-declaration]
  setup_timer(&rtlpriv->works.watchdog_timer,
  ^~~~~~~~~~~
  sk_stop_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex/base.o' failed
make[2]: *** [/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex/base.o] Error 1
Makefile:1552: recipe for target '_module_/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex' failed
make[1]: *** [_module_/home/siraj/File/WIFI/rtlwifi_new-rock.new_btcoex] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-33-generic'
Makefile:57: recipe for target 'all' failed
make: *** [all] Error 2
```

---

### Post by jeremy31 on 2018-08-31
That branch isn't any good any more
```
cd
rm -rf ~/File/WIFI/rtlwifi_new-rock.new_btcoex
git clone https://github/com/lwfinger/rtlwifi_new
cd rtlwifi_new
make
sudo make install
```

---

### Post by kanothsiraj on 2018-08-31
@[COLOR=#C61919]jeremy31

[/COLOR][SIZE=4][FONT=arial]Thanks for the reply.. but still  the wifi signal is too weak ( today i have updated ubuntu18.4.1)[/FONT][/SIZE][COLOR=#C61919]
[/COLOR]sudo modprobe -v rtl8723be ant_sel=2
[sudo] password for siraj: 
siraj@siraj-HP-Notebook:~$ echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
options rtl8723be ant_sel=2


[COLOR=#C61919]
[/COLOR][COLOR=#C61919]


[/COLOR]

---

### Post by jeremy31 on 2018-08-31
What is the result for ```
modinfo rtl8723be; grep [[:alnum:]] /etc/modprobe.d/* | grep rtl8723be
```

---

### Post by kanothsiraj on 2018-09-01
> **jeremy31 said:**
> What is the result for ```
modinfo rtl8723be; grep [[:alnum:]] /etc/modprobe.d/* | grep rtl8723be
```



:~$ modinfo rtl8723be; grep [[:alnum:]] /etc/modprobe.d/* | grep rtl8723be
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     1B45BB96576F0C4D6674527
alias:          pci:v000010ECd0000B723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8723be
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)
/etc/modprobe.d/50-rtl8723be.conf:options rtl8723be ant_sel=2
/etc/modprobe.d/rtl8723be.conf:options rtl8723be ant_sel=1

---

### Post by jeremy31 on 2018-09-01
```
sudo rm /etc/modprobe.d/rtl8723be.conf
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be
```
Any difference?

---

### Post by kanothsiraj on 2018-09-03
Yeah,

It works.. Thanks Lot :)

---

### Post by kanothsiraj on 2018-09-25
[COLOR=#000000]how to fix it permanently .. It happened again.. again done the same step.. Please i have two laptop[/COLOR]


[COLOR=#000000]bagmo@bagmo-HP-Notebook:~$ sudo modprobe -r rtl8723be[/COLOR]
[COLOR=#000000]bagmo@bagmo-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=1[/COLOR]
[COLOR=#000000]bagmo@bagmo-HP-Notebook:~$ iwlist scan | egrep -i 'ssid|quality'[/COLOR]
[COLOR=#000000]lo Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]enp1s0 Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]virbr0 Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]virbr0-nic Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]Quality=46/70 Signal level=-64 dBm [/COLOR]
[COLOR=#000000]ESSID:"BAGMO"[/COLOR]
[COLOR=#000000]Quality=32/70 Signal level=-78 dBm [/COLOR]
[COLOR=#000000]ESSID:"ESP_82845A"[/COLOR]
[COLOR=#000000]Quality=24/70 Signal level=-86 dBm [/COLOR]
[COLOR=#000000]ESSID:"NETGEAR20"[/COLOR]
[COLOR=#000000]bagmo@bagmo-HP-Notebook:~$ sudo modprobe -r rtl8723be[/COLOR]
[COLOR=#000000]bagmo@bagmo-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=2[/COLOR]
[COLOR=#000000]bagmo@bagmo-HP-Notebook:~$ iwlist scan | egrep -i 'ssid|quality'[/COLOR]
[COLOR=#000000]lo Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]enp1s0 Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]virbr0 Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]virbr0-nic Interface doesn't support scanning.[/COLOR]


[COLOR=#000000]Quality=46/70 Signal level=-64 dBm [/COLOR]
[COLOR=#000000]ESSID:"BAGMO"[/COLOR]
[COLOR=#000000]Quality=26/70 Signal level=-84 dBm [/COLOR]
[COLOR=#000000]ESSID:"ESP_82845A"[/COLOR]
[COLOR=#000000]Quality=24/70 Signal level=-86 dBm [/COLOR]
[COLOR=#000000]ESSID:"NETGEAR20"[/COLOR]




[COLOR=#000000]Sitting near by BAGMO router to post this thread[/COLOR]
[COLOR=#000000]-----------------------------------------------------[/COLOR]

[COLOR=#000000]$ modinfo rtl8723be; grep [[:alnum:]] /etc/modprobe.d/* | grep rtl8723be[/COLOR]
[COLOR=#000000]filename: /lib/modules/4.15.0-34-generic/updates/dkms/rtl8723be.ko[/COLOR]
[COLOR=#000000]firmware: rtlwifi/rtl8723befw_36.bin[/COLOR]
[COLOR=#000000]firmware: rtlwifi/rtl8723befw.bin[/COLOR]
[COLOR=#000000]description: Realtek 8723BE 802.11n PCI wireless[/COLOR]
[COLOR=#000000]license: GPL[/COLOR]
[COLOR=#000000]author: Realtek WlanFAE <wlanfae@realtek.com>[/COLOR]
[COLOR=#000000]author: PageHe <page_he@realsil.com.cn>[/COLOR]
[COLOR=#000000]srcversion: 41E3D27D506CBEDC478A504[/COLOR]
[COLOR=#000000]alias: pci:v000010ECd0000B723sv*sd*bc*sc*i*[/COLOR]
[COLOR=#000000]depends: rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211[/COLOR]
[COLOR=#000000]retpoline: Y[/COLOR]
[COLOR=#000000]name: rtl8723be[/COLOR]
[COLOR=#000000]vermagic: 4.15.0-34-generic SMP mod_unload [/COLOR]
[COLOR=#000000]parm: swenc:Set to 1 for software crypto (default 0)[/COLOR]
[COLOR=#000000](bool)[/COLOR]
[COLOR=#000000]parm: ips:Set to 0 to not use link power save (default 1)[/COLOR]
[COLOR=#000000](bool)[/COLOR]
[COLOR=#000000]parm: swlps:Set to 1 to use SW control power save (default 0)[/COLOR]
[COLOR=#000000](bool)[/COLOR]
[COLOR=#000000]parm: fwlps:Set to 1 to use FW control power save (default 1)[/COLOR]
[COLOR=#000000](bool)[/COLOR]
[COLOR=#000000]parm: msi:Set to 1 to use MSI interrupts mode (default 0)[/COLOR]
[COLOR=#000000](bool)[/COLOR]
[COLOR=#000000]parm: aspm:Set to 1 to enable ASPM (default 1)[/COLOR]
[COLOR=#000000](int)[/COLOR]
[COLOR=#000000]parm: debug_level:Set debug level (0-5) (default 0) (int)[/COLOR]
[COLOR=#000000]parm: debug_mask:Set debug mask (default 0) (ullong)[/COLOR]
[COLOR=#000000]parm: disable_watchdog:Set to 1 to disable the watchdog (default 0)[/COLOR]
[COLOR=#000000](bool)[/COLOR]
[COLOR=#000000]parm: ant_sel:Set to 1 or 2 to force antenna number (default 0)[/COLOR]
[COLOR=#000000](int)[/COLOR]
[COLOR=#000000]/etc/modprobe.d/50-rtl8723be.conf[/COLOR]:eek:[COLOR=#000000]ptions rtl8723be ant_sel=2[/COLOR]
[COLOR=#000000]/etc/modprobe.d/rtl8723-ant-sel.conf[/COLOR]:eek:[COLOR=#000000]ptions rtl8723be ant_sel=2[/COLOR]

---

### Post by jeremy31 on 2018-09-25
```
sudo apt-get install dkms git build-essential
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot, check BIOS to make sure Secure Boot is disabled and the problem should be fixed

---

