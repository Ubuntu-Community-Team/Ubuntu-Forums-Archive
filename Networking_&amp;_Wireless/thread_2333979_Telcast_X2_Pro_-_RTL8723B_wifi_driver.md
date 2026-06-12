---
title: "Telcast X2 Pro - RTL8723B wifi driver"
date: 2016-08-15
forum: Networking &amp; Wireless
---

### Post by makem2 on 2016-08-15
I searched everywhere but to date cannot find a wifi driver for my favourite xubuntu.

I am relatively new to linux so am wary of attempting to build a driver from sources I have come across.

Can anyone tell me if there is a 'made' driver available now, maybe RTL8723e which apparently included the 'b'

The Realtec web site does not have one. It seems this has been a problem wifi card since 2013.

---

### Post by chili555 on 2016-08-15
Let's start by identifying your exact device. Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```

---

### Post by makem2 on 2016-08-16
> **chili555 said:**
> Let's start by identifying your exact device. Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```

```

makem@makem-tPAD:~$ lspci -nnk | grep 0280 -A2
makem@makem-tPAD:~$ 

```

Nothing returned.

```

makem@makem-tPAD:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
    Subsystem: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604]
    Kernel driver in use: bdw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:161e] (rev 09)
    DeviceName:  Onboard IGD
    Subsystem: Intel Corporation Broadwell-U Integrated Graphics [8086:161e]
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: Intel Corporation Broadwell-U Audio Controller [8086:160c]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Broadwell-U Camarillo Device [8086:1603] (rev 09)
    Subsystem: Intel Corporation Broadwell-U Processor Thermal Subsystem [8086:1603]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
    Subsystem: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
    Subsystem: Intel Corporation Wildcat Point-LP MEI Controller [8086:9cba]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. Wildcat Point-LP High Definition Audio Controller [10ec:1082]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc7] (rev 03)
    Subsystem: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc7]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83] (rev 03)
    Subsystem: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
    Subsystem: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2]
    Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation Wildcat Point-LP Thermal Management Controller [8086:9ca4] (rev 03)
    Subsystem: Intel Corporation Wildcat Point-LP Thermal Management Controller [8086:9ca4]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
makem@makem-tPAD:~$ 

```

If it helps: I am currently using a wifi dongle to access this web page.

---

### Post by chili555 on 2016-08-16
Let's also have a look at:```
lsusb
dmesg | grep -i rtl
dmesg | grep -i sdio
```So far, we see no wireless device.

---

### Post by makem2 on 2016-08-17
> **chili555 said:**
> Let's also have a look at:```
lsusb
dmesg | grep -i rtl
dmesg | grep -i sdio
```So far, we see no wireless device.

```

makem@makem-tPAD:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 258a:6a88  
Bus 001 Device 007: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 17ef:6039 Lenovo 
Bus 001 Device 010: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
makem@makem-tPAD:~$ dmesg | grep -i rtl
[   12.629283] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   12.629288] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
makem@makem-tPAD:~$ dmesg | grep -i sdio
makem@makem-tPAD:~$

```

The Rlink is the wifi dongle I use when using xubuntu. The machine connects fine in windows 10 with its internal wireless so must have one.

---

### Post by chili555 on 2016-08-17
We haven't been able to see it yet. Please boot into Windows and get all the details you can about it and post them here. Every detail, number, code, etc. will be useful.

---

### Post by makem2 on 2016-08-17
Location Information:0000.0014.0000.003.000.000.000.000.000
Driver Ver: 1027.4.1120.2014
Driver date: 2015:2:17
inf file: netrtwlanu.inf
Desc: Realtek RTL8723B Wireless LAN 802.11n USB 2.0 Network Adaptor
Driver Provider: Realtek Semiconductor Corp.
INF Section: RTL8723bu.ndi.NT
Hardware ID: USB\VID_0BDA&PID_B720&REV_0200&MI_02
Hardware Address: 58-63-56-10-30-DF

---

### Post by chili555 on 2016-08-17
***Chili gives himself a stern facepalm. Chili wipes a few layers of grime off of his thick spectacles and sees*....**> makem@makem-tPAD:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 258a:6a88  
Bus 001 Device 007: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
[COLOR="#FF0000"]Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. [/COLOR]
Bus 001 Device 003: ID 17ef:6039 Lenovo 
Bus 001 Device 010: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubAlrighty then! Let's build a driver! Using your USB dongle temporarily, please open a terminal and do:

```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8723bu.git
cd rtl8723bu
make
sudo make install
```Detach the USB dongle, reboot and let me have your report. I will probably have one more step.

NOTE TO SEARCHERS: You MUST observe the correction at post #52. Also see the additional step at post #57. YOU HAVE BEEN WARNED.

---

### Post by makem2 on 2016-08-17
Thank you so much!

The driver worked and connected immediately to my router.

One question remains, is it possible to save the driver for future install shoul this prove necessary? Or, must I follow your instructions which I have saved, again?

---

### Post by chili555 on 2016-08-18
Well, that's a perfect lead-in to the second step. You have built the driver for your current kernel version only. When Update Manager installs a later kernel version, known as linux-image, recompile:

```
cd rtl8723bu
make clean
make
sudo make install
```
Reboot.

Please retain the file and these instructions for that time. If you wish, you can copy the rtl8723bu folder to a USB drive, CD or similar for future use. On a CD, the folder and contents will be read-only. Accordingly, if you need them in the future, I recommend that you drag and drop them to the desktop before recompiling.```
cd ~/Desktop/rtl8723bu
make clean
make
sudo make install
```

---

### Post by makem2 on 2016-08-18
Great, you have answered all for me.

Thank you for your time and knowledge sharing.

---

### Post by makem2 on 2016-08-18
Thank you for your time and knowledge sharing, it is much appreciated.

---

### Post by makem2 on 2017-07-01
Not far from a year to the date this help worked and after a recent update, now, even after a recompile, does not work.

Two things are different from the previous time:

1. A new SSD drive is in use and has been for some while.

2. A Bluetooth keyboard has been paired with the computer.

The keyboard was purchased whilst abroad and was being used with Windows 10 until I returned. On return I updated the Xubuntu system and paired the keyboard. It was then I noticed the wifi no longer worked.

I had 'miss-laid' the original driver file I had kept from the previous make and started again from the beginning. This time without success.

Could it be down to the BT pairing?

---

### Post by chili555 on 2017-07-01
'Without success' meaning that the file no longer compiles or it compiles but the wireless still doesn't work or the wireless works but the BT keyboard does not or ... what?

---

### Post by makem2 on 2017-07-01
> **chili555 said:**
> 'Without success' meaning that the file no longer compiles or it compiles but the wireless still doesn't work or the wireless works but the BT keyboard does not or ... what?

Wow, thank you for such a quick response.

The wireless connection did not work after the compile appeared to work.

However, after redoing all again the wifi worked. Also the BT worked too. I rebooted once again and this time the wifi did not connect but BT is working.

EDIT: I recompiled once again and once again the wifi connected but after a reboot it no longer connected. So, instead of rebooting, I shut down and restarted. The wifi then connected.

After a further test I am certain that the wifi connects only after first shutting down the machine. Rebooting does not work.

---

### Post by chili555 on 2017-07-01
Let's try a kwik-n-durty trick. Let's make sure that the module loads without fail on every boot:```
sudo -i
echo 8723bu  >>  /etc/modules
exit
```Any improvement? If not, we'll dig a little deeper.

---

### Post by makem2 on 2017-07-01
I tried that and the 'connected' icon appeared but no internet. The computer appeared very slow in opening a web page. I rebooted and this time had internet connection and was able to browse a web page normally. However, for some reason I was unable to access this forum thread again. (I m using a different computer at the moment)

Edit: Back on the problem machine now after access the forum from the beginning rather than from the thread url. Appears to have been browser related problem.

Please explain why those commands worked.

---

### Post by makem2 on 2017-07-01
Things are not right. Internet connection is not reliable. The 'connected' icon appears but no internet following reboots or shut downs and restarts. After disconnecting the wifi the icon still shows as if there is some connection.

I am using a spare machine again to edit this thread.

EDIT: I have just noticed that under the list of available wifi sources there are now two identical lists both include the one I am attempting to connect to.

EDIT2: Having disconnected both connections and reconnected just one, I now have an internet connection. I will reboot. There a duplicate sources and no internet until both are disconnected and one reconnected.

---

### Post by makem2 on 2017-07-02
Unable to find a solution to two connections to the same network and dropping out of any connection.

---

### Post by chili555 on 2017-07-02
You might consider removing *all *previous connections and starting fresh:```
sudo rm /etc/NetworkManager/system-connections/*
sudo service network-manager restart
```Caution: this will remove all stored wifi passwords. Proceed with care.

---

### Post by makem2 on 2017-07-02
Unable to find a solution to two connections to the same network and dropping out of any connection.

EDIT: Posted after your previous reply which was not seen.

---

### Post by makem2 on 2017-07-02
> **chili555 said:**
> You might consider removing *all *previous connections and starting fresh:```
sudo rm /etc/NetworkManager/system-connections/*
sudo service network-manager restart
```Caution: this will remove all stored wifi passwords. Proceed with care.

Thank you for bearing with me.

I did as you suggest but still have duplicate entries in the drop down list from the connection icon.

Each list is headed 'Wi-Fi Networks (Realtek 802.11n WLAN Adaptor)'

Each list contains 'makem2.4', the network I use, along with several others which are available. I can connect to 'makem2.4 in the top list and connect to the internet.

However, the list keeps flashing as if it is trying to find other available places and the mouse movement is slowed.

I am using the spare machine for this message as having typed it on the offending machine I was unable to reconnect to this site but could access others.

---

### Post by chili555 on 2017-07-02
Ah, haaaa! I think I see it now! > The Rlink is the wifi dongle I use when using xubuntu. Please detach the USB dongle and reboot. Let us hear your report.

---

### Post by makem2 on 2017-07-02
> **chili555 said:**
> Ah, haaaa! I think I see it now! Please detach the USB dongle and reboot. Let us hear your report.

I am afraid the Rlink dongle was in use whilst I was in China! It was left there!

I purchased another in the uk when I found I had 'miss-laid' the folder you told me to save. I used that dongle to get a wifi service running and since that time it has not been connected to the machine. It has not been connected since post #18.

Could the '[COLOR=#000000]kwik-n-durty trick' be causing another module to be loaded?

EDIT: The dongle I used initially in the UK was a TP-Link AC450 USB WiFi adaptor[/COLOR]

---

### Post by makem2 on 2017-07-02
```

makem@teclst:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 258a:6a88  
Bus 001 Device 006: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
makem@teclst:~$ dmesg | grep -i rtl
[    2.064327] RTL871X: module init start
[    2.064329] RTL871X: rtl8723bu v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
[    2.064330] RTL871X: rtl8723bu BT-Coex version = BTCOEX20140507-4E40
[    2.126702] RTL871X: rtw_ndev_init(wlan0)
[    2.127011] RTL871X: rtw_ndev_init(wlan1)
[    2.127311] usbcore: registered new interface driver rtl8723bu
[    2.127312] RTL871X: module init ret=0
[    3.299488] usbcore: registered new interface driver rtl8xxxu
[    3.301568] rtl8723bu 1-3:1.2 wlp0s20u3i2: renamed from wlan1
[    3.303285] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    3.303287] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    3.315818] rtl8723bu 1-3:1.2 wlx5863561030df: renamed from wlan0
[    4.697888] RTL871X: RTW_ADAPTIVITY_EN_AUTO, chplan:0x20, Regulation:3,3
[    4.697895] RTL871X: RTW_ADAPTIVITY_MODE_NORMAL
[    7.180211] RTL871X: nolinked power save enter
[    7.846028] RTL871X: RTW_ADAPTIVITY_EN_AUTO, chplan:0x20, Regulation:3,3
[    7.846035] RTL871X: RTW_ADAPTIVITY_MODE_NORMAL
[    8.468344] RTL871X: nolinked power save leave
[   10.349025] RTL871X: nolinked power save enter
[   15.418614] RTL871X: RTW_ADAPTIVITY_EN_AUTO, chplan:0x20, Regulation:3,3
[   15.418618] RTL871X: RTW_ADAPTIVITY_MODE_NORMAL
[   16.064398] RTL871X: nolinked power save leave
[   17.952570] RTL871X: nolinked power save enter
[   18.617949] RTL871X: RTW_ADAPTIVITY_EN_AUTO, chplan:0x20, Regulation:3,3
[   18.617953] RTL871X: RTW_ADAPTIVITY_MODE_NORMAL
[   21.116632] RTL871X: nolinked power save leave
[   21.325862] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[   21.395625] RTL871X: start auth
[   21.397799] RTL871X: auth success, start assoc
[   21.400970] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
[   21.400981] RTL871X: assoc success
[   21.405310] RTL871X: send eapol packet
[   21.415419] RTL871X: send eapol packet
[   21.545619] RTL871X: set pairwise key camid:4, addr:ac:9e:17:66:5d:58, kid:0, type:AES
[   21.546573] RTL871X: set group key camid:5, addr:ac:9e:17:66:5d:58, kid:2, type:AES
[  396.550542] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  396.558170] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  396.558983] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  396.559790] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  396.561343] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  396.562138] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  398.245038] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[  398.563411] RTL871X: start auth
[  398.568610] RTL871X: auth success, start assoc
[  398.577069] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
[  398.577104] RTL871X: assoc success
[  398.584379] RTL871X: send eapol packet
[  398.662028] RTL871X: send eapol packet
[  398.788111] RTL871X: set pairwise key camid:4, addr:ac:9e:17:66:5d:58, kid:0, type:AES
[  398.789340] RTL871X: set group key camid:5, addr:ac:9e:17:66:5d:58, kid:2, type:AES
[  991.123285] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[  992.071298] RTL871X: nolinked power save enter
[  992.732892] RTL871X: RTW_ADAPTIVITY_EN_AUTO, chplan:0x20, Regulation:3,3
[  992.732899] RTL871X: RTW_ADAPTIVITY_MODE_NORMAL
[  995.315322] RTL871X: nolinked power save leave
[  995.524086] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[  995.600447] RTL871X: start auth
[  995.605161] RTL871X: auth success, start assoc
[  995.608423] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
[  995.608454] RTL871X: assoc success
[  995.613830] RTL871X: send eapol packet
[  995.634464] RTL871X: send eapol packet
[  995.743915] RTL871X: set pairwise key camid:4, addr:ac:9e:17:66:5d:58, kid:0, type:AES
[  995.744866] RTL871X: set group key camid:5, addr:ac:9e:17:66:5d:58, kid:2, type:AES
[ 1110.215731] RTL871X: sta recv deauth reason code(7) sta:ac:9e:17:66:5d:58, ignore = 0
[ 1111.913710] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[ 1112.140756] RTL871X: start auth
[ 1112.144511] RTL871X: auth success, start assoc
[ 1112.149138] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
[ 1112.149170] RTL871X: assoc success
[ 1112.150962] RTL871X: send eapol packet
[ 1112.160610] RTL871X: send eapol packet
[ 1112.364842] RTL871X: set pairwise key camid:4, addr:ac:9e:17:66:5d:58, kid:0, type:AES
[ 1112.366081] RTL871X: set group key camid:5, addr:ac:9e:17:66:5d:58, kid:2, type:AES
makem@teclst:~$ dmesg | grep -i sdio
makem@teclst:~$ 

```

Does that assist?

Compiling the driver:

[https://github.com/lwfinger/rtl8723bu](https://github.com/lwfinger/rtl8723bu)

"[COLOR=#24292E][FONT=-apple-system]If you want to operate the hardware as a station AND as an access point [/FONT][/COLOR]*simultaneously*[COLOR=#24292E][FONT=-apple-system], follow these instructions. [/FONT][/COLOR][COLOR=#ff0000][FONT=-apple-system]This will show two devices when you run the [/FONT]iwconfig[FONT=-apple-system] command[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]."

[/FONT][/COLOR]That a possibility?

Error popup:

Connection failure
Failed to add/activate connection
(7) The access point /org/freedesktop/NetworkManager/AccessPoint/99 was not in the scan.

---

### Post by chili555 on 2017-07-02
Please do:```
sudo gedit /etc/modules
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
#8723bu
```Proofread carefully, save and close the text editor.

Now do:```
cd rtl8723bu
sudo make uninstall
sudo modprobe -r 8723bu
```Reboot and again let us see:```
dmesg | grep -i rtl
```I think we created a conflict; please see:> usbcore: registered new interface driver [COLOR="#FF0000"]rtl8xxxu[/COLOR]

---

### Post by makem2 on 2017-07-02
```

makem@teclst:~$ dmesg | grep -i rtl
[    3.128229] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    3.128231] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    3.131966] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_fw.bin failed with error -2
[    3.131970] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_fw.bin
[    3.133217] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    3.133219] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    3.133228] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_fw.bin failed with error -2
[    3.133229] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_fw.bin
[    3.375768] usb 1-3: rtl8723bu_parse_efuse: dumping efuse (0x200 bytes):
[    3.375880] usb 1-3: RTL8723BU rev D (SMIC) 1T1R, TX queues 3, WiFi=1, BT=1, GPS=0, HI PA=0
[    3.375882] usb 1-3: RTL8723BU MAC: 58:63:56:10:30:df
[    3.375885] usb 1-3: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[    4.177359] usbcore: registered new interface driver rtl8xxxu
[    4.182133] rtl8xxxu 1-3:1.2 wlx5863561030df: renamed from wlan0
[   15.566017] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[   15.574012] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
makem@teclst:~$ 

```

The available connections now only has one set available.

---

### Post by chili555 on 2017-07-02
> The available connections now only has one set available.Awesome! And does it connect as expected? May we see:```
lsmod | grep -e 8723 -e rtl
```

---

### Post by makem2 on 2017-07-02
> **chili555 said:**
> Awesome! And does it connect as expected? May we see:```
lsmod | grep -e 8723 -e rtl
```

No, it does not connect

EDIT: output as requested (passed from problem machine via USB dongle)

```

makem@teclst:~$ lsmod | grep -e 8723 -e rtl
rtl8xxxu              122880  0
mac80211              761856  1 rtl8xxxu
btrtl                  16384  1 btusb
bluetooth             557056  12 btrtl,btintel,bnep,btbcm,btusb
makem@teclst:~$ 

```

---

### Post by praseodym on 2017-07-02
Firmware is not loaded correctly. Install this file and reboot:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161.1_all.deb)

---

### Post by makem2 on 2017-07-02
Unless I use the USB dongle again I cannot install that file. Should I do that?

---

### Post by jeremy31 on 2017-07-02
What kernel are we dealing with?  ```
uname -a
```

The only firmware issue I saw was for the bluetooth

---

### Post by makem2 on 2017-07-02
> **jeremy31 said:**
> What kernel are we dealing with?  ```
uname -a
```

The only firmware issue I saw was for the bluetooth

```

makem@teclst:~$ uname -a
Linux teclst 4.8.0-58-generic #63~16.04.1-Ubuntu SMP Mon Jun 26 18:08:51 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
makem@teclst:~

```

obtained via usb flash drive from problem machine

---

### Post by chili555 on 2017-07-02
Also post:```
rfkill list all
dmesg | grep wlx
```

---

### Post by makem2 on 2017-07-02
> **chili555 said:**
> Also post:```
rfkill list all
dmesg | grep wlx
```

```

makem@teclst:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
makem@teclst:~$ dmesg | grep wlx
[    4.150957] rtl8xxxu 1-3:1.2 wlx5863561030df: renamed from wlan0
[    4.175233] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    4.182692] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    4.236613] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[   13.885215] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   13.889036] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   14.092365] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   14.296399] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   14.500390] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   15.692927] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   15.696593] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   15.900471] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   16.104512] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   16.308512] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   17.873523] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   17.876896] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   18.080711] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   18.308630] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   18.512608] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   20.577613] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   20.581636] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   20.784776] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   20.988892] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   21.192803] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   33.302672] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   33.305997] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   33.509575] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   33.713587] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   33.917598] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   38.015504] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[   39.058579] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   39.062451] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   39.265804] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   39.469856] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   39.673866] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   50.738711] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   50.743618] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   50.946546] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   51.150555] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   51.354464] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   63.015194] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[   64.060016] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   64.064638] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   64.267182] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   64.471184] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   64.675226] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   75.736688] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   75.740238] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   75.943836] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   76.147924] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   76.351879] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   88.015664] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[   89.057341] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[   89.063405] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[   89.264523] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[   89.468550] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[   89.672596] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[   99.199957] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  100.249970] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  100.253908] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  100.457224] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  100.661184] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  100.865198] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  102.443436] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  124.847512] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  124.852130] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  125.054621] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  125.258631] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  125.462635] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  136.536000] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  136.539330] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  136.743205] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  136.947272] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  137.151227] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  149.022408] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  150.068868] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  150.072787] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  150.275898] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  150.479919] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  150.683958] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  161.757325] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  161.760710] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  161.964656] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  162.168660] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  162.372673] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  174.020537] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  218.204466] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  218.207903] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  218.411756] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  218.615771] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  218.819789] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  229.885280] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  229.889327] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  230.092401] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  230.296410] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  230.500362] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  242.025069] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  475.110720] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  475.114609] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  475.317800] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  475.521916] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  475.725932] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  486.791277] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  486.796687] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  486.998449] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  487.202563] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  487.406576] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  499.039016] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  500.095968] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  500.099157] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  500.303188] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  500.507199] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  500.711298] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  511.776930] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  511.780712] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  511.983930] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  512.187938] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  512.391949] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  524.042256] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  525.093371] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  525.097097] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  525.300540] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  525.504673] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  525.708681] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  536.770070] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  536.774232] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  536.977342] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  537.181264] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  537.385329] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  549.041131] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  550.082936] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  550.086241] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  550.289948] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  550.493968] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  550.697947] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  561.763373] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  561.767704] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  561.970670] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  562.174700] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  562.378706] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  574.043812] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  875.144618] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  875.148219] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  875.351831] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  875.555954] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  875.759964] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  886.829306] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  886.833449] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  887.036464] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  887.240594] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  887.444620] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  899.061322] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  900.106199] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  900.109960] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  900.313320] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  900.517323] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  900.721338] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  911.786801] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  911.789974] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  911.993960] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  912.197886] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  912.401980] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  924.063475] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  925.107452] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  925.111488] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  925.314590] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  925.518611] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  925.722602] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  936.784186] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  936.787158] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  936.991321] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  937.195360] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  937.399356] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  949.064111] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[  950.112752] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  950.117727] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  950.319963] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  950.523960] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  950.727970] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  961.793455] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[  961.797344] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[  962.000720] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[  962.204672] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[  962.408743] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[  974.065378] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[ 1275.170904] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1275.174872] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1275.377968] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1275.581988] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1275.785996] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1286.847237] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1286.851154] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1287.054531] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1287.258547] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1287.462525] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1299.084451] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[ 1302.163805] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1302.168603] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1302.371330] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1302.575339] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1302.779357] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1313.844920] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1313.849061] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1314.052103] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1314.256110] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1314.460126] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1324.084572] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[ 1325.129471] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1325.134460] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1325.336627] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1325.540644] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1325.744752] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1336.806209] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1336.810403] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1337.013361] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1337.217382] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1337.421390] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1349.087551] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[ 1350.130964] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1350.135443] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1350.338102] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1350.542008] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1350.746021] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1367.856019] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1367.860255] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1368.063077] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1368.267090] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1368.471104] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1374.087518] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[ 1675.168698] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1675.172319] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1675.376006] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1675.580014] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1675.784019] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
[ 1699.106455] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[ 1724.196687] wlx5863561030df: authenticate with ac:9e:17:66:5d:58
[ 1724.199031] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 1/3)
[ 1724.402572] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 2/3)
[ 1724.606661] wlx5863561030df: send auth to ac:9e:17:66:5d:58 (try 3/3)
[ 1724.810624] wlx5863561030df: authentication with ac:9e:17:66:5d:58 timed out
makem@teclst:~$ 

```

[COLOR=#000000]obtained via usb flash drive from problem machine[/COLOR]

---

### Post by makem2 on 2017-07-02
As I seemed to be back at the beginning with a wifi connection which did not work under any circumstances I decided to start at the beginning and recompile the driver as per instructions from day one.

The wifi is working, connecting correctly to makem2.4 after a shut down/restart and there is only one list of available connections. After a reboot no connections are available and I must shut down/restart.

I know I have been there before, today, but at least I have got rid of duplication in available connections, can use the internet and make output code available without using two machines and a usb flash drive.

---

### Post by chili555 on 2017-07-02
You log suggests that there are many attempts and subsequent failures to associate with the router or other access point. May we assume that you have carefully double-checked the WPA password?

In many cases, Linux drivers are sensitive to configuration in the router.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, then I suggest that you abandon the internal device and blacklist its driver:

```
sudo -i
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit
```

Thereafter, rely on the USB.

---

### Post by makem2 on 2017-07-02
I will check everything as you suggest. However my router is an Asus RT-AC68U 2.4 and 5GHz. It is used for several various OS machines and mobile phones and as you know, for almost a year gave no trouble with connecting to the Teclast machine.

I use fixed IPs, fixed channel 6 (the least used in my area) and custom Merlin router firmware.

Do you think the suggestions you make would have an effect on the reason why a reboot does not work when a shutdown/restart does? No router changes have been made during the period since the Teclast worked correctly.

I appreciate your assistance and will report back after I make any necessary changes.

---

### Post by makem2 on 2017-07-02
Asus RT-AC68U using asuswrt-merlin firmware.

Wireless Mode = Auto (N not selected)
Authentification= WPA2-Personal
WPA Encrytion= AES
WPA Pre-Shared Key = (verified on all machines)
Control Channel = 6


No changes made to the router.


Regulatory domain returned 00, changed to GB in crda (previously blank)

Tectlast still will not connect after a reboot, only after a shutdown/restart.


As for IPv6, I see many reports of problems with error messages after disabling it. I will check further later.

Problem with blacklisting the driver is a) It did work fine and b) the machine only has two USB port one of which is used for the mouse.

---

### Post by chili555 on 2017-07-02
> Do you think the suggestions you make would have an effect on the reason why a reboot does not work when a shutdown/restart does?I am reasonably confident that much of your problem currently is interaction between two drivers attempting to drive two different devices at once.>  It is used for several various OS machines and mobile phonesI understand. I myself have several Ubuntu machines, iPads and even a Chromebook. What I understand as well is that in my case and in the case of many to whom I've made these suggestions on this and other forums, the tweaks are very often (not always) helpful. It costs nothing but a few moments of your time to find out.

I'd like to try everything we can to get the internal device working. If we can not, I suggest we accept reality and use the USB dongle.

---

### Post by makem2 on 2017-07-02
I also hate abandoning something which worked at one time and for some reason a problem has crept in.

I cannot see where the rtl8xxxu appeared from and it appears to me that is the problem. Is it not possible just to remove it manually?

However, I do appreciate the time you have spent and understand that I may have to be content with what I now have as I cannot fix it.

---

### Post by chili555 on 2017-07-02
>  Is it not possible just to remove it manually?
That's what blacklisting does, essentially. It prevents it from loading.

---

### Post by makem2 on 2017-07-02
> **chili555 said:**
> That's what blacklisting does, essentially. It prevents it from loading.

Blacklisting brought back the double network entries! Two makem2.4 again, no internet until turn off the connected one and turn on the other even after a reboot or shutdown. Seems like a circular path here.

---

### Post by chili555 on 2017-07-02
>   Blacklisting brought back the double network entries!  Something is not right here. Let us see: ```
tail -n5 /etc/modprobe.d/blacklist.conf
lsmod | grep -e 8723 -e rtl
iwconfig
```All run before you change or attempt to fix anything.

---

### Post by makem2 on 2017-07-03
```

makem@teclst:~$ tail -n5 /etc/modprobe.d/blacklist.conf
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rtl8xxxu
makem@teclst:~$ lsmod | grep -e 8723 -e rtl
8723bu                880640  0
btrtl                  16384  1 btusb
bluetooth             557056  39 btrtl,btintel,bnep,btbcm,rfcomm,btusb
cfg80211              581632  1 8723bu
makem@teclst:~$ iwconfig
lo        no wireless extensions.


wlp0s20u3i2  IEEE 802.11bgn  ESSID:"makem2.4"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: AC:9E:17:66:5D:58   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


wlx5863561030df  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


makem@teclst:~$

```

To enable wifi access I disconnected the connection in the lower section of the list and reconnected using the top connection, having just started the machine for the first time today.

---

### Post by chili555 on 2017-07-03
This just gets weirder by the minute! Please post the entirety of:```
lsmod
```Fascinating...

---

### Post by makem2 on 2017-07-03
Result after starting the machine up from a long shutdown (No internet access found)

```

makem@teclst:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  12
bnep                   20480  2
rtsx_usb_ms            20480  0
rtsx_usb_sdmmc         28672  0
memstick               20480  1 rtsx_usb_ms
snd_hda_codec_hdmi     45056  1
8723bu                880640  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
cfg80211              581632  1 8723bu
bluetooth             557056  39 btrtl,btintel,bnep,btbcm,rfcomm,btusb
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
joydev                 20480  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_hda_intel          36864  5
snd_soc_rt5640        118784  0
snd_soc_ssm4567        16384  0
ablk_helper            16384  1 aesni_intel
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_soc_rl6231         16384  1 snd_soc_rt5640
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
snd_soc_core          233472  2 snd_soc_ssm4567,snd_soc_rt5640
intel_cstate           16384  0
snd_compress           20480  1 snd_soc_core
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ac97_bus               16384  1 snd_soc_core
intel_rapl_perf        16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
goodix                 16384  0
kxcjk_1013             20480  0
elan_i2c               36864  0
industrialio_triggered_buffer    16384  1 kxcjk_1013
snd_seq_midi           16384  0
input_leds             16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
serio_raw              16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
intel_pch_thermal      16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
mei_me                 40960  0
snd                    86016  23 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
mei                   102400  1 mei_me
lpc_ich                24576  0
processor_thermal_device    16384  0
soundcore              16384  1 snd
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3403_thermal        16384  0
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
snd_soc_sst_acpi       16384  0
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
8250_dw                16384  0
int3402_thermal        16384  0
int3406_thermal        16384  0
i2c_designware_platform    16384  0
spi_pxa2xx_platform    24576  0
int3400_thermal        16384  0
i2c_designware_core    20480  1 i2c_designware_platform
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
acpi_als               16384  0
mac_hid                16384  0
acpi_pad               24576  0
kfifo_buf              16384  2 acpi_als,industrialio_triggered_buffer
industrialio           65536  4 kxcjk_1013,acpi_als,industrialio_triggered_buffer,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
i915                 1314816  11
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 i915,drm_kms_helper
ahci                   36864  4
libahci                32768  1 ahci
wmi                    16384  0
sdhci_acpi             16384  0
video                  40960  2 int3406_thermal,i915
sdhci                  45056  1 sdhci_acpi
fjes                   28672  0
i2c_hid                20480  0
hid                   122880  4 i2c_hid,hid_generic,usbhid
makem@teclst:~$ 



```

Result after disconnecting the lower makem2.4 connection (no access) and connecting to the top makem2.4 to gain access:

```

makem@teclst:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  12
bnep                   20480  2
rtsx_usb_ms            20480  0
rtsx_usb_sdmmc         28672  0
memstick               20480  1 rtsx_usb_ms
snd_hda_codec_hdmi     45056  1
8723bu                880640  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
cfg80211              581632  1 8723bu
bluetooth             557056  39 btrtl,btintel,bnep,btbcm,rfcomm,btusb
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
joydev                 20480  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_hda_intel          36864  5
snd_soc_rt5640        118784  0
snd_soc_ssm4567        16384  0
ablk_helper            16384  1 aesni_intel
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_soc_rl6231         16384  1 snd_soc_rt5640
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
snd_soc_core          233472  2 snd_soc_ssm4567,snd_soc_rt5640
intel_cstate           16384  0
snd_compress           20480  1 snd_soc_core
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ac97_bus               16384  1 snd_soc_core
intel_rapl_perf        16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
goodix                 16384  0
kxcjk_1013             20480  0
elan_i2c               36864  0
industrialio_triggered_buffer    16384  1 kxcjk_1013
snd_seq_midi           16384  0
input_leds             16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
serio_raw              16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
intel_pch_thermal      16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
mei_me                 40960  0
snd                    86016  23 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
mei                   102400  1 mei_me
lpc_ich                24576  0
processor_thermal_device    16384  0
soundcore              16384  1 snd
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3403_thermal        16384  0
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
snd_soc_sst_acpi       16384  0
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
8250_dw                16384  0
int3402_thermal        16384  0
int3406_thermal        16384  0
i2c_designware_platform    16384  0
spi_pxa2xx_platform    24576  0
int3400_thermal        16384  0
i2c_designware_core    20480  1 i2c_designware_platform
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
acpi_als               16384  0
mac_hid                16384  0
acpi_pad               24576  0
kfifo_buf              16384  2 acpi_als,industrialio_triggered_buffer
industrialio           65536  4 kxcjk_1013,acpi_als,industrialio_triggered_buffer,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
i915                 1314816  12
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 i915,drm_kms_helper
ahci                   36864  4
libahci                32768  1 ahci
wmi                    16384  0
sdhci_acpi             16384  0
video                  40960  2 int3406_thermal,i915
sdhci                  45056  1 sdhci_acpi
fjes                   28672  0
i2c_hid                20480  0
hid                   122880  4 i2c_hid,hid_generic,usbhid
makem@teclst:~$

```

I hope you stay fascinated

---

### Post by chili555 on 2017-07-03
If possible, it makes even _less_ sense than my previous posts! Let's have a look at the result of:```
dmesg | grep wl
```:confused:  :confused:  :confused:

---

### Post by makem2 on 2017-07-03
```

makem@teclst:~$ dmesg | grep wl
[    3.353626] RTL871X: rtw_ndev_init(wlan0)
[    3.353900] RTL871X: rtw_ndev_init(wlan1)
[    3.356172] rtl8723bu 1-3:1.2 wlp0s20u3i2: renamed from wlan1
[    3.379890] rtl8723bu 1-3:1.2 wlx5863561030df: renamed from wlan0
[    4.093975] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[    5.272428] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[    5.276945] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    5.277050] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    5.483394] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    5.487651] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[   12.935999] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[   14.635810] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[   15.002174] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
[   15.002348] IPv6: ADDRCONF(NETDEV_CHANGE): wlx5863561030df: link becomes ready
[  118.687980] RTL871X: rtw_set_802_11_connect(wlp0s20u3i2)  fw_state=0x00000008
[  118.945194] RTL871X: rtw_cfg80211_indicate_connect(wlp0s20u3i2) BSS not found !!
[  118.945326] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s20u3i2: link becomes ready
[  118.950282] RTL871X: port switch - port0(wlp0s20u3i2), port1(wlx5863561030df)
makem@teclst:~$

```

Have I discovered something new then? Only done this once in my life so far!

---

### Post by chili555 on 2017-07-03
Is the USB wireless dongle you purchased in here?> makem@teclst:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 258a:6a88  
Bus 001 Device 006: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubPlease try removing it; run again:```
lsusb
```Insert it; run again:```
lsusb
```Which exact device is the USB wireless you purchased?

> Have I discovered something new then? It seems so, but let's verify twice before we get out the plasma cutter and sledge hammer.

---

### Post by makem2 on 2017-07-03
I don't have any USB device attached except for the mouse dongle so the answer to your question is, "no".

I have put the device away for use with my RPi's one day.

I can get it out and do as you request, but it it necessary?

I also see two apparent wife connections but can assure you there is only the internal device in use. This has been the case since I first enabled WiFi access without the USB TP-Link AC450.

---

### Post by chili555 on 2017-07-03
> "If you want to operate the hardware as a station AND as an access point simultaneously, follow these instructions. This will show two devices when you run the iwconfig command."

That a possibility?That is from your post way up there and I think it is our problem. It seems that the default code is written to build in concurrent mode and that we have to take affirmative steps to make it NOT concurrent mode. Leaving aside any comments I may have as to the practicality of defaulting to two interfaces (!!!), let's just fix it. From the terminal:```
cd rtl8723bu
make clean
gedit Makefile
```Use nano or kate or leafpad if you don't have the text editor gedit. Change this sequence:```
EXTRA_CFLAGS += -Wno-unused-variable
EXTRA_CFLAGS += -Wno-unused-value
EXTRA_CFLAGS += -Wno-unused-label
EXTRA_CFLAGS += -Wno-unused-parameter
EXTRA_CFLAGS += -Wno-unused-function
EXTRA_CFLAGS += -Wno-unused
EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
```To comment out the 'concurrent' part:```
EXTRA_CFLAGS += -Wno-unused-variable
EXTRA_CFLAGS += -Wno-unused-value
EXTRA_CFLAGS += -Wno-unused-label
EXTRA_CFLAGS += -Wno-unused-parameter
EXTRA_CFLAGS += -Wno-unused-function
EXTRA_CFLAGS += -Wno-unused
**#**EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
```Proofread carefully, save and close the text editor.

Now do:```
make
sudo make install
```Reboot while I write a tear-stained apology.

---

### Post by makem2 on 2017-07-03
No apology necessary, I am only to grateful for the learning experience. (I remembered to copy to desktop too!)

Code carried before rebooting as requested:

```

makem@teclst:~$ cd ~/rtl8723bu
makem@teclst:~/rtl8723bu$ make clean
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd */*.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
makem@teclst:~/rtl8723bu$ nano Makefile
makem@teclst:~/rtl8723bu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.8.0-58-generic/build M=/home/makem/rtl8723bu  modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-58-generic'
  CC [M]  /home/makem/rtl8723bu/core/rtw_cmd.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_security.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_debug.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_io.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_ioctl_query.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_ioctl_set.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_ieee80211.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_mlme.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_mlme_ext.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_wlan_util.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_vht.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_pwrctrl.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_rf.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_recv.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_sta_mgt.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_ap.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_xmit.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_p2p.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_tdls.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_br_ext.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_iol.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_sreset.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_btcoex.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_beamforming.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_odm.o
  CC [M]  /home/makem/rtl8723bu/core/rtw_efuse.o
  CC [M]  /home/makem/rtl8723bu/os_dep/osdep_service.o
  CC [M]  /home/makem/rtl8723bu/os_dep/os_intfs.o
  CC [M]  /home/makem/rtl8723bu/os_dep/usb_intf.o
  CC [M]  /home/makem/rtl8723bu/os_dep/usb_ops_linux.o
  CC [M]  /home/makem/rtl8723bu/os_dep/ioctl_linux.o
  CC [M]  /home/makem/rtl8723bu/os_dep/xmit_linux.o
  CC [M]  /home/makem/rtl8723bu/os_dep/mlme_linux.o
  CC [M]  /home/makem/rtl8723bu/os_dep/recv_linux.o
  CC [M]  /home/makem/rtl8723bu/os_dep/ioctl_cfg80211.o
  CC [M]  /home/makem/rtl8723bu/os_dep/wifi_regd.o
  CC [M]  /home/makem/rtl8723bu/os_dep/rtw_android.o
  CC [M]  /home/makem/rtl8723bu/os_dep/rtw_proc.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_intf.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_com.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_com_phycfg.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_phy.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_btcoex.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_usb.o
  CC [M]  /home/makem/rtl8723bu/hal/hal_usb_led.o
  CC [M]  /home/makem/rtl8723bu/hal/HalPwrSeqCmd.o
  CC [M]  /home/makem/rtl8723bu/hal/Hal8723BPwrSeq.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_sreset.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_hal_init.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_phycfg.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_rf6052.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_dm.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_rxdesc.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723b_cmd.o
  CC [M]  /home/makem/rtl8723bu/hal/usb_halinit.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723bu_led.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723bu_xmit.o
  CC [M]  /home/makem/rtl8723bu/hal/rtl8723bu_recv.o
  CC [M]  /home/makem/rtl8723bu/hal/usb_ops.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_debug.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_AntDiv.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_interface.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_HWConfig.o
  CC [M]  /home/makem/rtl8723bu/hal/odm.o
  CC [M]  /home/makem/rtl8723bu/hal/HalPhyRf.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_EdcaTurboCheck.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_DIG.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_PathDiv.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_RaInfo.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_DynamicBBPowerSaving.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_DynamicTxPower.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_CfoTracking.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_NoiseMonitor.o
  CC [M]  /home/makem/rtl8723bu/hal/HalBtc8723b1Ant.o
  CC [M]  /home/makem/rtl8723bu/hal/HalBtc8723b2Ant.o
  CC [M]  /home/makem/rtl8723bu/hal/HalHWImg8723B_BB.o
  CC [M]  /home/makem/rtl8723bu/hal/HalHWImg8723B_MAC.o
  CC [M]  /home/makem/rtl8723bu/hal/HalHWImg8723B_RF.o
  CC [M]  /home/makem/rtl8723bu/hal/HalHWImg8723B_FW.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_RegConfig8723B.o
  CC [M]  /home/makem/rtl8723bu/hal/HalPhyRf_8723B.o
  CC [M]  /home/makem/rtl8723bu/hal/odm_RTL8723B.o
  CC [M]  /home/makem/rtl8723bu/platform/platform_ops.o
  LD [M]  /home/makem/rtl8723bu/8723bu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/makem/rtl8723bu/8723bu.mod.o
  LD [M]  /home/makem/rtl8723bu/8723bu.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-58-generic'
makem@teclst:~/rtl8723bu$

```

---

### Post by makem2 on 2017-07-03
After a reboot there are still two lists under the wifi icon which suggests it has a connection. It does not. It is necessary to disconnect the apparently connected connection and select the alternative one to immediately have access.

In addition the mouse action is extremely slow, perhaps because the wifi is searching via the default connection? The mouse also seems a little slow even after the connection is made.

---

### Post by makem2 on 2017-07-03
Output after the re-compile:

```

makem@teclst:~$ tail -n5 /etc/modprobe.d/blacklist.conf
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rtl8xxxu
makem@teclst:~$ lsmod | grep -e 8723 -e rtl
8723bu                880640  0
btrtl                  16384  1 btusb
cfg80211              581632  1 8723bu
bluetooth             557056  39 btrtl,btintel,bnep,btbcm,rfcomm,btusb
makem@teclst:~$ iwconfig
wlx5863561030df  IEEE 802.11bgn  ESSID:"makem2.4"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: AC:9E:17:66:5D:58   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


wlp0s20u3i2  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


makem@teclst:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  12
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
rtsx_usb_sdmmc         28672  0
bnep                   20480  2
8723bu                880640  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
cfg80211              581632  1 8723bu
bluetooth             557056  39 btrtl,btintel,bnep,btbcm,rfcomm,btusb
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
joydev                 20480  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_hda_codec_hdmi     45056  1
snd_hda_codec_realtek    86016  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_soc_rt5640        118784  0
goodix                 16384  0
snd_soc_ssm4567        16384  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
elan_i2c               36864  0
snd_soc_core          233472  2 snd_soc_ssm4567,snd_soc_rt5640
kxcjk_1013             20480  0
industrialio_triggered_buffer    16384  1 kxcjk_1013
snd_compress           20480  1 snd_soc_core
aesni_intel           167936  0
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
intel_cstate           16384  0
intel_rapl_perf        16384  0
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
input_leds             16384  0
serio_raw              16384  0
snd_pcm               110592  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
intel_pch_thermal      16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
lpc_ich                24576  0
snd                    86016  23 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3403_thermal        16384  0
dw_dmac                16384  0
snd_soc_sst_acpi       16384  0
dw_dmac_core           24576  1 dw_dmac
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
8250_dw                16384  0
spi_pxa2xx_platform    24576  0
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
int3402_thermal        16384  0
int3406_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
acpi_als               16384  0
mac_hid                16384  0
acpi_pad               24576  0
acpi_thermal_rel       16384  1 int3400_thermal
kfifo_buf              16384  2 acpi_als,industrialio_triggered_buffer
industrialio           65536  4 kxcjk_1013,acpi_als,industrialio_triggered_buffer,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
i915                 1314816  9
ahci                   36864  4
libahci                32768  1 ahci
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
wmi                    16384  0
syscopyarea            16384  1 drm_kms_helper
video                  40960  2 int3406_thermal,i915
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fjes                   28672  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 i915,drm_kms_helper
i2c_hid                20480  0
sdhci_acpi             16384  0
hid                   122880  4 i2c_hid,hid_generic,usbhid
sdhci                  45056  1 sdhci_acpi
makem@teclst:~$ dmesg | grep wl
[    3.331219] RTL871X: rtw_ndev_init(wlan0)
[    3.331727] RTL871X: rtw_ndev_init(wlan1)
[    3.335189] rtl8723bu 1-3:1.2 wlp0s20u3i2: renamed from wlan1
[    3.362298] rtl8723bu 1-3:1.2 wlx5863561030df: renamed from wlan0
[    4.173407] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[    5.410660] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[    5.415322] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    5.415379] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    5.580742] IPv6: ADDRCONF(NETDEV_UP): wlx5863561030df: link is not ready
[    5.586728] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[   11.057466] IPv6: ADDRCONF(NETDEV_UP): wlp0s20u3i2: link is not ready
[   12.686729] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[   12.928644] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
[   12.928699] IPv6: ADDRCONF(NETDEV_CHANGE): wlx5863561030df: link becomes ready
[  273.152021] RTL871X: rtw_set_802_11_connect(wlx5863561030df)  fw_state=0x00000008
[  273.458918] RTL871X: rtw_cfg80211_indicate_connect(wlx5863561030df) BSS not found !!
makem@teclst:~$

```

During the time it took to obtain this output the internet connection was dropped and it was necessary to change to the alternative available one.

---

### Post by makem2 on 2017-07-03
Now it is MY time to make an apology!!

I saw that the output had not appeared to change after the re-compile. I felt after reading the output that I had omitted to do 'sudo make install'

Apology, profusely. Repeated the instructions and, lo and behold, one wifi list which WAS connected.

EDIT: The connection persists after a reboot too.

Is there any housekeeping to do to remove things which are not required now?

---

### Post by chili555 on 2017-07-03
Only one bit of housekeeping. You have compiled the driver for your current running kernel only. When Update Manager installs a later one, also known as linux-image, after the requested reboot, re-compile:

```
cd  rtl8723bu
make clean
make
sudo make install
sudo modprobe 8723bu
```
Please retain the file and these instructions for that time.

Sorry that I didn't catch the 'concurrent mode' glitch for an exciting 50+ posts!

I'm glad that it's now working as expected.

---

### Post by makem2 on 2017-07-03
Thank you very much for your help. I have this time made sure I will not miss-lay the file and instructions.

I too am surprised that the default is concurrent when I would have thought that that use would be less.

Not sure if I should re-mark this as solved because it may lead to heartache for others. If it were possible to delete all posts except the necessary ones then I think it would be of great value to followers who make the same 'concurrent' mistake.

My next project is getting grub to recognise Bluetooth.

EDIT: One last point noted: Your instructions differ from those given first time. This time there is an additional line:
sudo modprobe [COLOR=#000000][FONT=&quot]8723bu
[/FONT][/COLOR]

---

### Post by chili555 on 2017-07-03
> Not sure if I should re-mark this as solved because it may lead to heartache for others. If it were possible to delete all posts except the necessary ones then I think it would be of great value to followers who make the same 'concurrent' mistake.I'll put a warning at the earlier post where I offered the solution. It should be clear.> EDIT: One last point noted: Your instructions differ from those given first time. This time there is an additional line:
sudo modprobe 8723buI believe that's correct.

---

