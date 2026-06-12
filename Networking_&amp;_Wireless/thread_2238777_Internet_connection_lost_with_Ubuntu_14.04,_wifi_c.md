---
title: "Internet connection lost with Ubuntu 14.04, wifi connection"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by dev-skg on 2014-08-10
Hi,

I installed Ubuntu 14.04 64bit on my second partition alongside Windows in my PC. I am using a NetGear USB Wifi Adapter to connect to my wireless router. I am able to connect seamlessly and browse/download in windows. however, when i use in Ubuntu 14.04, the connection gets lost after few minutes. I am able to see the Wireless icon on the top (which says Connected) but opening a webpage or trying to install any software doesnt work. I looked at various forums and disabled the 802.11 N setting. Doesnt seem to help. Also i installed the latest updates available for Ubuntu 14.04. Can someone please assist?

thanks
Sandesh

---

### Post by dave131 on 2014-08-10
Post back the output of:

lsusb

---

### Post by coffeecat on 2014-08-10
Welcome to the forum. Please have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

You can ignore the first bit since you have already updated your system. Run the wireless script and post the results between [noparse]```
 and 
```[/noparse] tags as explained in the sticky.

---

### Post by dev-skg on 2014-08-10
hi,

please find below output.

```
########## wireless info START ##########


Report from: 10 Aug 2014 19:38 IST +0530


Script from: 04 Aug 2014 18:47 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop #####


Ubuntu


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
	Kernel driver in use: e1000e


##### lsusb #####


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0846:9021 NetGear, Inc. 
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
video                  19476  1 asus_wmi
wmi                    19177  2 mxm_wmi,asus_wmi


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
          Interrupt:20 Memory:f7100000-f7120000 


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::abd:43ff:fe7f:11fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:417853 (417.8 KB)  TX bytes:102513 (102.5 KB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC addr Wireless>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search Home


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [Wireless] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           7 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Wireless:       Infra, <MAC addr Wireless>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
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


lo        no frequency information.


wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #####


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Wireless>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002fb87c4b
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos #####


[rtl8192cu]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     7B1675B5BB89B5DD8E7EBAC
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846pF001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


[rtl8192c_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


##### module parameters #####


[rtl8192cu]
debug: 0
swenc: N


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


# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    0.549258] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.819051] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    8.891379] type=1400 audit(1407679626.852:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=472 comm="apparmor_parser"
[    8.891708] type=1400 audit(1407679626.852:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=472 comm="apparmor_parser"
[    9.110654] rtl8192cu: Chip version 0x11
[    9.144951] rtl8192cu: MAC address: <MAC addr wlan0>
[    9.144952] rtl8192cu: Board Type 0
[    9.145030] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    9.145047] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    9.259865] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.260014] rtlwifi: wireless switch is on
[   10.828792] type=1400 audit(1407679628.784:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=903 comm="apparmor_parser"
[   11.011434] rtl8192cu: MAC auto ON okay!
[   11.021970] rtl8192cu: Tx queue select: 0x05
[   11.377854] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.378011] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.028890] wlan0: authenticate with <MAC addr Wireless>
[   13.050611] wlan0: send auth to <MAC addr Wireless> (try 1/3)
[   13.056928] wlan0: authenticated
[   13.060502] wlan0: associate with <MAC addr Wireless> (try 1/3)
[   13.069116] wlan0: RX AssocResp from <MAC addr Wireless> (capab=0x411 status=0 aid=1)
[   13.069143] wlan0: associated
[   13.069187] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.109714] wlan0: deauthenticating from <MAC addr Wireless> by local choice (reason=2)
[   13.120591] wlan0: authenticate with <MAC addr Wireless>
[   13.131410] wlan0: send auth to <MAC addr Wireless> (try 1/3)
[   13.174006] wlan0: authenticated
[   13.176664] wlan0: associate with <MAC addr Wireless> (try 1/3)
[   13.183107] wlan0: RX AssocResp from <MAC addr Wireless> (capab=0x411 status=0 aid=1)
[   13.183123] wlan0: associated


########## wireless info END ############
```

Meanwhile, i tried the steps in -->

[http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

It seemed to work for some time. But once i put the pc to sleep and then waking up, it doesnt seem to work. I lost the connectivity. Now after 2 restarts, it is still connected for more than 10 minutes. Waiting and watching..

---

### Post by dev-skg on 2014-08-10
Update >> Not making a difference. Lost the connectivity after few minutes.

---

### Post by dave131 on 2014-08-11
I can tell from the usb id what the adapter chipset is, and according to what I read in the debian info it looks like it has the correct driver loaded.  Could you also post back just the name of the Netgear adapter - like a model number? 

I'm a newbie, so I may be wrong here.  Just trying to learn and maybe help along the way.  I know Coffeecat is one of the very knowledgable people here so I'm going to stay on the sidelines learning unless something glaringly simple shows up ;)  Maybe it needs something from the backports?

---

