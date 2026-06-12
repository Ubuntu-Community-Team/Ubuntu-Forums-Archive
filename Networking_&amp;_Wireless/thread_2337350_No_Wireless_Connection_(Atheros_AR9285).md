---
title: "No Wireless Connection (Atheros AR9285)"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by cces4415 on 2016-09-16
Hi everyone, this is my first post on this forum,
just created this account a few minutes ago for this annoying issue
First of all I'm a total newbie in Ubuntu
I've just installed unbuntu MATE 16.04.1 LTS (Xenial Xerus) and deleted WIN 7 on my Genuine HanBody HRP1041D (quite an old notebook, about 5 years) yesterday
It took me whole afternoon and night running through a bunch of fails and errors but still succeeded at the end, magically. 
but then the worst thing ever happened
NO WIFI!!
It seems that Ubuntu is unable to detect my wireless card Atheros AR9285, which looks like a common problem
I've tried a couple of solutions provided by my friends and the Internet, and thanks to the computer they don't work at all.
1. create /etc/modprobe.d/wmi.conf  with content "blacklist toshiba_wmi" then reboot--> FAILED
2. [https://ubuntuforums.org/showthread.php?t=1286503](https://ubuntuforums.org/showthread.php?t=1286503) using ver 4.4.2 instead --> FAILED (Appendix II)
3. sudo rfkill unblock all --> FAILED
Could any one come up with a solution? Thanks a million :)

[SIZE=7]Appendix I[/SIZE]
rfkill list
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

lspci -k -s 0000:03:00.0
```

03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: XAVi Technologies Corp. WB214E 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD]
    Kernel driver in use: ath9k
    Kernel modules: ath9k


```

[SIZE=7]Appendix II[/SIZE]
When I typed "make" the ouput
```
Generating local configuration database from kernel ...make[2]: gcc: Command not found
 done.
/--------------
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|     make oldconfig
|     make menuconfig
|
| To get defaults for certain drivers:
|     make defconfig-alx
|     make defconfig-ar5523
|     make defconfig-ath10k
|     make defconfig-ath5k
|     make defconfig-ath6kl
|     make defconfig-ath9k
|     make defconfig-ath9k-debug
|     make defconfig-b43
|     make defconfig-b43legacy
|     make defconfig-brcmfmac
|     make defconfig-brcmsmac
|     make defconfig-carl9170
|     make defconfig-cw1200
|     make defconfig-hwsim
|     make defconfig-ieee802154
|     make defconfig-igb
|     make defconfig-iwlwifi
|     make defconfig-media
|     make defconfig-nfc
|     make defconfig-rtlwifi
|     make defconfig-wcn36xx
|     make defconfig-wifi
|     make defconfig-wil6210
|     make defconfig-wwan
\--
Makefile.real:45: recipe for target '.config' failed
make[2]: *** [.config] Error 1
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2

```
Well maybe it's due to the wrong version of ubuntu....I'm not sure

---

### Post by wildmanne39 on 2016-09-16
First your driver is already loaded, but your wifi is turned off usually means by the physical switch.

Please look for a button or switch to turn it on, it could be a key combination like fn+f5 for example but n the older laptop it is probably a button or switch. You do not need to install a driver like I said it is already loaded, will tell you that your device does not work very well in ubuntu, but there war parameters we can try after your wifi is turned on, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by cces4415 on 2016-09-17
Thanks a lot, it does appear that the physical switch (Fn + F2) isn't turned on. 
Quite a stupid mistake, though still learned something :D
thanks again~

---

### Post by wildmanne39 on 2016-09-17
Your welcome!
Enjoy!

---

