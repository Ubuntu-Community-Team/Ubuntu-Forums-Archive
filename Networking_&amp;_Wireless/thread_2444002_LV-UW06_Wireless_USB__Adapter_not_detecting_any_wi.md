---
title: "LV-UW06 Wireless USB  Adapter not detecting any wifi in Ubuntu 20.04 LTS in Desktop"
date: 2020-05-23
forum: Networking &amp; Wireless
---

### Post by mordex on 2020-05-23
I want to use Wireless USB Adapter for connect wifi in my desktop.

I have attached photo of Wireless USB Adapter and my ubuntu os information.

Now i have installed  two wifi driver in my system after some analysis.

[URL="https://askubuntu.com/questions/1062402/cant-find-wifi-drivers-for-0bdaf179-realtek-semiconductor-corp"]https://askubuntu.com/questions/1062402/cant-find-wifi-drivers-for-0bdaf179-realtek-semiconductor-corp

[/URL][https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

But both drivers are not working for me somehow it shows icon off wifi but when i am click on Select network nothing is visible.

--------------------------------------------------------------------------------------------------------

**lsusb result**
```

hp@HP-Computer:~$ lsusb
Bus 002 Device 004: ID 18d1:4ee2 Google Inc. Nexus Device (debug)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:f179 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 001 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
--------------------------------------------------------------------------------------------------------------

**iwconfig result**```

hp@HP-Computer:~$ iwconfig
eno1      no wireless extensions.

lo        no wireless extensions.

wlx00e0222cf986  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
------------------------------------------------------------------------------------------------------

---

### Post by coffeecat on 2020-05-23
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2020-05-23
I suspect that the instructions you followed missed a crucial step. Please run:

```
cd ~/rtl8188fu
sudo cp firmware/rtl8188fufw.bin /lib/firmware/rtlwifi/
sudo modprobe -r rtl8188fu
sudo modprobe rtl8188fu

```
If the wireless is still not working, then please run the terminal commands:

```
rfkill list all
dmesg | grep -e rtl -e wlx

```
Post the result.

---

### Post by mordex on 2020-05-23
hp@HP-Computer:~$ rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

hp@HP-Computer:~$ dmesg | grep -e rtl -e wlx
[    2.790578] rtl8188fu: loading out-of-tree module taints kernel.
[    2.791017] rtl8188fu: module verification failed: signature and/or required key missing - tainting kernel
[    2.792839] RTL871X: rtl8188fu v4.3.23.6_20964.20170110
[    2.926572] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[    2.927786] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[    2.927788] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[    2.927788] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[    2.927789] RTL871X: rtl8188f_FirmwareDownload by IO write!
[    2.978327] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[    2.978328] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 52ms
[    2.978445] RTL871X:  <=== rtl8188f_FirmwareDownload()
[    2.997315] usbcore: registered new interface driver rtl8188fu
[    3.370781] rtl8188fu 1-1.5:1.0 wlx00e0222cf986: renamed from wlan0
[    4.429174] RTL871X: cfg80211_rtw_dump_station(wlx00e0222cf986)
[    4.814175] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[    4.814204] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[    4.814206] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[    4.814206] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[    4.814207] RTL871X: rtl8188f_FirmwareDownload by IO write!
[    4.865492] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[    4.865493] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 52ms
[    4.865553] RTL871X:  <=== rtl8188f_FirmwareDownload()
[    5.495050] RTL871X: rtl8188fu_hal_init in 692ms
[    5.509221] RTL871X: cfg80211_rtw_set_power_mgmt(wlx00e0222cf986) enabled:0, timeout:-1
[    5.556231] RTL871X: cfg80211_rtw_flush_pmksa(wlx00e0222cf986)
[    5.607682] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[    7.342780] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[    7.342786] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[    7.381197] RTL871X: ==> rtl8188fu_hal_deinit
[    8.977575] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[    8.982019] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[    8.982070] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[    8.982073] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[    8.982074] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[    8.982075] RTL871X: rtl8188f_FirmwareDownload by IO write!
[    9.029282] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[    9.029283] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 48ms
[    9.029390] RTL871X:  <=== rtl8188f_FirmwareDownload()
[    9.640386] RTL871X: rtl8188fu_hal_init in 664ms
[   11.364000] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[   11.364026] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[   11.395420] RTL871X: ==> rtl8188fu_hal_deinit
[   31.977532] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[   31.983180] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[   31.983211] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[   31.983213] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[   31.983213] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[   31.983214] RTL871X: rtl8188f_FirmwareDownload by IO write!
[   32.052313] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[   32.052314] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 72ms
[   32.052428] RTL871X:  <=== rtl8188f_FirmwareDownload()
[   32.985059] RTL871X: rtl8188fu_hal_init in 1008ms
[   34.751174] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[   34.751179] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[   34.778455] RTL871X: ==> rtl8188fu_hal_deinit
[   64.980061] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[   64.985506] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[   64.985560] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[   64.985563] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[   64.985564] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[   64.985564] RTL871X: rtl8188f_FirmwareDownload by IO write!
[   65.032131] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[   65.032132] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 48ms
[   65.032251] RTL871X:  <=== rtl8188f_FirmwareDownload()
[   65.644126] RTL871X: rtl8188fu_hal_init in 664ms
[   67.379115] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[   67.379123] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[   67.407444] RTL871X: ==> rtl8188fu_hal_deinit
[  107.979355] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[  107.983863] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[  107.983920] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[  107.983923] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[  107.983924] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[  107.983925] RTL871X: rtl8188f_FirmwareDownload by IO write!
[  108.030494] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[  108.030495] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 48ms
[  108.030609] RTL871X:  <=== rtl8188f_FirmwareDownload()
[  108.640605] RTL871X: rtl8188fu_hal_init in 660ms
[  110.365093] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[  110.365100] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[  110.393783] RTL871X: ==> rtl8188fu_hal_deinit
[  160.982748] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[  160.987753] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[  160.987809] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[  160.987812] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[  160.987813] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[  160.987813] RTL871X: rtl8188f_FirmwareDownload by IO write!
[  161.034879] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[  161.034881] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 48ms
[  161.034998] RTL871X:  <=== rtl8188f_FirmwareDownload()
[  161.651107] RTL871X: rtl8188fu_hal_init in 668ms
[  163.371735] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[  163.371742] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[  163.401156] RTL871X: ==> rtl8188fu_hal_deinit
[  223.981522] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[  223.986176] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[  223.986227] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[  223.986230] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[  223.986231] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[  223.986232] RTL871X: rtl8188f_FirmwareDownload by IO write!
[  224.033443] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[  224.033445] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 48ms
[  224.033563] RTL871X:  <=== rtl8188f_FirmwareDownload()
[  224.651679] RTL871X: rtl8188fu_hal_init in 668ms
[  226.387671] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[  226.387679] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[  226.415561] RTL871X: ==> rtl8188fu_hal_deinit
[  286.981137] RTL871X: cfg80211_rtw_scan(wlx00e0222cf986)
[  286.985866] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin
[  286.985917] usb 1-1.5: request firmware rtlwifi/rtl8188fufw.bin loaded
[  286.985919] RTL871X: rtl8188f_FirmwareDownload: fw_ver=4 fw_subver=0000 sig=0x88f1, Month=08, Date=22, Hour=17, Minute=36
[  286.985919] RTL871X: rtl8188f_FirmwareDownload(): Shift for fw header!
[  286.985920] RTL871X: rtl8188f_FirmwareDownload by IO write!
[  287.033599] RTL871X: rtl8188f_FirmwareDownload: DLFW OK !
[  287.033600] RTL871X: rtl8188f_FirmwareDownload success. write_fw:1, 48ms
[  287.033727] RTL871X:  <=== rtl8188f_FirmwareDownload()
[  287.651718] RTL871X: rtl8188fu_hal_init in 668ms
[  289.391208] RTL871X: survey done event(0) band:0 for wlx00e0222cf986
[  289.391217] RTL871X: rtw_indicate_scan_done(wlx00e0222cf986)
[  289.424487] RTL871X: ==> rtl8188fu_hal_deinit
```

---

### Post by mordex on 2020-05-23
Please check i run and uploaded output here.

---

### Post by wildmanne39 on 2020-05-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mordex on 2020-05-23
> Sure i will take care of this next time. 
Ok

---

### Post by praseodym on 2020-05-23
SecureBoot is disabled?

---

### Post by chili555 on 2020-05-23
Is it inserted in a USB2 or a USB3 slot? Please try USB2.

Is this a dual boot with Windows? Is the behavior any different if you reboot from Windows or if you boot straight to Ubuntu?

---

