---
title: "Finally got Netgear WNDA3100v2 wireless adapter working, but connection keeps droppin"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by Deedlebag on 2014-10-25
[COLOR=#000000][FONT=verdana](Sorry for the typo in the title)
So after days of searching, I was finally able to get my Netgear wireless adapter (WNDA3100v2) functioning on my setup (Ubuntu 14.04) by following this guide: [/FONT][/COLOR][http://av3ngr.wikispaces.com/Netgear+WNDA3100v2+USB](http://av3ngr.wikispaces.com/Netgear+WNDA3100v2+USB)

[COLOR=#000000][FONT=verdana]And the adapter seems to work. At first, it would keep trying to connect to my secure connection and ask for the WPA2 key (which I made sure was correct) and just keep doing that. But then, someone suggested disabling the power management setting on the adapter, so once I did that it was finally able to hold a connection.
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]But now, my issue is my adapter seems to lose connection after about a minute. And by lose connection, I mean the internet plain stops working. The adapter says its connected, but I can't get to any websites or use other internet services. When I plug in the device, and connect to my signal, it works perfectly. But then gets progressively slower and slower, until the internet doesn't work at all. I've searched all over Google to find help for my problem, but the solutions I've tried didn't work for me. Below are the results of running the wireless-script:
[/FONT][/COLOR]```



########## wireless info START ##########


Report from: 25 Oct 2014 09:28 PDT -0700


Booted last: 25 Oct 2014 09:25 PDT -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c326 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              484040  0 
ndiswrapper           283985  0 
wmi                    19177  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.42.0.13  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fec8:1897/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:465878 (465.8 KB)  TX bytes:267026 (267.0 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c604:15ff:fe73:63c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419287 (419.2 KB)  TX bytes:128376 (128.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"NM5NK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'NM5NK' [AC1]>   
          Bit Rate=52 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:27  Invalid misc:28397   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.42.0.1       0.0.0.0         UG    0      0        0 eth0
10.42.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [NM5NK] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           52 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    23RN4:           Infra, <MAC '23RN4' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    5AK50:           Infra, <MAC '5AK50' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WEP
    YH9LC:           Infra, <MAC 'YH9LC' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WEP
    0EXG4:           Infra, <MAC '0EXG4' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    *NM5NK:          Infra, <MAC 'NM5NK' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    AWY66:           Infra, <MAC 'AWY66' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WEP


  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.42.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         10.42.0.1


    DNS:             10.42.0.1


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


[[/etc/NetworkManager/system-connections/NM5NK]] (600 root)
[connection] id=NM5NK | type=802-11-wireless
[802-11-wireless] ssid=NM5NK | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NM5NK' [AC1]>
                    ESSID:"NM5NK"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'YH9LC' [AC2]>
                    ESSID:"YH9LC"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: <MAC '5AK50' [AC3]>
                    ESSID:"5AK50"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: <MAC '0EXG4' [AC4]>
                    ESSID:"0EXG4"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: <MAC 'AWY66' [AC5]>
                    ESSID:"AWY66"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-37-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc
ndiswrapper


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
options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   76.437609] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   76.981361] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   76.983669] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   77.072130] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   87.874445] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```[COLOR=#000000][FONT=verdana]

Thanks in advance![/FONT][/COLOR]

---

### Post by jeremy31 on 2014-10-25
The real solution is to find an adapter that doesn't require ndiswrapper as it is difficult to troubleshoot

---

### Post by Deedlebag on 2014-10-26
> **jeremy31 said:**
> The real solution is to find an adapter that doesn't require ndiswrapper as it is difficult to troubleshoot
Well sure, that's a really easy fix but I'd really like to get this adapter to work so I don't have to go buy another.

---

### Post by jeremy31 on 2014-10-26
You might want to use the file Chili555 attached here [http://ubuntuforums.org/showthread.php?t=1964173&p=11867790#post11867790](http://ubuntuforums.org/showthread.php?t=1964173&p=11867790#post11867790) with ndiswrapper
Nevermind, it is likely the one you have

---

### Post by sammiev on 2014-10-26
Glad you have it working but you should be using WPA2 instead of WEP unless you are not worried about security.

---

### Post by Deedlebag on 2014-10-26
> **sammiev said:**
> Glad you have it working but you should be using WPA2 instead of WEP unless you are not worried about security.
That's my mistake, it is actually WPA2.

---

### Post by Christian_Cariaso on 2014-11-20
Hello everyone. I have the same situation here. I got my netgear usb working by following chili555's thread. I was able detect my wifi and i was able to connect and surf the internet once this morning. But when I disconnected it I can't connect to my wifi again. I tried rebooting, turning my wifi on and off  to no avail. I have no knowledge in linux and was only able to do things through forums and threads. Can anyone help please?

---

### Post by derek30 on 2015-03-17
it appears this is a common problem and that it won't be solved anytime soon. (im assuming you've already done so because you havn't replied to your thread in months) but i would suggest buying a more compatable modem as the broadcam chipset doesn't like linux. i have had this problem myself and am going to buy myself a new modem within this week or the next as i have found on [this thread]("http://ubuntuforums.org/showthread.php?t=1888673") that says that both the [netgear wna1100]("http://www.amazon.com/NETGEAR-N150-Wi-Fi-Adapter-WNA1100/dp/B0036R9XRU") and the [TRENDnet TEW-649UB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&cm_re=TrendNet_TEW-649UB-_-33-156-268-_-Product") work with linux (make sure it isn't the TEW-64**8**UB, as said on the above thread). i don't know if 2.4 GHz modems work with 5 GHz routers but lets just hope you have a 2.4 GHz service. there are modems other than that if you don't have a 2.4 GHz router, but you will have to search for it yourself. however i have found these websites that have suggestions/references for modems for linux. 

[http://elinux.org/RPi_USB_Wi-Fi_Adapters](http://elinux.org/RPi_USB_Wi-Fi_Adapters) 

[http://www.htpcbeginner.com/linux-compatible-usb-wireless-adapters-2012/](http://www.htpcbeginner.com/linux-compatible-usb-wireless-adapters-2012/)

[http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html](http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html)

i hope that helps anyone out there that has come across this problem. sadly im sure there is a solution to the 'broadcam' problem but i havn't found one and it seems you would have to trouble shoot it yourself.

---

