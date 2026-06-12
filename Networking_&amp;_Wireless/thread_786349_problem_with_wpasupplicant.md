---
title: "problem with wpasupplicant"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by jreubens on 2008-05-08
Hi all, 

help this newbie.... i have ubuntu gusty 7.10, i am very new to linux, i used this tutorial to setup my wireless card [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a2669e6253e78a64b66ed1c27e42c1bb8ae43416](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a2669e6253e78a64b66ed1c27e42c1bb8ae43416)

everything works fines, my network manager works... perfect.

unfortunately for my thesis i have to do some experiment on wpasupplicant, when i used wpasupplicant that comes with ubuntu 7.10 (because when i tired to apt-get install, it says wpa_supplicant already installed, so i cannot mention my own config options while building like CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_NDISWRAPPER=y, CONFIG_CTRL_IFACE=y). when i tired to use wpa_supplicant, it gives the following error.

Here is my wpa_supplicant conf file
network={
ssid="testnet"
scan_ssid=1
key_mgmt=WPA-PSK
psk=e7172cf145d9cb8d57bf0a06e2317c80e980a8311e7ac807315703299413debb
}

here is my lswh -C network info
 *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:98:e4:2a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

here is my output for wpa_supplicant
Trying to associate with 00:1e:e5:43:7f:2b (SSID='testnet' freq=2437 MHz)
Association request to the driver failed
Authentication with 00:1e:e5:43:7f:2b timed out.

here is my demsg (some useful info that may give u hint to help me)
[   17.604000] ndiswrapper version 1.45 loaded (smp=yes)
[   17.720000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   17.720000] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   17.720000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 22
[   17.720000] PCI: Setting latency timer of device 0000:03:00.0 to 64

[   17.728000] ndiswrapper: using IRQ 22
[   18.080000] wlan0: ethernet device 00:1a:73:98:e4:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4312.5.conf
[   18.080000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


Thank you for helping me out... (forget to mention, i disabled the network manager by following a tutorial where it is mention

quote
Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

, nd i dont know how to enable it either, if i make wpasupplicant to work then i can make a fresh install of gusty)

Thank you for taking time for me,

Regards,
Jreubens

---

### Post by kevdog on 2008-05-08
See link and then post back with questions:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by jreubens on 2008-05-08
i have tried your post before for that i have problem with the ctrl_interface=/var/run/wpa_supplicant line, so i deleted it then i get this messaged

i have checked with the unecrypted and wep encryption... everything works fine

do you need more info? on which file?

i am really fustrated..... help me plz

/jreubens

---

### Post by jreubens on 2008-05-08
hi,

i have tired you tutorial, now i get different error mesg

jennianand@jennianand:~$ sudo wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     74 65 73 74 6e 65 74                              testnet         
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='testnet'
Initializing interface (2) 'wlan0'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1a:73:98:e4:2a
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 926 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:19:bb:fe:41:13 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
2: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:19:bb:fe:41:13 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 926 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:19:bb:fe:41:13 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
2: 00:19:bb:fe:41:13 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 704 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
2: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 926 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:19:bb:fe:41:13 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:60:df:f7:c9 ssid='default' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1e:e5:43:7f:2b ssid='testnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
2: 00:19:bb:fe:41:13 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:18:39:1c:3d:16 ssid='aalto' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
 this repeats, i some of the post u asked to change the conf file i changed still no luck, here is my conf file
network={
ssid="testnet"
proto=WPA
key_mgmt=WPA-PSK
psk=9fa83d52e36a338af93d1cea44a3d885d65822455c5ba2f7efeb6146a0bb3552
}

i dont have scan_sssid, ap_scan lines...but still i get error, my router is configured to use wpa-psk with tkip as the encryption algorithm.

i am jus wondering i have nothing in /etc/default/wpa_supplicant file, because when i made my broadcom card work with ndiswrapper i have written enabled=0 to /etc/default/wpa_supplicant file. does i ahve add more, plz help me....

i have to set this up for my thesis, i disabled the network manager also.. i dont know what to do now

Thank you for your time,

/jenni

---

### Post by kevdog on 2008-05-08
The output you provided keeps telling me you access point cant be found.  If you do a iwlist scan, does your access point show up?

What driver/chipset combination are you using for your card?  Some strange errors like WPA not working but WEP working are actually due to some driver problems.

---

