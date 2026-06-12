---
title: "Ubuntu 14.04.2 LTS; wifi connectiion on one user account, but not another"
date: 2015-06-23
forum: Networking &amp; Wireless
---

### Post by mat91fnd on 2015-06-23
Greetings,


I have Lubuntu (Ubuntu 14.04.2 LTS) hosted on Dell Pentium 4 desktop. We have Comcast ArrisTG862G/CT cable modem, with 802.11 bgn. 
Ethernet (wired) access is no problem.  We recently purchased a USB 2.0 802.11n adapter. One user account has no issue connecting wirelessly.
 The other user account does not even see any WiFi hotspot, including my neighbors'.


I tried installing Network Manager to no avail. Changing router's channel does not affect it either. 


I ran the wireless-info.bash and here is the output.  Thanks for


```
########## wireless info START ##########


Report from: 20 Jun 2015 20:21 PDT -0700


Booted last: 20 Jun 2015 20:02 PDT -0700


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-46-generic #76-Ubuntu SMP Thu Feb 26 18:52:49 UTC 2015 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)
	Subsystem: Dell Device [1028:01c4]
	Kernel driver in use: e100


##### lsusb #############################


Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 279e:024e  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


##### lsmod #############################


cfg80211              409394  0 
r8188eu               755586  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13426975 (13.4 MB)  TX bytes:1003241 (1.0 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:  off   RTS thr:  off   Fragment thr:  off
          Power Management:  off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


root       699     1  0 20:02 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


** (process:2395): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/0: uid 1000 has no permission to perform this operation


** (process:2395): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/1: uid 1000 has no permission to perform this operation


** (process:2395): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceWifi.


** (process:2395): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation


** (process:2395): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8188eu
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    HOME-3802:       Infra, <MAC 'HOME-3802' [AC2]>, Freq 2462 MHz, Rate 14 Mb/s, Strength 57 WPA WPA2
    YoungDevoe:      Infra, <MAC 'YoungDevoe' [AC4]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC1]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 0


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/YoungDevoe]] (600 root)
[connection] id=YoungDevoe | type=802-11-wireless | permissions=user:rht:;
[802-11-wireless] ssid=YoungDevoe | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-3802]] (600 root)
[connection] id=HOME-3802 | type=802-11-wireless | permissions=user:rht:;
[802-11-wireless] ssid=HOME-3802 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'xfinitywifi' [AC1]>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:  off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 02 - Address: <MAC 'HOME-3802' [AC2]>
                    ESSID:"HOME-3802"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:  on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=72/100  
          Cell 03 - Address: <MAC '' [AC3]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:  on
                    Bit Rates:270 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 04 - Address: <MAC 'YoungDevoe' [AC4]>
                    ESSID:"YoungDevoe"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:  on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:  on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        97:3B:F0:F9:5D:4E:E6:29:D1:96:4C:EA:21:CB:01:5A:4D:0C:FD:77
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[r8188eu]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     3E7C2595787C9010733B049
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        97:3B:F0:F9:5D:4E:E6:29:D1:96:4C:EA:21:CB:01:5A:4D:0C:FD:77
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1


##### /etc/modules ######################


lp


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1064 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   13.604233] intel_rng: don't want to disable this in firmware setup, and if
[ 1102.324306] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[ 1103.013076] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)


########## wireless info END ############
```

---

### Post by wildmanne39 on 2015-06-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2015-06-23
Go into network manager top right corner of the screen and click on edit connection then click on your wifi connection and make sure all users can connect to network is checked, refer to screenshots.
Thanks

---

### Post by mat91fnd on 2015-06-24
Thanks for the reminder.

---

### Post by wildmanne39 on 2015-06-24
If your issue is resolved please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by mat91fnd on 2015-06-24
Wild Man,
I can not save the setting ('Save' button is grayed out).  I added the user to adm group, but still has no effect.  Suggestion?

---

### Post by wildmanne39 on 2015-06-24
You do not really want to add anyone to the admin group, you need to be logged on as your user then you should be able to put a check mark by all users can use the network and click save. If not then you may have permissions missed up or configuration files.

---

### Post by mat91fnd on 2015-06-24
Ok.  Looks like I will need to tinker with this a bit.  Thanks, Wild Man.

---

### Post by wildmanne39 on 2015-06-24
Make sure you have all users can use connection checked  then create a new account for this person and that should take care of any configuration issues.

---

### Post by mat91fnd on 2015-07-04
Not sure what turned the "Save" button on, but it allowed me to save.  So selecting "Allow all users to connect" turns wireless connection on the account now.  Yeah, I am happy!  Thanks, Wild Man.

---

### Post by wildmanne39 on 2015-07-05
Glad it is working.
Enjoy!

---

