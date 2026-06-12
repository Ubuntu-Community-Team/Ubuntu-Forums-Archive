---
title: "Ubuntu 12.4 problem with Dell Computers 3521"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by sinawy on 2013-10-20
[SIZE=4][COLOR=#ff0000]Good evening Community members and experts valued[/COLOR][/SIZE]

[SIZE=4][COLOR=#0000cd]I have a problem in Ubuntu 12.4 operating system components and two Dell 3521 on the following [/COLOR][/SIZE][SIZE=4][COLOR=#0000cd]link[/COLOR][/SIZE]

[URL="http://www.dell.com/support/drivers/eg/en/19/ServiceTag/4GXXCW1"][SIZE=3]http://www.dell.com/support/drivers/eg/en/19/ServiceTag/4GXXCW1[/SIZE]
[/URL][SIZE=4][COLOR=#0000cd]
Where I suffer from a severe slow wireless Internet

I'm tired of searching in many locations, behold, I am with you now to find solutions

What do I do?
[/COLOR][/SIZE][B][I][SIZE=5][COLOR=#ff0000]
Thank you for your interest[/COLOR][/SIZE][/I][/B][B][I][SIZE=5][COLOR=#ff0000]
Sinawy[/COLOR][/SIZE][/I][/B]

---

### Post by sinawy on 2013-10-20
[I][COLOR=#ff0000][SIZE=4][B]Where technical solutions Ubuntu?
I'm waiting for solutions
????????????????
[/B][/SIZE][/COLOR][/I]

---

### Post by wildmanne39 on 2013-10-20
Hi, first please use normal fonts when posting and second we are all volunteers in different time zones and you are only allowed to bump your post once every twenty four hours.

copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by sinawy on 2013-10-21
First, thank you for your interest and help me

Secondly, I've done the first step which put the code in the terminal and file appeared to me wireless-info

This is all the information from a wireless-info.txt
```

*************** info trace ***************

***** uname -a *****

Linux sinawy 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:05b8]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Dell Device [1028:0209]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1d57:0008  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e004 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 064e:8132 Suyin Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"hoor"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1264  Invalid misc:18   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath9k                 151796  0 
mac80211              630977  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              422432  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
ath3k                  12968  0 
bluetooth             247165  25 bnep,rfcomm,ath3k,btusb
cfg80211              525326  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [hoor] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TE-Data:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA
    *hoor:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA

  IPv4 Settings:
    Address:         
    Prefix:          24 (            )
    Gateway:       

    DNS:            
    DNS:             

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#NetworkManager#auto wlan0
#NetworkManager#iface wlan0 inet dhcp
#NetworkManager#    wpa-ssid fingerprint
#NetworkManager#    wpa-psk  (null)

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"hoor"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005f4b2a769
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0004686F6F72
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050002097A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706414C20010D10
                    IE: Unknown: DD1E00904C330C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"TE-Data"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c51782e45
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000754452D44617461
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000067A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706454720010D10
                    IE: Unknown: DD1E00904C336C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     74064173F9189761845D970
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     083DD7A079F4041AE50FFC4
depends:        ath
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     E2D00DC65DDBF27B324FEED
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.520965] ath: phy0: ASPM enabled: 0x43
[   12.520969] ath: EEPROM regdomain: 0x60
[   12.520970] ath: EEPROM indicates we should expect a direct regpair map
[   12.520972] ath: Country alpha2 being used: 00
[   12.520973] ath: Regpair used: 0x60
[   18.917229] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.920248] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.296501] wlan0: authenticate with <MAC address removed>
[   22.306746] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.308804] wlan0: authenticated
[   22.311710] wlan0: associate with <MAC address removed> (try 1/3)
[   22.315776] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   22.315829] wlan0: associated
[   22.315839] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   98.422791] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   99.679381] wlan0: authenticate with <MAC address removed>
[   99.690198] wlan0: send auth to <MAC address removed> (try 1/3)
[   99.692282] wlan0: authenticated
[   99.694543] wlan0: associate with <MAC address removed> (try 1/3)
[   99.698559] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   99.698625] wlan0: associated
[  105.669800] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  106.785693] wlan0: authenticate with <MAC address removed>
[  106.796450] wlan0: send auth to <MAC address removed> (try 1/3)
[  106.798543] wlan0: authenticated
[  106.800806] wlan0: associate with <MAC address removed> (try 1/3)
[  106.804800] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  106.804850] wlan0: associated

****************** done ******************


```
 

I hope to find a final solution to this problem because I am really tired and I hope that does not leave the world of Ubuntu

Finally, thank you for your attention
With sincere wishes for success and progress to make the world of Ubuntu is the first
[COLOR=#ff0000]
Your friend
Sinawy
[/COLOR]
Thank While waiting for the final solution

---

### Post by wildmanne39 on 2013-10-21
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Change your encryption in your router to just wpa2 AES only if you have that option.

Get rid of TKIP.

Change the channel to 1 or 11.
Also > ***** interfaces ***** should only have the following in the file, did you remove network manger?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
Thanks

---

