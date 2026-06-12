---
title: "Wifi indicator has disappeared from top of the screen after installation of 14.04"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by mahboob218 on 2014-08-24
Hi, 

     i have installed Ubuntu 14.04, my Model is " Dell Inspiron 4050, First wifi indicator was there at the top of screen with battery , 

but suddenly it went off and never come back there , i tried to search for solution but all in vain. 

now is there any one who can help to find solution for this problem ?

 thanks in advance

---

### Post by Ksiencha on 2014-08-24
First run this in your terminal:
```

wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script

```

This will create *wireless-info.txt* or *wireless-info.txt.tar.gz* file in your home directory. You can either attach it and post it here or just copy/paste here the content of it and wrap with code tags.

---

### Post by mahboob218 on 2014-08-24
[SIZE=6]Hi[/SIZE] [[COLOR=#000000]Ksiencha[/COLOR]]("http://ubuntuforums.org/member.php?u=1921425")[COLOR=#000000] 

        first of all thanks for help , and second as you asked for the file with the name " wifi info txt " is here attached with the reply , 

i hope you can solve this problem , i little worried about it , 


thank you very much, [/COLOR][ATTACH]255802[/ATTACH]


here is the text i found in that file.



########## wireless info START ##########


Report from: 24 Aug 2014 22:15 PKT +0500


Script from: 17 Aug 2014 02:46 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0502]
	Kernel driver in use: r8169


09:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD] [1028:0205]
	Kernel driver in use: ath9k


##### lsusb #####


Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643e Microdia 
Bus 001 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 007: ID 12d1:14db Huawei Technologies Co., Ltd. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
ath3k                  13318  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
bluetooth             391196  23 bnep,ath3k,btusb,rfcomm
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 dell_wmi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr <MAC addr eth1>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c6ff:fe60:6460/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1369556 (1.3 MB)  TX bytes:406067 (406.0 KB)


##### iwconfig #####


eth0      no wireless extensions.


eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            cdc_ether
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth1>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: /hfp/C01885338CC2_0026692BBAB2 ---------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            ofono
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


eth0      no frequency information.


eth1      no frequency information.


lo        no frequency information.


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


##### iwlist scan #####


eth0      Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


##### module infos #####


[ath3k]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512


##### module parameters #####


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0


##### /etc/modules #####


lp
rtc


##### blacklists #####


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


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[   13.223614] ath: phy0: ASPM enabled: 0x42
[   13.223618] ath: EEPROM regdomain: 0x60
[   13.223619] ath: EEPROM indicates we should expect a direct regpair map
[   13.223622] ath: Country alpha2 being used: 00
[   13.223624] ath: Regpair used: 0x60
[   16.995710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.401213] cdc_ether 1-1.1:1.0 eth1: register 'cdc_ether' at usb-0000:00:1a.0-1.1, CDC Ethernet Device, <MAC addr eth1>


########## wireless info END ############

---

### Post by varunendra on 2014-08-25
mahboob218,

First of all, and quite importantly, please use 'Code' tags to wrap the output parts in your post like Ksiencha asked you -
> or just copy/paste here the content of it and wrap with code tags

 Please follow the "Use Code Tags" link in my signature below to see why, and how.

About the problem, the first one is that your wireless is simply NOT enabled from Network Manager -
```
0: phy0: Wireless LAN
**Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
Hard blocked: no
....
....
[main]
NetworkingEnabled=true
**WirelessEnabled=[COLOR="#FF0000"]false[/COLOR]**
WWANEnabled=true
WimaxEnabled=true

```
The first part highlighted in RED shows that your wifi is soft-blocked, and the second part below confirms that it is blocked from Network Manager.

Solution - In Network Manager menu (the nm-applet icon beside the speaker icon on the top-right corner of the screen), click on "Enable Wireless" option to put a tick mark beside it. A tick mark means it is enabled from there.

If it still has problems, please confirm first that you did above correctly by posting the outputs of -
```
rfkill list
cat /var/lib/NetworkManager/NetworkManager.conf
```
..in **Code Tags** this time please. :)

---

### Post by mahboob218 on 2014-08-29
i don't know what to do, and i don't understand code " varundra " so i decided to install my operating system again, 

now it is running like an horse/.  :D
 
[URL="http://ubuntuforums.org/member.php?u=1043629"]
[/URL]

---

### Post by varunendra on 2014-08-29
Great! Please mark the thread as [SOLVED] using "Thread Tools" link above the first post.

---

