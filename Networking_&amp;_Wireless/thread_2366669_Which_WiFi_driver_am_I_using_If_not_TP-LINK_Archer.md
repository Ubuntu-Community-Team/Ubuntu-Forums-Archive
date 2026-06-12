---
title: "Which WiFi driver am I using? If not TP-LINK Archer T1U, why not?"
date: 2017-07-20
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-07-20
I am using a Teclast TPad X2 Pro dual booted with Windows 10.

I had help installing the driver for the internal WiFi card - Realtek and at first this worked from cold boot or from re-boot. It now only works from a cold boot. Not agreat problem but as it seems flaky I decided to use a T-LINK USB adapter AC 450 Archer T1U instead.

Following the instructions here:

[https://ubuntuforums.org/showthread.php?t=2359573](https://ubuntuforums.org/showthread.php?t=2359573)

Without any problems and rebooted. I could not get a WiFi connection. I shutdown and booted again. This time I got a connection but don't know which driver is being used.

Judging from dmesg it appears to be:

[ 11.827661] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START

[https://paste.ubuntu.com/25132900/](https://paste.ubuntu.com/25132900/)


As the T1U driver seemed to compile correctly and ended up as suggested without the problems experienced by the original OP, I ask for confirmation that the Realtex driver is being used and if so,can any assistance be given with the T1I driver?

As the Teclast only has two USB ports and one is used for the mouse dongle I invested in a small 4 port USB 3 hub and anticipated using the 'better' T1U in future. I also need to use a dongle which is wider than normal and cannot be used at the same time as the mouse dongle, hence another reason for the hub.

When I did the compile the T1U was not inserted nor was the hub and when I reboot or shutdown as mentioned the hub was not in use.

The T1U worked without any drivers when I bought it because I needed to download files to compile the driver for internal card so I am a bit peeved.

---

### Post by wildmanne39 on 2017-07-20
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by makem2 on 2017-07-20
> **wildmanne39 said:**
> Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

I was unaware that I had not conformed to the post requirements. I had great difficulty in posting anything via Chrome which gave an error. Also Firefox gave an error until I copied and pasted the post in parts.

Result as requested:

[https://pastebin.com/VWSrjQH9](https://pastebin.com/VWSrjQH9)

---

### Post by chili555 on 2017-07-20
The answer to the question, which driver is being used is: both:```
[COLOR="#FF0000"]rtl8xxxu  [/COLOR]            122880  0
mac80211              761856  1 rtl8xxxu
cfg80211              581632  2 [COLOR="#FF0000"]8723bu[/COLOR],mac80211
```However, the one that triggers a connection is the USB:```
wlx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.1.214  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::18d6:7459:44bb:d737/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:69854713 (69.8 MB)  TX bytes:15229581 (15.2 MB)
```wlx followed by a long string of numbers and letters is usually the USB.

The question of which driver *should* be used is more complex. I'd always like to get the internal working, if possible. If it isn't, we could try to troubleshoot it and see if we can persuade it to work.

If you do not want to use the internal, I'd blacklist and unload its driver:```
sudo -i
modprobe -r 8723bu
echo "blacklist 8723bu"  >>  /etc/modprobe.d/blacklist.conf
exit
```I also see a few things in the paste that I think you could tweak to improve performance.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor. Reboot.

---

### Post by makem2 on 2017-07-20
Thank you chili555, 

You assisted me to get the internal WiFi working correctly but as I said it fails on reboot now. I travel out of the UK often and visit many WiFi points so I was worried than the flaky internal might let me down. I have not changed anything since you assisted, except to install the driver for the T1U so some he points you mention have been dealt with. I have changed to channel 6. 

WPA2-Personal AES was in use.

Mode was auto and I have set it to N. (the other option was legacy)

I will blacklist the internal and come back later thank you.

[COLOR=#DD4814][/COLOR]

---

### Post by chili555 on 2017-07-20
> Mode was auto and I have set it to N.I suggest Auto B, G and N. What we are hoping to avoid is setting the router to N and trying to connect with a device that either doesn't do N at all or one that starts at B, negotiates to G and then negotiates to N. It may, failing to find a B starting place, quit entirely.

I look forward to your report.

---

### Post by makem2 on 2017-07-20
My choices are: In 2.4GHz Auto; N; Legacy and in 5GHz; Auto; N; N/AC; Legacy

I have set 2.4GHz back to Auto. In 5GHz I have left it Auto also.

USB dongle AC450 - similar to the internal, I need to shut down and restart to get a connection  which only shows two bars.

---

### Post by chili555 on 2017-07-20
> similar to the internal, I need to shut down and restart to get a connection which only shows two bars.Any clues in the log?```
dmesg | grep rtl
```

---

### Post by makem2 on 2017-07-20
makem@teclast:~$ dmesg | grep rtl
[    3.194926] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    3.194929] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    3.243147] usb 1-3: rtl8723bu_parse_efuse: dumping efuse (0x200 bytes):
[    3.243302] usb 1-3: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[    4.076073] usbcore: registered new interface driver rtl8xxxu
[    4.078698] rtl8xxxu 1-3:1.2 wlx5863561030df: renamed from wlan0
[   20.148183] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[   20.157201] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[  137.138318] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[  252.875465] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[  252.879460] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[  579.132484] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[  748.907644] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[  748.912228] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 1080.172491] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 1196.916891] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[ 1196.921844] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 1371.155976] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 1380.582039] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[ 1380.757325] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
makem@teclast:~$ 

No idea :-(

EDIT: Removed the TP-LINK dongle and still was connected

---

### Post by chili555 on 2017-07-20
> EDIT: Removed the TP-LINK dongle and still was connectedHow is this possible? Did you not correctly blacklist the internal? Is the ethernet still attached? If those two are not true, it is impossible.

Perhaps the Network Manager icon shows a connection, but you can not possibly pass traffic, pull web pages, etc. Please retrace your steps and explain.

---

### Post by makem2 on 2017-07-20
I did:

```

sudo -i
modprobe -r 8723bu
echo "blacklist 8723bu"  >>  /etc/modprobe.d/blacklist.conf
exit
```

I rebooted and replied.

I will do it again. I notice only the internal driver is mentioned in dmesg.

---

### Post by makem2 on 2017-07-20
```

makem@teclast:~$ sudo  -i
[sudo] password for makem: 
root@teclast:~# modprobe -r 8723bu
root@teclast:~# echo "blacklist 8723bu"  >>  /etc/modprobe.d/blacklist.conf
root@teclast:~# exit
logout
makem@teclast:~$ dmesg | grep rtl
[    3.194926] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    3.194929] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    3.243147] usb 1-3: rtl8723bu_parse_efuse: dumping efuse (0x200 bytes):
[    3.243302] usb 1-3: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[    4.076073] usbcore: registered new interface driver rtl8xxxu
[    4.078698] rtl8xxxu 1-3:1.2 wlx5863561030df: renamed from wlan0
[   20.148183] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[   20.157201] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[  137.138318] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[  252.875465] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[  252.879460] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[  579.132484] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[  748.907644] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[  748.912228] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 1080.172491] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 1196.916891] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[ 1196.921844] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 1371.155976] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 1380.582039] usb 1-3: rtl8xxxu_bss_info_changed: HT supported
[ 1380.757325] usb 1-3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
makem@teclast:~$

```

---

### Post by makem2 on 2017-07-20
Rebooted - no connection. Shutdown, restarted, have a connection.

Removed the usb dongle,, opened a new browser and opened a new web page.

[http://paste.ubuntu.com/25135010/](http://paste.ubuntu.com/25135010/)

EDIT: Another reboot - no connection, shutdown, restart to get a connection - without the usb dongle!

The file /etc/modprobe.d/blacklist.conf ends with:

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


#blacklist btusb
blacklist 8723bu
blacklist 8723bu

---

### Post by chili555 on 2017-07-21
I learn something new every day. Sometimes, I learn that I missed crucial details from the original few posts and have been consequently chasing the wrong rabbit. I'm sorry. 

Here is your internal device: > ID 0bda:b720 Realtek Semiconductor Corp.  I learned today that two possibly conflicting drivers claim the device:```
chili@T440p:~$ modinfo rtl8xxxu | grep B720
alias:          usb:v0BDAp[COLOR="#FF0000"]B720[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*

```And also:```
chili@T440p:~$ modinfo Desktop/Forum/rtl8723bu/8723bu.ko | grep B720
alias:          usb:v0BDAp[COLOR="#FF0000"]B720[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*

```That's why when you blacklisted 8723bu, the device still works!!! 

I am not going crazy after all. A bit slow, but not crazy.

I also learned this. Here is your USB dongle:> ID 2357:0105  Nice descriptive name, eh? We learn this about it: [https://wikidevi.com/wiki/TP-LINK_Archer_T1U](https://wikidevi.com/wiki/TP-LINK_Archer_T1U)> WI1 chip1: MediaTek MT7610UHere is how you might install its driver: [https://askubuntu.com/questions/791780/how-do-i-get-tp-link-archer-t1u-usb-wireless-dongle-working](https://askubuntu.com/questions/791780/how-do-i-get-tp-link-archer-t1u-usb-wireless-dongle-working)

It may or may not work in your 4.8 kernel version. 

A bigger question is that is the connection satisfactory just using rtl8xxxu for the internal? Should we instead blacklist rtl8xxxu and remove the 8723bu blacklist and see if the internal works well? Or shall we abandon the internal altogether and concentrate on the USB?

---

### Post by makem2 on 2017-07-21
Thank you for that research.

You beat me to the USB information.
```

makem@teclast:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 258a:6a88  
Bus 001 Device 007: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
makem@teclast:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 258a:6a88  
Bus 001 Device 007: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 013: ID 2357:0105  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
makem@teclast:~$

```

As I said, I am concerned about the fact that the internal does not get a connection on reboot which means something is wrong and whilst I travel I may not get a connection. The internal will always be there and sort of works. The external should be better if it can be activated properly. It will also survive updates?

So, I would like to get the external working and use the internal as a fallback. I think we should get the internal working correctly first.

However, I am in your hands as on my own it would take for ever, if ever.

I next travel around Wales, UK, Northwards next Thursday or Friday. (Just returned from Denmark and Sweden) I can use my Galaxy s8 if all else fails in Wales but it will be a good test before I leave the UK again,

---

### Post by makem2 on 2017-07-21
I have blacklisted the [COLOR=#000000]rtl8xxxu and the internal connected after a reboot :)

Shall I use the instruction to install the external driver or do you have any suggestions to make before I start?

EDIT: I have already compiled and installed the TP-LINK driver and will see if I can either remove or black list it before above.

[/COLOR]

---

### Post by makem2 on 2017-07-21
```

makem@teclast:~$ find /lib/modules/$(uname -r)/kernel/drivers/net/wireless -name '*.ko'
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8187/rtl8187.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/btcoexist/btcoexist.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192se/rtl8192se.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723ae/rtl8723ae.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192ee/rtl8192ee.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192de/rtl8192de.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/admtek/adm8211.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/mac80211_hwsim.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwlegacy.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwl4965.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwl3945.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/ipw2x00/ipw2100.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/ipw2x00/libipw.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/ipw2x00/ipw2200.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/rsi/rsi_sdio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/rsi/rsi_91x.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/rsi/rsi_usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco_tmd.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco_plx.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/spectrum_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco_usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco_nortel.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/hostap/hostap_plx.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/hostap/hostap_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/hostap/hostap_pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/hostap/hostap.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/p54/p54spi.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/p54/p54common.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/p54/p54usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intersil/p54/p54pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ray_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/zydas/zd1201.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/zydas/zd1211rw/zd1211rw.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/broadcom/b43legacy/b43legacy.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/8723bu.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/wl3501_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/mediatek/mt7601u/mt7601u.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/mt7610u_sta.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/atmel/atmel_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/atmel/atmel_pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/atmel/at76c50x-usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/atmel/atmel.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ar5523/ar5523.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/wcn36xx/wcn36xx.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/wil6210/wil6210.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas_tf/libertas_tf_usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas_tf/libertas_tf.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas/usb8xxx.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas/libertas_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas/libertas.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas/libertas_spi.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/libertas/libertas_sdio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/mwl8k.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/mwifiex/mwifiex_sdio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/mwifiex/mwifiex.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/mwifiex/mwifiex_usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/marvell/mwifiex/mwifiex_pcie.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/st/cw1200/cw1200_wlan_sdio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/st/cw1200/cw1200_core.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/st/cw1200/cw1200_wlan_spi.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/rndis_wlan.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2400pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt73usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2500pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2500usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt61pci.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/cisco/airo_cs.ko
/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/cisco/airo.ko
makem@teclast:~$ 

```

I believe the TP-LINK external driver is RT2xxxx because the compile instructions mention RT2870STA.dat

---

### Post by chili555 on 2017-07-22
> I have blacklisted the rtl8xxxu and the internal connected after a reboot I assume that you mean that you blacklisted rtl8xxxu and UN-blacklisted 8723bu. Please clarify.  

Was the connection smooth and reliable?> I believe the TP-LINK external driver is RT2xxxx because the compile instructions mention RT2870STA.dat
14 Hours AgoThe driver is this:> /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/mt7610u_sta.koRecall that deviwiki said:> 
WI1 chip1: MediaTek MT7610UIf you blacklist* both* 8723bu and rtl8xxxu, disabling the internal, does the USB work? Does the driver load?```
lsmod | grep mt76
```Is a wireless interface created; wlx-something, perhaps?```
iwconfig
```Does it connect reliably?

---

### Post by makem2 on 2017-07-22
[QUOTE=chili555;13668687]I assume that you mean that you blacklisted rtl8xxxu and UN-blacklisted 8723bu. Please clarify. 

[COLOR=#008000]Yes[/COLOR] 

Stupid forgot to insert the dongle!

Will recommence.

---

### Post by makem2 on 2017-07-22
Stupid!

Forgot to put in the dongle! :(

---

### Post by makem2 on 2017-07-22
> **chili555 said:**
> I assume that you mean that you blacklisted rtl8xxxu and UN-blacklisted 8723bu. Please clarify.  

Was the connection smooth and reliable?The driver is this:Recall that deviwiki said:If you blacklist* both* 8723bu and rtl8xxxu, disabling the internal, does the USB work? Does the driver load?```
lsmod | grep mt76
```Is a wireless interface created; wlx-something, perhaps?```
iwconfig
```Does it connect reliably?

I blacklisted rtl8xxxu and UN-blacklisted 8723bu.

The connection was smooth and reliable.

Blacklist* both* 8723bu and rtl8xxxu, disabling the internal, no connection. (with the dongle inserted!)

---

### Post by makem2 on 2017-07-22
makem@teclast:~$ cd /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/
makem@teclast:/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless$ ls -la
total 73660
drwxr-xr-x 16 root root     4096 Jul 20 23:28 .
drwxr-xr-x 27 root root     4096 Jul  9 15:37 ..
-rw-r--r--  1 root root 36992384 Jul 17 22:45 8723bu.ko
drwxr-xr-x  2 root root     4096 Jul  9 15:37 admtek
drwxr-xr-x 10 root root     4096 Jul  9 15:37 ath
drwxr-xr-x  2 root root     4096 Jul  9 15:37 atmel
drwxr-xr-x  5 root root     4096 Jul  9 15:37 broadcom
drwxr-xr-x  2 root root     4096 Jul  9 15:37 cisco
drwxr-xr-x  5 root root     4096 Jul  9 15:37 intel
drwxr-xr-x  5 root root     4096 Jul  9 15:37 intersil
-rw-r--r--  1 root root    84750 Jun 26 22:33 mac80211_hwsim.ko
drwxr-xr-x  5 root root     4096 Jul  9 15:37 marvell
drwxr-xr-x  3 root root     4096 Jul  9 15:37 mediatek
[COLOR=#ff0000]-rw-r--r--  1 root root 38020456 Jul 20 23:28 mt7610u_sta.ko[/COLOR]
drwxr-xr-x  3 root root     4096 Jul  9 15:37 ralink
-rw-r--r--  1 root root   110166 Jun 26 22:33 ray_cs.ko
drwxr-xr-x  5 root root     4096 Jul  9 15:37 realtek
-rw-r--r--  1 root root    98742 Jun 26 22:33 rndis_wlan.ko
drwxr-xr-x  2 root root     4096 Jul  9 15:37 rsi
drwxr-xr-x  3 root root     4096 Jul  9 15:37 st
-rw-r--r--  1 root root    41766 Jun 26 22:33 wl3501_cs.ko
drwxr-xr-x  3 root root     4096 Jul  9 15:37 zydas
makem@teclast:/lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless$

---

### Post by chili555 on 2017-07-22
> I blacklisted rtl8xxxu and UN-blacklisted 8723bu.

The connection was smooth and reliable.Frankly, that's the way I'd leave it. If, however, you'd prefer the USB, post back and we'll try it.

---

### Post by makem2 on 2017-07-22
I have a 5GHz router and the external dongle can do that so it would be good to use it. If trying it will not breaking what has been achieved of course.

---

### Post by chili555 on 2017-07-22
In recent kernels, such as your 4.8.0-xx, the mt7610u devices are almost (and maybe actually) impossible to get going. You have been warned.

I am nothing if not a willing and somewhat knowledgeable experimenter/nerd/wireless whisperer. Let's give it our best try.

Please also blacklist 8723bu and reboot. Then open a terminal and do:

```
sudo modprobe mt7610u_sta
```

Any errors or warnings? Does the wireless spring to life?```
iwconfig
dmesg | grep -i mt76
```

---

### Post by makem2 on 2017-07-22
iwconfig:

lo no wireless extensions
[COLOR=#000000][FONT=&quot]
dmesg | grep -i mt76

returns blank[/FONT][/COLOR]

---

### Post by chili555 on 2017-07-22
Was the module loaded? ```
lsmod | grep mt76
```Does the module cover your exact device?```
modinfo mt7610u_sta | grep 0105
```If this also returns blank, then try:```
sudo -i
modprobe mt7610u_sta
echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
exit
```Just so you'll know, we are at the mayday grab-your-parachutes stage here. Our available options are getting slim.

---

### Post by makem2 on 2017-07-22
makem@teclast:~$ lsmod | grep mt76
makem@teclast:~$ modinfo mt7610u_sta | grep 0105
makem@teclast:~$ sudo -i
[sudo] password for makem: 
root@teclast:~# modprobe mt7610u_sta 
root@teclast:~# echo "2357 0105" > /sys/bus/usb/drivers/rt2870/new_id
root@teclast:~# exit
logout
makem@teclast:~$ 

Immediately after pressing 'enter' and before typing exit a 'System program problem was detected'.

Rebooted  and received the same error. No wireless connection too.

---

### Post by chili555 on 2017-07-22
Before we give up on that particular version of mt7610u and try something different, let's see if there are any clues in the log:```
cat /var/log/syslog | grep -i -e rt2 -e mt76
```

---

### Post by makem2 on 2017-07-22
> **makem2 said:**
> makem@teclast:~$ lsmod | grep mt76
makem@teclast:~$ modinfo mt7610u_sta | grep 0105
makem@teclast:~$ sudo -i
[sudo] password for makem: 
root@teclast:~# modprobe mt7610u_sta 
[COLOR=#ff0000]root@teclast:~# echo "2357 0105" > /sys/bus/usb/drivers/rt2870/new_id[/COLOR]
root@teclast:~# exit
logout
makem@teclast:~$ 

Immediately after pressing 'enter' and before typing exit a 'System program problem was detected'.

Rebooted  and received the same error. No wireless connection too.

The command in red above did not make a new folder rt2870

I did not have two spaces before and after '>'

```

makem@teclast:~$ sudo -i
[sudo] password for makem: 
root@teclast:~# modprobe mt7610u_sta 
root@teclast:~# echo "2357 0105" > /sys/bus/usb/drivers/rt2870/new_id
root@teclast:~# exit
logout
makem@teclast:~$ cd /sys/bus/usb/drivers
makem@teclast:/sys/bus/usb/drivers$ ls -la
total 0
drwxr-xr-x 9 root root 0 Jul 22 22:17 .
drwxr-xr-x 4 root root 0 Jul 22 22:17 ..
drwxr-xr-x 2 root root 0 Jul 22 22:17 btusb
drwxr-xr-x 2 root root 0 Jul 22 22:17 hub
drwxr-xr-x 2 root root 0 Jul 22 22:17 rtsx_usb
drwxr-xr-x 2 root root 0 Jul 22 22:17 usb
drwxr-xr-x 2 root root 0 Jul 22 22:17 usbfs
drwxr-xr-x 2 root root 0 Jul 22 22:17 usbhid
drwxr-xr-x 2 root root 0 Jul 22 22:17 uvcvideo
makem@teclast:/sys/bus/usb/drivers$

```

```

makem@teclast:/$ sudo -i
[sudo] password for makem: 
root@teclast:~# modprobe mt7610u_sta
root@teclast:~# echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
root@teclast:~# exit
logout
makem@teclast:/$ cd /sys/bus/usb/drivers
makem@teclast:/sys/bus/usb/drivers$ ls -la
total 0
drwxr-xr-x 12 root root 0 Jul 22 22:29 .
drwxr-xr-x  4 root root 0 Jul 22 22:20 ..
drwxr-xr-x  2 root root 0 Jul 22 22:20 btusb
drwxr-xr-x  2 root root 0 Jul 22 22:20 hub
drwxr-xr-x  2 root root 0 Jul 22 22:29 rt2870
drwxr-xr-x  2 root root 0 Jul 22 22:20 rtsx_usb
drwxr-xr-x  2 root root 0 Jul 22 22:21 uas
drwxr-xr-x  2 root root 0 Jul 22 22:25 usb
drwxr-xr-x  2 root root 0 Jul 22 22:20 usbfs
drwxr-xr-x  2 root root 0 Jul 22 22:20 usbhid
drwxr-xr-x  2 root root 0 Jul 22 22:21 usb-storage
drwxr-xr-x  2 root root 0 Jul 22 22:20 uvcvideo
makem@teclast:/sys/bus/usb/drivers$

```
However, still no wireless connection.

After a reboot the folder rt2870 was no longer present! As had usb-storage.

---

### Post by chili555 on 2017-07-22
> The command in red above did not make a new folder rt2870
It is not supposed to; modprobe is. But the second try it did??> drwxr-xr-x  2 root root 0 Jul 22 22:29 rt2870Again, any clues in the log?```
cat /var/log/syslog | grep -i -e rt2 -e mt76
```> I did not have two spaces before and after '>'The commands are equivalent. It just improves readability somewhat. It helps some new users understand that we are not asking for:```
echo "2357 0105">/sys/bus/usb/drivers/rt2870/new_id
```That is, with NO spaces. That is not equivalent and will fail.

---

### Post by makem2 on 2017-07-22
> **chili555 said:**
> It is not supposed to; modprobe is. But the second try it did??

[COLOR=#008000]Yes as I showed, it did, but then it disappeared after a re-boot.
[/COLOR]
Again, any clues in the log?```
cat /var/log/syslog | grep -i -e rt2 -e mt76


I am getting an error, "Sorry Ubuntu 16.04 has experienced an internal error" this time.

[CODE]
makem@teclast:~$ cat /var/log/syslog | grep -i -e rt2 -e mt76
Jul 22 18:30:04 teclast kernel: [ 3725.639640] rtusb init rt2870 --->
Jul 22 18:30:04 teclast kernel: [ 3725.640079] usbcore: registered new interface driver rt2870
Jul 22 21:29:17 teclast kernel: [   49.288397] rtusb init rt2870 --->
Jul 22 21:29:17 teclast kernel: [   49.288438] usbcore: registered new interface driver rt2870
Jul 22 22:06:36 teclast kernel: [  198.933835] rtusb init rt2870 --->
Jul 22 22:06:36 teclast kernel: [  198.934360] usbcore: registered new interface driver rt2870
Jul 22 22:09:08 teclast kernel: [  351.195897] rt2870_disconnect(): CMD_RTPRIV_IOCTL_STA_SIOCSIWAP(00:00:00:00:00:00)
Jul 22 22:29:28 teclast kernel: [  737.122881] rtusb init rt2870 --->
Jul 22 22:29:28 teclast kernel: [  737.123247] usbcore: registered new interface driver rt2870
makem@teclast:~$

```

---

### Post by makem2 on 2017-07-22
Second time around, this time to see what the result is before rebooting.

```

makem@teclast:~$ sudo -i
[sudo] password for makem: 
root@teclast:~# modprobe mt7610u_sta
root@teclast:~# echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
root@teclast:~# exit
logout
makem@teclast:~$ cd /sys/bus/usb/drivers
makem@teclast:/sys/bus/usb/drivers$ ls -la
total 0
drwxr-xr-x 12 root root 0 Jul 22 23:52 .
drwxr-xr-x  4 root root 0 Jul 22 23:52 ..
drwxr-xr-x  2 root root 0 Jul 22 23:52 btusb
drwxr-xr-x  2 root root 0 Jul 22 23:52 hub
drwxr-xr-x  2 root root 0 Jul 23 00:05 rt2870
drwxr-xr-x  2 root root 0 Jul 22 23:52 rtsx_usb
drwxr-xr-x  2 root root 0 Jul 22 23:57 uas
drwxr-xr-x  2 root root 0 Jul 22 23:52 usb
drwxr-xr-x  2 root root 0 Jul 22 23:52 usbfs
drwxr-xr-x  2 root root 0 Jul 22 23:52 usbhid
drwxr-xr-x  2 root root 0 Jul 22 23:57 usb-storage
drwxr-xr-x  2 root root 0 Jul 22 23:52 uvcvideo
makem@teclast:/sys/bus/usb/drivers$


makem@teclast:/sys/bus/usb/drivers$ cd rt2870
makem@teclast:/sys/bus/usb/drivers/rt2870$ ls -la
total 0
drwxr-xr-x  2 root root    0 Jul 23 00:05 .
drwxr-xr-x 12 root root    0 Jul 23 00:05 ..
--w-------  1 root root 4096 Jul 23 00:08 bind
lrwxrwxrwx  1 root root    0 Jul 23 00:08 module -> ../../../../module/mt7610u_sta
-rw-r--r--  1 root root 4096 Jul 23 00:05 new_id
-rw-r--r--  1 root root 4096 Jul 23 00:08 remove_id
--w-------  1 root root 4096 Jul 23 00:05 uevent
--w-------  1 root root 4096 Jul 23 00:08 unbind
makem@teclast:/sys/bus/usb/drivers/rt2870$

```

---

### Post by chili555 on 2017-07-23
It is pretty clear that the driver that you installed isn't going to work properly. Let's remove it.

I assume, since I linked this as a possible way to get the device working, that this is the method you used to install it. [https://askubuntu.com/questions/791780/how-do-i-get-tp-link-archer-t1u-usb-wireless-dongle-working](https://askubuntu.com/questions/791780/how-do-i-get-tp-link-archer-t1u-usb-wireless-dongle-working) If not, stop and tell us what you did instead.

If so, remove it:```
sudo apt purge mt7610u-dkms
```Just to be sure it all went well, reboot and then do:```
sudo modprobe mt7610u_sta
```We expect it will show fatal not found. If so, all is well and please continue:```
sudo apt update
sudo apt install git
git clone https://github.com/ulli-kroll/mt7610u.git
cd mt7610u
make
sudo insmod mt7610u 
```This driver includes your usb.id, so the new_id step is not needed.

Fingers crossed!

---

### Post by makem2 on 2017-07-23
Post #1:

[https://ubuntuforums.org/showthread.php?t=2359573](https://ubuntuforums.org/showthread.php?t=2359573)

[https://paste.ubuntu.com/25132900/](https://paste.ubuntu.com/25132900/)

As I said, I am still getting system errors when rebooting since the last attempts. Is it possible to remove the last attempts we made?

---

### Post by chili555 on 2017-07-23
Your dmesg paste is frustrating. It shows clearly that rtl8xxxu is loaded; i.e. not blacklisted so as to prevent a probable conflict with the USB driver.

It is difficult for me to try to help you and troubleshoot when what I assumed was done isn't. I thought you wanted to concentrate on the USB and that we were blacklisting *both *drivers for the internal. First:> I blacklisted rtl8xxxu and UN-blacklisted 8723bu.But you prefer the USB:> I have a 5GHz router and the external dongle can do that so it would be good to use it. And then:> Please also blacklist 8723bu and reboot.I don't understand...

I'm confused.

---

### Post by makem2 on 2017-07-23
I am sorry if I have caused confusion. I should have just answered simply rather than refer to my first post. I will do so after this and hope we can carry on from that point.

The dmesg url and  method url I posted were taken from [COLOR=#ff0000]Post #1 of this thread[/COLOR]. Therefore the dmesg relates only to my very first attempt following those instructions. If it is not of value, please ignore it.

I have followed exactly what you suggest from your first post in this thread and have completed everything.

---

### Post by makem2 on 2017-07-23
> **chili555 said:**
> It is pretty clear that the driver that you installed isn't going to work properly. Let's remove it.

I assume, since I linked this as a possible way to get the device working, that this is the method you used to install it. [https://askubuntu.com/questions/791780/how-do-i-get-tp-link-archer-t1u-usb-wireless-dongle-working](https://askubuntu.com/questions/791780/how-do-i-get-tp-link-archer-t1u-usb-wireless-dongle-working) If not, stop and tell us what you did instead.

Fingers crossed!

No, that is not the method I used. I have stopped.

This is the method I used: 

[https://ubuntuforums.org/showthread.php?t=2359573](https://ubuntuforums.org/showthread.php?t=2359573)

EDIT: I would like to remove settings made in and following Post #27 as they seem to cause startup errors.

---

### Post by praseodym on 2017-07-23
There is another driver available (if not already tried...):

[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

---

### Post by chili555 on 2017-07-23
> EDIT: I would like to remove settings made in and following Post #27 as they seem to cause startup errors.
That's exactly what we're going to do. We will then download and try another driver. When we get ready to load the new driver, you must blacklist BOTH rtl8xxxu AND 8723bu so that the drivers for the internal device don't conflict. If you want to then use the internal, blacklist the mt7610u driver, again, so they don't conflict. What we do not want is random changes that suddenly appear and about which the experts watching this thread (there are at least three that I know of) have to guess about.

First, we remove the old not-working driver, reversing the process you say you followed:```
cd ~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master
sudo make uninstall
sudo modprobe -r mt7610u_sta
```Now, let's try a possibly better driver:```
sudo apt update
sudo apt install git
git clone https://github.com/ulli-kroll/mt7610u.git
cd mt7610u
make
sudo cp firmware/*  /lib/firmware

```Make certain that your blacklists are in order and reboot. Next:```
cd mt7610u
sudo insmod mt7610u
```Now run and post:```
iwconfig
dmesg | grep -e rt2 -e mt76
```

---

### Post by chili555 on 2017-07-23
> **praseodym said:**
> There is another driver available (if not already tried...):

[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)Thanks! That will be a possible future trial.

---

### Post by makem2 on 2017-07-23
> **chili555 said:**
> That's exactly what we're going to do. We will then download and try another driver. When we get ready to load the new driver, you must blacklist BOTH rtl8xxxu AND 8723bu so that the drivers for the internal device don't conflict. If you want to then use the internal, blacklist the mt7610u driver, again, so they don't conflict. What we do not want is random changes that suddenly appear and about which the experts watching this thread (there are at least three that I know of) have to guess about.


My current blacklist:
blacklist 8723bu
blacklist 8723bu
blacklist rtl8xxxu

Before I continue with your removal instructions I need to query, "If you want to then use the internal, blacklist the mt7610u driver, again, so they don't conflict."

We are about to remove that driver? If so why would I later need to blacklist it to use it? [COLOR=#008000]Because you refer to the new driver (same name)! Sorry, I now understand.[/COLOR]

EDIT: One further thing, should the usb dongle be in or out during the next steps?

---

### Post by makem2 on 2017-07-23
Following on after checking the blacklist:

```

makem@teclast:~$ cd ~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master
makem@teclast:~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master$ sudo make uninstall
[sudo] password for makem: 
make -C /home/makem/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux -f Makefile.6 uninstall
make[1]: Entering directory '/home/makem/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux'
rm -rf /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/mt7610u_sta.ko
/sbin/depmod -a 4.8.0-58-generic
make[1]: Leaving directory '/home/makem/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux'
makem@teclast:~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master$ sudo modprobe -r mt7610u_sta
modprobe: FATAL: Module mt7610u_sta not found.
makem@teclast:~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master$

```

Error?? Strange, Post @22 shows: [COLOR=#FF0000]-rw-r--r-- 1 root root 38020456 Jul 20 23:28 mt7610u_sta.ko[/COLOR]

---

### Post by chili555 on 2017-07-23
That's fine so far. Please continue.

Dongle out until the last insmod step, please.

---

### Post by makem2 on 2017-07-23
> **chili555 said:**
> That's exactly what we're going to do. We will then download and try another driver. When we get ready to load the new driver, you must blacklist BOTH rtl8xxxu AND 8723bu so that the drivers for the internal device don't conflict. If you want to then use the internal, blacklist the mt7610u driver, again, so they don't conflict. What we do not want is random changes that suddenly appear and about which the experts watching this thread (there are at least three that I know of) have to guess about.

First, we remove the old not-working driver, reversing the process you say you followed:```
cd ~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master
sudo make uninstall
sudo modprobe -r mt7610u_sta
```Now, let's try a possibly better driver:```
sudo apt update
sudo apt install git
git clone https://github.com/ulli-kroll/mt7610u.git
cd mt7610u
make
sudo cp firmware/*  /lib/firmware

```Make certain that your blacklists are in order and reboot. Next:```
cd mt7610u
sudo insmod mt7610u
```Now run and post:```
iwconfig
dmesg | grep -e rt2 -e mt76
```


```

makem@teclast:~$ cd mt7610u
makem@teclast:~/mt7610u$ sudo insmod mt7610u
[sudo] password for makem: 
insmod: ERROR: could not load module mt7610u: No such file or directory
makem@teclast:~/mt7610u$ iwconfig
lo        no wireless extensions.


makem@teclast:~/mt7610u$ dmesg | grep -e rt2 -e mt76
makem@teclast:~/mt7610u$ 

```

The installed git was the latest and the make completed and copied without error.

---

### Post by chili555 on 2017-07-23
> makem@teclast:~$ cd mt7610u
makem@teclast:~/mt7610u$ sudo insmod mt7610u
[sudo] password for makem: 
insmod: ERROR: could not load module mt7610u: No such file or directory
makem@teclast:~/mt7610u$ iwconfig
lo        no wireless extensions.


makem@teclast:~/mt7610u$ dmesg | grep -e rt2 -e mt76
makem@teclast:~/mt7610u$Oops! My mistake and my apologies. Please see my correction:

Make certain that your blacklists are in order and reboot. Next:
```
cd mt7610u
sudo insmod mt7610u[COLOR="#FF0000"].ko[/COLOR]
```
Now run and post:
```
iwconfig
dmesg | grep -e rt2 -e mt76
```For all you driver dawgs out there, mt7610u implies a module in the usual location; /lib/modules/etc.  mt7610u[COLOR="#FF0000"].ko [/COLOR] implies a module in the current directory; in this case, mt7610u which we just cd into.

---

### Post by makem2 on 2017-07-24
```

makem@teclast:~$ sudo nano /etc/modprobe.d/blacklist.conf
makem@teclast:~$ cd mt7610u
makem@teclast:~/mt7610u$ sudo insmod mt7610u.ko
insmod: ERROR: could not insert module mt7610u.ko: Unknown symbol in module
makem@teclast:~/mt7610u$ iwconfig
lo        no wireless extensions.


makem@teclast:~/mt7610u$ dmesg | grep -e rt2 -e mt76
[  223.672528] mt7610u: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[  223.672621] mt7610u: Unknown symbol cfg80211_scan_done (err 0)
[  223.672703] mt7610u: Unknown symbol regulatory_hint (err 0)
[  223.672781] mt7610u: Unknown symbol wiphy_new_nm (err 0)
[  223.672818] mt7610u: Unknown symbol cfg80211_connect_bss (err 0)
[  223.672872] mt7610u: Unknown symbol wiphy_register (err 0)
[  223.672965] mt7610u: Unknown symbol wiphy_unregister (err 0)
[  223.673067] mt7610u: Unknown symbol ieee80211_channel_to_frequency (err 0)
[  223.673136] mt7610u: Unknown symbol ieee80211_frequency_to_channel (err 0)
[  223.673171] mt7610u: Unknown symbol wiphy_free (err 0)
makem@teclast:~/mt7610u$

```

---

### Post by makem2 on 2017-07-24
I am still getting System problem program detected errors with report or cancel options. I do not report as it may have been caused by the changes made recently.

---

### Post by chili555 on 2017-07-24
Now we know that the last driver won't work, either. Let's remove it:```
cd mt7610u
make clean
```There isn't any 'sudo make install' available in this or any other mt7610u driver I've ever seen, so it is not installed anywhere on your system aside from this directory.

The driver that my colleague praseodym has linked clearly says:> Operating System
Linux (Kernel version 2.6~3.16)That means that it will never compile on your 4.8.0-xx kernel.

In fact, having tried many different versions of mt7610u from github and other sources, I am unaware of *any *driver that compiles successfully and then works; that is, connects and pulls web pages, emails, etc.

I regret that I can offer no better solution aside from getting a fully supported plug-and-play device.

---

### Post by makem2 on 2017-07-24
Thank you for all your effort to assist me. It is much appreciated. I will revert to the internal.

I only purchased this dongle because I needed one to get the internal working and it was just my luck it was the only one left on the shelf. Now I know why!

Will removing this driver fix the errors I am getting or is that a different matter? They only cropped up during our attempts to get the dongle working but it could be coincidence of course.

---

### Post by chili555 on 2017-07-24
> Will removing this driver fix the errors I am getting or is that a different matter?It is likely a different matter. As I said, the driver isn't actually installed in your system in /lib/modules/whatever. It only exists in the mt7610u directory. As long as you don't insmod it, it is not effective in any way, either for good or for bad.

This post may be helpful in finding a better supported dongle: [https://ubuntuforums.org/showthread.php?t=2359573&p=13639455#post13639455](https://ubuntuforums.org/showthread.php?t=2359573&p=13639455#post13639455) It is interesting that it is near the end of another long thread about mt7610u!

As for your errors, you might check the log:```
cat /var/log/syslog | grep -i -e warn -e error
```If you see an obvious error, Google it along with 'Ubuntu' and a solution may be found. If is not wireless or networking, I suggest that you ask here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by makem2 on 2017-07-24
Thank you, have a great day.

---

