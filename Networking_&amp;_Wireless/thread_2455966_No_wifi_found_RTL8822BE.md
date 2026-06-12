---
title: "No wifi found RTL8822BE"
date: 2020-12-31
forum: Networking &amp; Wireless
---

### Post by josilva00 on 2020-12-31
sudo dmesg | grep 8822 returns:
```
[    3.739368] Bluetooth: hci0: RTL: examining hci_ver=07 hci_rev=000b lmp_ver=07 lmp_subver=8822
[    3.740572] Bluetooth: hci0: RTL: loading rtl_bt/rtl8822b_fw.bin
[    3.740912] Bluetooth: hci0: RTL: loading rtl_bt/rtl8822b_config.bin
[    3.744674] r8822be: loading out-of-tree module taints kernel.
[    3.745019] r8822be: module verification failed: signature and/or required key missing - tainting kernel
[    3.822461] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    3.826110] r8822be: rtlwifi: wireless switch is on
[    3.890958] r8822be 0000:07:00.0 wlp7s0: renamed from wlan0
[    4.307781] r8822be: halmac_init_hal failed
[    4.315962] r8822be: halmac_init_hal failed
[    4.316109] r8822be: halmac_init_hal failed
[   15.019809] r8822be: halmac_init_hal failed
[   15.020439] r8822be: halmac_init_hal failed
[   25.024699] r8822be: halmac_init_hal failed
[   25.025319] r8822be: halmac_init_hal failed
[   35.022320] r8822be: halmac_init_hal failed
[   35.022708] r8822be: halmac_init_hal failed
[   45.164547] r8822be: halmac_init_hal failed
[   45.165163] r8822be: halmac_init_hal failed
[   55.203152] r8822be: halmac_init_hal failed
[   55.203301] r8822be: halmac_init_hal failed

```

lsmod | grep 8822 returns:
```
rtw_8822be             16384  0
rtw_8822b             225280  1 rtw_8822be
rtw_pci                24576  1 rtw_8822be
rtw_core              176128  2 rtw_8822b,rtw_pci
r8822be               688128  0
mac80211              966656  3 rtw_core,rtw_pci,r8822be
cfg80211              843776  3 rtw_core,mac80211,r8822be

```

lspci -nnk returns:


```
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822] (rev ff)
    Kernel driver in use: r8822be
    Kernel modules: r8822be, rtw_8822be

```

update:
apparently if i boot the pc disconnected from power wifi works just fine

---

