---
title: "connectivity issues with dlink dwa 131 wifi adapter"
date: 2020-03-31
forum: Networking &amp; Wireless
---

### Post by mukundanks on 2020-03-31
i'm facing problems with dwa 131 wifi adapter.it was working fine until last reboot. i have gone through many threads regarding the same. most often i'm getting error with the commands they have given. i'm new to linux btw. also when i try to update through terminal, it says the given package doesnot have release note and so on.

i'm listing the return values of some commands.

$ lsusb
Bus 001 Device 004: ID 2001:3319 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ dmesg | grep -i rtl
[    1.189142] r8169 0000:01:00.0 eth0: RTL8168d/8111d at 0x        (ptrval), bc:ae:c5:55:37:27, XID 083000c0 IRQ 24
[   13.171263] usbcore: registered new interface driver rtl8192cu
[   14.853439] usb 1-8: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[   14.853618] usb 1-8: RTL8192EU rev B (SMIC) 2T2R, TX queues 3, WiFi=1, BT=0, GPS=0, HI PA=0
[   14.853621] usb 1-8: RTL8192EU MAC: 0c:b6:d2:d0:df:08
[   14.853625] usb 1-8: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[   15.979276] usbcore: registered new interface driver rtl8xxxu
[   16.494875] usbcore: registered new interface driver rtl8192eu
[   16.508418] rtl8xxxu 1-8:1.0 wlx0cb6d2d0df08: renamed from wlan0
[   23.304427] usb 1-8: rtl8xxxu_bss_info_changed: HT supported
[ 7575.422342] usb 1-8: rtl8192eu_active_to_emu: Disabling MAC timed out
[ 7577.377951] usb 1-7: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[ 7577.378086] usb 1-7: RTL8192EU rev B (SMIC) 2T2R, TX queues 3, WiFi=1, BT=0, GPS=0, HI PA=0
[ 7577.378089] usb 1-7: RTL8192EU MAC: 0c:b6:d2:d0:df:08
[ 7577.378091] usb 1-7: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[ 7578.883365] rtl8xxxu 1-7:1.0 wlx0cb6d2d0df08: renamed from wlan0
[ 7583.017079] usb 1-7: rtl8xxxu_bss_info_changed: HT supported


$ rfkill list all 
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2020-03-31
We don't see anything alarming and fixable there. Let's dig deeper. Please post the result of:

```
dmesg | grep wlx
nmcli device wifi list

```

---

### Post by mukundanks on 2020-03-31
dmesg | grep wlx
[   16.508418] rtl8xxxu 1-8:1.0 wlx0cb6d2d0df08: renamed from wlan0
[   21.919606] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[   21.941151] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[   22.064801] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[   23.280154] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[   23.292594] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[   23.294331] wlx0cb6d2d0df08: authenticated
[   23.296230] wlx0cb6d2d0df08: associate with 50:d4:f7:24:8e:34 (try 1/3)
[   23.302715] wlx0cb6d2d0df08: RX AssocResp from 50:d4:f7:24:8e:34 (capab=0x1411 status=0 aid=1)
[   23.306058] wlx0cb6d2d0df08: associated
[   23.620691] IPv6: ADDRCONF(NETDEV_CHANGE): wlx0cb6d2d0df08: link becomes ready
[  244.921568] wlx0cb6d2d0df08: deauthenticating from 50:d4:f7:24:8e:34 by local choice (Reason: 3=DEAUTH_LEAVING)
[  346.302627] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[  346.359996] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[  347.579037] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  347.590715] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  347.794662] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  347.998682] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  348.202683] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  349.487379] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  349.510946] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  349.714696] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  349.918713] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  350.122720] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  351.803400] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  351.827575] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  352.030774] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  352.234770] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  352.438780] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  354.623633] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  354.647949] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  354.850851] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  355.054835] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  355.258852] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  365.443427] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  365.455205] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  365.659121] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  365.863132] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  366.067121] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  373.062859] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[  374.266652] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  374.278459] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  374.479321] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  374.683326] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  374.887338] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  386.080220] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  386.103317] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  386.303616] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  386.507632] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  386.711633] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  399.056489] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[  400.269296] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  400.281097] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  400.483966] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  400.687970] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  400.891978] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  412.077083] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  412.101465] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  412.304250] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  412.508271] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  412.712270] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  425.059044] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[  426.266066] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  426.277849] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  426.480609] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  426.684619] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  426.888620] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  438.073686] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  438.097725] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  438.300893] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  438.504911] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  438.708902] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  451.058264] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[  510.827444] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  510.851868] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  511.054704] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  511.258722] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  511.462717] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  522.647652] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[  522.672362] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[  522.875026] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[  523.079028] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[  523.283004] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[  535.059022] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 7578.883365] rtl8xxxu 1-7:1.0 wlx0cb6d2d0df08: renamed from wlan0
[ 7579.208778] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 7581.752734] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 7581.791968] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 7582.993518] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 7583.005249] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 7583.007001] wlx0cb6d2d0df08: authenticated
[ 7583.011203] wlx0cb6d2d0df08: associate with 50:d4:f7:24:8e:34 (try 1/3)
[ 7583.014972] wlx0cb6d2d0df08: RX AssocResp from 50:d4:f7:24:8e:34 (capab=0x1411 status=0 aid=2)
[ 7583.019092] wlx0cb6d2d0df08: associated
[ 7583.040411] IPv6: ADDRCONF(NETDEV_CHANGE): wlx0cb6d2d0df08: link becomes ready
[ 8492.207172] wlx0cb6d2d0df08: deauthenticating from 50:d4:f7:24:8e:34 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 8495.222044] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 8495.267728] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 8496.472669] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8496.484505] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8496.687831] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8496.891841] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8497.095828] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[ 8498.384492] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8498.408883] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8498.611814] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8498.815822] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8499.019813] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[ 8500.716487] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8500.740145] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8500.943852] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8501.147846] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8501.351821] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[ 8503.536467] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8503.560257] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8503.763821] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8503.967817] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8504.171802] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[ 8514.357752] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8514.369632] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8514.571796] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8514.775800] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8514.979790] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[ 8522.067131] IPv6: ADDRCONF(NETDEV_UP): wlx0cb6d2d0df08: link is not ready
[ 8523.282759] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8523.296119] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8523.499733] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8523.703767] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8523.907769] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out
[ 8535.088416] wlx0cb6d2d0df08: authenticate with 50:d4:f7:24:8e:34
[ 8535.113145] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 1/3)
[ 8535.315702] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 2/3)
[ 8535.519709] wlx0cb6d2d0df08: send auth to 50:d4:f7:24:8e:34 (try 3/3)
[ 8535.723708] wlx0cb6d2d0df08: authentication with 50:d4:f7:24:8e:34 timed out

$ nmcli device wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
        Classified  Infra  5     270 Mbit/s  17      &#9602;___  WPA1 WPA2 


it was working during the first thread(with very low signal reception), now it is not connecting.

---

### Post by CelticWarrior on 2020-03-31
"WPA1 WPA2" is a problem in itself. WPA2 only is what should be. Please check the router settings.

---

### Post by mukundanks on 2020-03-31
i have corrected in router, but still same result

---

### Post by chili555 on 2020-03-31
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

---

### Post by mukundanks on 2020-04-06
reconfigured the router, and did everything as you said.

sudo iw reg get
global
country IN: DFS-UNSET
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5150 - 5350 @ 160), (N/A, 23), (N/A)
    (5725 - 5875 @ 80), (N/A, 23), (N/A)

thanks to you, its working now ! sorry for the late reply

---

