---
title: "Dropped connection, both Broadcom and Realtek cards"
date: 2016-05-26
forum: Networking &amp; Wireless
---

### Post by tparks on 2016-05-26
The wireless connection drops on my HP Stream 11 running Xubuntu 16.04 unless I am close to an AP.

I am currently using a USB wireless adapter with a Realtek RTL8188EUS chip. But I had the sane problem with Ubuntu 16.04 using the onboard Broadcom BCM43142 card.

I am especially baffled by the same issue when using two different cards and drivers.

iwconfig:
wlxec086b0c3f21 IEEE 802.11bgn ESSID:"ATT6YXb2IG" Nickname:"<WIFI@REALTEK>"
          Mode:Managed Frequency:2.452 GHz Access Point: DC:7F:A4:99:73:B6
          Bit Rate:65 Mb/s Sensitivity:0/0
          Retry:off RTS thr:off Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-**** Security mode:open
          Power Management:off
          Link Quality=0/100 Signal level=2/100 Noise level=0/100
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

This is something beyond the drivers, right? How can I fix it?

---

### Post by chili555 on 2016-05-26
> Encryption key:****-****-****-****-****-****-****-**** Security mode:openThis implies that the encryption method is the leaky, insecure WEP. Please change your router immediately to WPA2-AES, sometimes known in routers administration pages as CCMP.

If it still drops, we'll proceed from there.

---

### Post by tparks on 2016-05-26
When I checked my home connection in Network Manager, it indicated WPA and WPA2 Personal. My connection at school, where the dropout occurs, is WPA and WPA 2 Enterprise. The Google Starbucks connection, which also drops out, is insecure.

I have now run the wireless-info script as the forum suggests. I am attaching the output.

Thanks for your help.

---

### Post by chili555 on 2016-05-26
With a working internet connection, please open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
```Next, I recommend that your regulatory domain be set explicitly. Check yours:

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

Detach the USB wireless, reboot and tell us if the internal device is working now.

---

### Post by tparks on 2016-05-27
I installed bcmwl-kernel-source, set the regulatory domain, removed the USB wireless adapter, and rebooted.

The internal Broadcom device allows me to connect at home, near my router. But at school, the behavior is the same as before: I can connect to my university's wireless network, but, when I open a browser, I can't reach a site, and, soon, Network Manager tells me the computer is disconnected. When I originally installed Ubuntu 16.04, it found the Broadcom driver, but the problem then was the same as now. And I have the nearly identical issues with the Realtek RTL8188EUS USB adapter.

I'm posting the latest from the wireless-info script. I appreciate the help.

```

########## wireless info START ##########

Report from: 27 May 2016 16:20 CDT -0500

Booted last: 27 May 2016 00:00 CDT -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
	Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0177 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

wl                   6365184  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              565248  1 wl
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:7816
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95339 (95.3 KB)  TX bytes:96752 (96.7 KB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       664     1  0 16:07 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ATT6YXb2IG 1]] (600 root)
[connection] id=ATT6YXb2IG 1 | type=wifi | permissions=user:tparks:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=ATT6YXb2IG
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LUBisonNet]] (600 root)
[connection] id=LUBisonNet | type=wifi | permissions=user:tparks:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=LUBisonNet
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlp1s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  145.262081] CPU: 0 PID: 414 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-22-generic #40-Ubuntu
[  145.262260]  [<ffffffffc0855955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  145.262336]  [<ffffffffc0854fb0>] wl_event_handler+0x60/0x1d0 [wl]
[  145.262413]  [<ffffffffc0854f50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  172.638047] CPU: 0 PID: 414 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-22-generic #40-Ubuntu
[  172.638168]  [<ffffffffc0855955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  172.638218]  [<ffffffffc0854fb0>] wl_event_handler+0x60/0x1d0 [wl]
[  172.638268]  [<ffffffffc0854f50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  784.684191] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by chili555 on 2016-05-27
Is your router using a fixed channel, 1, 6 or 11 ideally, or is it set to auto select the channel?

[https://ask.fedoraproject.org/en/question/73659/wifi-keeps-dropping/](https://ask.fedoraproject.org/en/question/73659/wifi-keeps-dropping/)> I was having the same problem until I went into the router and changed the channel to a fixed channel. Since then I have not had a drop. Note: the channel would have to be one that others close in proximity to you does not use.This is a significant issue from your log:> [  172.638168]  [<ffffffffc0855955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  172.638218]  [<ffffffffc0854fb0>] wl_event_handler+0x60/0x1d0 [wl]
[  172.638268]  [<ffffffffc0854f50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  784.684191] ERROR @wl_dev_intvar_get : error (-1)

---

### Post by tparks on 2016-05-28
As best I can determine, my ATT router is fixed, currently using channel 9. But I have no problems connecting at home.

The issue is joining networks in places where I don't have control over the routers, as at my university workplace and in cafes. 

Why have I had similar issues with two wireless adapters -- were there problems with both drivers, or is there another issue? As it is, the card is unusable except at home, near the router. 

Again, thanks for your help.

---

### Post by praseodym on 2016-05-28
Try Wicd instead:
```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
You can choose from different templates there (WPA, WPA/WPA2, etc). Networkmanager can be uninstalled then or deactivated from Autostart

---

### Post by tparks on 2016-05-29
I connected at home successfully, and the connection at a local Starbucks was much better. No dropouts, although I noticed that the signal strength would vary. Is that normal?

I was unable to connect at work, likely because I was unsure how to configure the connection. Authentication consistently failed. When I could intermittently connect before with Network Manager, these were the parameters:
WPA & WPA2 Enterprise
Protected EAP (PEAP)
No CA certificate required
MSCHAPv2

wicd lists the encryption as WPA2. When I select WPA2-Enterprise, I am unable to supply an "Anonymous_Identity" because I have none. In Network Manager, I was previously able to check ""No CA certificate required" to avoid having to specify a certificate path.

I appreciate the help.

---

