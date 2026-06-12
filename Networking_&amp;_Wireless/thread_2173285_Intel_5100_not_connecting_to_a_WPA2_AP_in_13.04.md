---
title: "Intel 5100 not connecting to a WPA2 AP in 13.04"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by raubvogel on 2013-09-08
I am running Ubuntu 13.04 in my laptop and have an Intel 5100 card. Ubuntu seems to see it (lspci):

```
 02:00.0 Network controller: Intel Corporation WiFi Link 5100
```

When I try to connect to my wireless network (MyWifi, 802.11g, WPA2), I get the following messages:

From syslog
```
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) starting connection 'MyWifi 1'
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> (wlan3): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3/wireless): access point 'MyWifi 1' has security, but secrets are required.
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> (wlan3): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> (wlan3): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3/wireless): connection 'MyWifi 1' has security, and secrets exist.  No new secrets needed.
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Config: added 'ssid' value 'MyWifi'
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Config: added 'scan_ssid' value '1'
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Config: added 'auth_alg' value 'OPEN'
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Config: added 'psk' value '<omitted>'
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> Config: set interface ap_scan to 1
Sep  8 21:35:21 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep  8 21:35:41 hamster wpa_supplicant[1271]: wlan3: SME: Trying to authenticate with 00:1c:f0:f9:3a:d8 (SSID='MyWifi' freq=2432 MHz)
Sep  8 21:35:41 hamster kernel: [ 3693.132925] wlan3: authenticate with 00:1c:f0:f9:3a:d8
Sep  8 21:35:41 hamster kernel: [ 3693.135800] wlan3: direct probe to 00:1c:f0:f9:3a:d8 (try 1/3)
Sep  8 21:35:41 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  8 21:35:42 hamster kernel: [ 3693.335559] wlan3: direct probe to 00:1c:f0:f9:3a:d8 (try 2/3)
Sep  8 21:35:42 hamster kernel: [ 3693.539169] wlan3: direct probe to 00:1c:f0:f9:3a:d8 (try 3/3)
Sep  8 21:35:42 hamster kernel: [ 3693.742838] wlan3: authentication with 00:1c:f0:f9:3a:d8 timed out
Sep  8 21:35:42 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: authenticating -> disconnected
Sep  8 21:35:42 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep  8 21:35:45 hamster wpa_supplicant[1271]: wlan3: SME: Trying to authenticate with 00:1c:f0:f9:3a:d8 (SSID='MyWifi' freq=2432 MHz)
Sep  8 21:35:45 hamster kernel: [ 3697.179829] wlan3: authenticate with 00:1c:f0:f9:3a:d8
Sep  8 21:35:45 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  8 21:35:45 hamster kernel: [ 3697.185202] wlan3: direct probe to 00:1c:f0:f9:3a:d8 (try 1/3)
Sep  8 21:35:46 hamster kernel: [ 3697.388333] wlan3: direct probe to 00:1c:f0:f9:3a:d8 (try 2/3)
Sep  8 21:35:46 hamster kernel: [ 3697.591967] wlan3: direct probe to 00:1c:f0:f9:3a:d8 (try 3/3)
Sep  8 21:35:46 hamster kernel: [ 3697.795576] wlan3: authentication with 00:1c:f0:f9:3a:d8 timed out
Sep  8 21:35:46 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: authenticating -> disconnected
Sep  8 21:35:46 hamster NetworkManager[1045]: <warn> Activation (wlan3/wireless): association took too long, failing activation.
Sep  8 21:35:46 hamster NetworkManager[1045]: <info> (wlan3): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep  8 21:35:46 hamster NetworkManager[1045]: <warn> Activation (wlan3) failed for connection 'MyWifi 1'
Sep  8 21:35:46 hamster NetworkManager[1045]: <info> (wlan3): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  8 21:35:46 hamster NetworkManager[1045]: <info> (wlan3): deactivating device (reason 'none') [0]
Sep  8 21:35:46 hamster NetworkManager[1045]: <info> (wlan3): supplicant interface state: disconnected -> inactive
```

As you can see from my log, it fails to connect. Why? Why in the end it states it cannot find the SSID 

```
Sep  8 21:35:46 hamster NetworkManager[1045]: <info> (wlan3): device state change: config -> failed (reason 'SSID not found') [50 120 53]
```

even though some 8 lines above it acts like it knows it?

```
Sep  8 21:35:45 hamster wpa_supplicant[1271]: wlan3: SME: Trying to authenticate with 00:1c:f0:f9:3a:d8 (SSID='MyWifi' freq=2432 MHz)
```

I am currently using a usb wireless adapter (on wlan1) to type this; it has no issues connecting to my AP:

```
raub@hamster:~$ iwconfig 
wlan1     IEEE 802.11bgn  ESSID:"MyWifi"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1C:F0:F9:3A:D8   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

wlan3     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
raub@hamster:~$
```

lshw tells me that

```
sudo lshw -class network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan3
       version: 00
       serial: 00:16:ea:52:06:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:f3100000-f3101fff
```

Could my issues be related to the firmware 5.4.A.11 vs 8.83.5.1 as mentioned in [http://askubuntu.com/questions/298097/which-iwlwifi-firmware-for-intel-wifi-link-5100](http://askubuntu.com/questions/298097/which-iwlwifi-firmware-for-intel-wifi-link-5100) ?

---

### Post by chili555 on 2013-09-09
> Could my issues be related to the firmware 5.4.A.11 vs 8.83.5.1 as mentioned in [http://askubuntu.com/questions/29809...wifi-link-5100](http://askubuntu.com/questions/29809...wifi-link-5100) ? No. If you download and extract the linked file, it contains iwlwifi-5000-[COLOR="#FF0000"]1[/COLOR].ucode. Please see:```
modinfo iwlwifi
```> $ modinfo iwlwifi
filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-[COLOR="#FF0000"]5[/COLOR].ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
srcversion:     010E5CFF9BB5A6F9A4CC4EC
<snip>The current iwlwifi driver wants -5, although, in some drivers, there is a tolerance written in so it will accept a version or so above or below the stated version:```
/* Highest firmware API version supported */
#define IWL7260_UCODE_API_MAX 6
#define IWL3160_UCODE_API_MAX 6
```Of course, you are free to try it but I strongly suspect you'll get the 'firmware not found' error and the card won't initiate.

I am more suspicious that you have a conflict because you seem to have two (!) wireless cards and probably, at one time, had a third! Before you troubleshoot further, I'd remove the Realtek or at least blacklist its driver. Both cards use the same cfg80211 and mac80211 pieces and so it's difficult for me to figure out who is helping and who is hurting.

---

### Post by raubvogel on 2013-09-09
Thanks for the reply.  When I first tried to connect, I had just one  wireless device, the 5100.  I added the Realtek so I coulld post the  question. But, let me try it again, this time using the 5100 as the  wireless and ethernet for wired. So, I first turn wireless on in network  manager:

```
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3): bringing up device.
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> WiFi hardware radio set enabled
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> WiFi now enabled by radio killswitch
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3): bringing up device.
Sep  9 19:10:32 hamster kernel: [  589.727372] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Sep  9 19:10:32 hamster kernel: [  589.730534] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
Sep  9 19:10:32 hamster kernel: [  589.870222] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3) supports 5 scan SSIDs
Sep  9 19:10:32 hamster NetworkManager[1011]: <warn> Trying to remove a non-existant call id.
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: starting -> ready
Sep   9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3): device  state change: unavailable -> disconnected (reason  'supplicant-available') [20 30 42]
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: ready -> inactive
Sep  9 19:10:32 hamster NetworkManager[1011]: <info> (wlan3) supports 5 scan SSIDs
```

Then I tried to connect:
> Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) starting connection 'MyWifi 1'
Sep   9 19:10:47 hamster NetworkManager[1011]: <info> (wlan3): device  state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
Sep   9 19:10:47 hamster NetworkManager[1011]: <info> (wlan3): device  state change: prepare -> config (reason 'none') [40 50 0]
Sep  9  19:10:47 hamster NetworkManager[1011]: <info> Activation  (wlan3/wireless): access point 'MyWifi 1' has security, but secrets are  required.
Sep  9 19:10:47 hamster NetworkManager[1011]: <info>  (wlan3): device state change: config -> need-auth (reason 'none') [50  60 0]
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
Sep   9 19:10:47 hamster NetworkManager[1011]: <info> (wlan3): device  state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
Sep   9 19:10:47 hamster NetworkManager[1011]: <info> (wlan3): device  state change: prepare -> config (reason 'none') [40 50 0]
Sep  9  19:10:47 hamster NetworkManager[1011]: <info> Activation  (wlan3/wireless): connection 'MyWifi 1' has security, and secrets exist.   No new secrets needed.
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Config: added 'ssid' value 'MyWifi'
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Config: added 'scan_ssid' value '1'
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Config: added 'auth_alg' value 'OPEN'
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Config: added 'psk' value '<omitted>'
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> Config: set interface ap_scan to 1
Sep  9 19:10:47 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: inactive -> scanning
Sep   9 19:10:51 hamster wpa_supplicant[1411]: wlan3: SME: Trying to  authenticate with 00:02:6f:d0:52:4a (SSID='MyWifi' freq=2462 MHz)
Sep  9 19:10:51 hamster kernel: [  608.318315] wlan3: authenticate with 00:02:6f:d0:52:4a
Sep  9 19:10:51 hamster kernel: [  608.320137] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
Sep  9 19:10:51 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  9 19:10:51 hamster kernel: [  608.521214] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
Sep  9 19:10:51 hamster kernel: [  608.724845] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
Sep  9 19:10:51 hamster kernel: [  608.928450] wlan3: authentication with 00:02:6f:d0:52:4a timed out
Sep   9 19:10:51 hamster NetworkManager[1011]: <info> (wlan3):  supplicant interface state: authenticating -> disconnected
Sep  9 19:10:51 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep  9 19:10:55 hamster kernel: [  612.370160] wlan3: authenticate with 00:02:6f:d0:52:4a
Sep   9 19:10:55 hamster wpa_supplicant[1411]: wlan3: SME: Trying to  authenticate with 00:02:6f:d0:52:4a (SSID='MyWifi' freq=2462 MHz)
Sep  9 19:10:55 hamster kernel: [  612.373291] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
Sep  9 19:10:55 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  9 19:10:55 hamster kernel: [  612.573971] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
Sep  9 19:10:55 hamster kernel: [  612.777609] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
Sep  9 19:10:55 hamster kernel: [  612.981242] wlan3: authentication with 00:02:6f:d0:52:4a timed out
Sep   9 19:10:55 hamster NetworkManager[1011]: <info> (wlan3):  supplicant interface state: authenticating -> disconnected
Sep  9 19:10:55 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep   9 19:10:59 hamster wpa_supplicant[1411]: wlan3: SME: Trying to  authenticate with 00:02:6f:d0:52:4a (SSID='MyWifi' freq=2462 MHz)
Sep  9 19:10:59 hamster kernel: [  616.459170] wlan3: authenticate with 00:02:6f:d0:52:4a
Sep  9 19:10:59 hamster kernel: [  616.460939] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
Sep  9 19:10:59 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  9 19:10:59 hamster kernel: [  616.662670] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
Sep  9 19:10:59 hamster kernel: [  616.866308] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
Sep  9 19:10:59 hamster kernel: [  617.069937] wlan3: authentication with 00:02:6f:d0:52:4a timed out
Sep   9 19:10:59 hamster NetworkManager[1011]: <info> (wlan3):  supplicant interface state: authenticating -> disconnected
Sep  9 19:11:00 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep   9 19:11:03 hamster wpa_supplicant[1411]: wlan3: SME: Trying to  authenticate with 00:02:6f:d0:52:4a (SSID='MyWifi' freq=2462 MHz)
Sep  9 19:11:03 hamster kernel: [  620.527820] wlan3: authenticate with 00:02:6f:d0:52:4a
Sep  9 19:11:03 hamster kernel: [  620.529709] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
Sep  9 19:11:03 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  9 19:11:03 hamster kernel: [  620.731469] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
Sep  9 19:11:03 hamster kernel: [  620.935011] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
Sep  9 19:11:04 hamster kernel: [  621.138666] wlan3: authentication with 00:02:6f:d0:52:4a timed out
Sep   9 19:11:04 hamster NetworkManager[1011]: <info> (wlan3):  supplicant interface state: authenticating -> disconnected
Sep  9 19:11:04 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep   9 19:11:07 hamster wpa_supplicant[1411]: wlan3: SME: Trying to  authenticate with 00:02:6f:d0:52:4a (SSID='MyWifi' freq=2462 MHz)
Sep  9 19:11:07 hamster kernel: [  624.600618] wlan3: authenticate with 00:02:6f:d0:52:4a
Sep  9 19:11:07 hamster kernel: [  624.602391] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
Sep  9 19:11:07 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  9 19:11:07 hamster kernel: [  624.804134] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
Sep  9 19:11:07 hamster kernel: [  625.007757] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
Sep  9 19:11:08 hamster kernel: [  625.211395] wlan3: authentication with 00:02:6f:d0:52:4a timed out
Sep   9 19:11:08 hamster NetworkManager[1011]: <info> (wlan3):  supplicant interface state: authenticating -> disconnected
Sep  9 19:11:08 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep   9 19:11:11 hamster wpa_supplicant[1411]: wlan3: SME: Trying to  authenticate with 00:02:6f:d0:52:4a (SSID='MyWifi' freq=2462 MHz)
Sep  9 19:11:11 hamster kernel: [  628.725659] wlan3: authenticate with 00:02:6f:d0:52:4a
Sep  9 19:11:11 hamster kernel: [  628.727479] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
Sep  9 19:11:11 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> authenticating
Sep  9 19:11:11 hamster kernel: [  628.928731] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
Sep  9 19:11:12 hamster kernel: [  629.132389] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
Sep  9 19:11:12 hamster kernel: [  629.336029] wlan3: authentication with 00:02:6f:d0:52:4a timed out
Sep   9 19:11:12 hamster NetworkManager[1011]: <info> (wlan3):  supplicant interface state: authenticating -> disconnected
Sep  9 19:11:12 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Sep   9 19:11:12 hamster NetworkManager[1011]: <warn> Activation  (wlan3/wireless): association took too long, failing activation.
Sep   9 19:11:12 hamster NetworkManager[1011]: <info> (wlan3): device  state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep  9 19:11:12 hamster NetworkManager[1011]: <warn> Activation (wlan3) failed for connection 'MyWifi 1'
Sep   9 19:11:12 hamster NetworkManager[1011]: <info> (wlan3): device  state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  9 19:11:12 hamster NetworkManager[1011]: <info> (wlan3): deactivating device (reason 'none') [0]
Sep  9 19:11:12 hamster NetworkManager[1011]: <info> (wlan3): supplicant interface state: scanning -> disconnected
Sep   9 19:11:12 hamster NetworkManager[1011]: <warn> Couldn't  disconnect supplicant interface: This interface is not connected.
  

About which version of iwlwifi-5000-?.ucode, all I care is for the one  that works. ;) If -5 works, great. If not, I guess I will need to  install the older versions.

---

### Post by chili555 on 2013-09-10
>     If -5 works, great. If not, I guess I will need to install the older versions. I fail to understand how or why you think this is a firmware issue, especially since the link *you provided* says:> In order to correct the situation I downloaded the iwlwifi-5000-ucode-5.4.A.11.tar.gz which contains a file iwlwifi-5000-1.ucode. I also removed existing /lib/firmware/iwlwifi* files (e.g. iwlwifi-5000-5.ucode) and copied the new iwlwifi-5000-1.ucode in the firmware directory

```
sudo mv /lib/firmware/*iwlwifi* ~/keep_iwlwif
sudo cp iwlwifi-5000-1.ucode /lib/firmware
```

After rebooting sudo lshw -class network displayed the firmware=5.4.1.16 which seemed good to me but the dmesg displayed following iwlwifi errors.

```
[   14.196502] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-5.ucode' failed.
[   14.200629] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-4.ucode' failed.
[   14.204814] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-3.ucode' failed.
[   14.253843] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-2.ucode' failed.
```

I decided to add the iwlwifi-5000-5.ucode back to /lib/firmware and rebooted. After reboot I was back in where I started, sudo lshw -class network displayed again the firmware=8.83.5.1 and no dmesg errors for iwlwifi. Why on earth would you think that taking the same steps that were proven unsuccessful would now be successful for you? 

Please reboot with the Realtek disconnected and try to connect. If you fail to do so, run:```
dmesg
```Paste the entire result here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by raubvogel on 2013-09-11
Here it is [http://paste.ubuntu.com/6094027/](http://paste.ubuntu.com/6094027/)

---

### Post by chili555 on 2013-09-11
Oh, boy! > [   91.528991] wlan3: authentication with 00:02:6f:d0:52:4a timed out
[   93.533559] iwlwifi 0000:02:00.0: [COLOR="#FF0000"]fail to flush all tx fifo queues[/COLOR]
[   96.846895] wlan3: authenticate with 00:02:6f:d0:52:4a
[   96.848671] wlan3: direct probe to 00:02:6f:d0:52:4a (try 1/3)
[   97.051084] wlan3: direct probe to 00:02:6f:d0:52:4a (try 2/3)
[   97.254740] wlan3: direct probe to 00:02:6f:d0:52:4a (try 3/3)
[   97.458378] wlan3: authentication with 00:02:6f:d0:52:4a timed outI suggest you try:```
sudo -i
echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf
modprobe -r iwldvm
modprobe -r iwlwifi
modprobe iwlwifi
exit
```It may take a reboot. Any improvement?

---

### Post by raubvogel on 2013-09-11
Besides now having two "options iwlwifi 11n_disable=1" lines in /etc/modprobe.d/iwlwifi.conf, I am afraid not: [http://paste.ubuntu.com/6094551/](http://paste.ubuntu.com/6094551/)

---

### Post by chili555 on 2013-09-12
> **raubvogel said:**
> Besides now having two "options iwlwifi 11n_disable=1" lines in /etc/modprobe.d/iwlwifi.conf, I am afraid not: [http://paste.ubuntu.com/6094551/](http://paste.ubuntu.com/6094551/)Oops! Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the last two lines to:```
options iwlwifi 11n_disable=1 5ghz_disable=1
```Proofread, save and close gedit. Now unload and reload:```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Any improvement?

---

### Post by raubvogel on 2013-09-12
I am afraid not; still getting the *fail to flush all tx fifo queues* error message: [http://paste.ubuntu.com/6097251/](http://paste.ubuntu.com/6097251/)

Just to be on the safe side, I did reboot. You can understand if I feel rather confused. It does feel like something else is going on and I am missing it... :confused:

In any case, thanks for all the help on this issue!

---

### Post by chili555 on 2013-09-12
Have you tried resetting your router to disable N speeds?

---

### Post by raubvogel on 2013-09-16
Yeah, still no dice.  Swapped it with an Atheros card (AR9287) and it seems to be working. Still, I would like to find out what's the deal with the 5100...  I guess it might have to wait until I put the second minipci socket in the laptop.

---

