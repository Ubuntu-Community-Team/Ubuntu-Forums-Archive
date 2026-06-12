---
title: "I have an intermittent Wifi connection.  =("
date: 2016-05-24
forum: Networking &amp; Wireless
---

### Post by james214 on 2016-05-24
Almost every time I'm in a public place -- or even at home -- I get an intermittent Wifi connection on my Ubuntu laptop... while my Android phone connects to the Wifi with no problem whatsoever. (Often times I will see the "Disconnected" message appear on my screen... before it reconnects a minute later). Is there any solution for this? Is there any way to test my Wifi connection to see if it's working properly? (It sure doesn't seem to be!)

Thank you.

---

### Post by jeremy31 on 2016-05-24
James214, please see the wireless script link in my signature and post results

---

### Post by james214 on 2016-05-25
Not sure if I did everything right, but...

```



########## wireless info START ##########


Report from: 25 May 2016 14:47 EDT -0400


Booted last: 25 May 2016 14:39 EDT -0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-59-generic #66~14.04.1-Ubuntu SMP Fri May 13 17:27:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2230]
	Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
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


hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wl                   6369280  0 
cfg80211              532480  1 wl
wmi                    20480  1 hp_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.1.10.217  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: 2601:40d:8001:d500::efa7/128 Scope:Global
          inet6 addr: 2601:40d:8001:d500:70c9:27da:96f:30c5/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 2601:40d:8001:d500:<IP6 'wlan0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10451 errors:0 dropped:0 overruns:0 frame:13573
          TX packets:7595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13371604 (13.3 MB)  TX bytes:911046 (911.0 KB)
          Interrupt:17 


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"Zarape4_2.4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Zarape4_2.4' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.10.1       0.0.0.0         UG    0      0        0 wlan0
10.1.10.0       0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search hsd1.mi.comcast.net


##### network managers ##################


Installed:


	NetworkManager


Running:


root       712     1  0 14:39 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Zarape4_2.4] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           39 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    CBCI-2AB2-2.4:   Infra, <MAC 'CBCI-2AB2-2.4' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Saline Inn Guest:Infra, <MAC 'Saline Inn Guest' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    *Zarape4_2.4:    Infra, <MAC 'Zarape4_2.4' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    Subway_Gateway_859: Infra, <MAC 'Subway_Gateway_859' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    DTMIMID001B:     Infra, <MAC 'DTMIMID001B' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA


  IPv4 Settings:
    Address:         10.1.10.217
    Prefix:          24 (255.255.255.0)
    Gateway:         10.1.10.1


    DNS:             75.75.76.76
    DNS:             75.75.75.75


  IPv6 Settings:
    Address:         2601:40d:8001:d500::efa7
    Prefix:          128
    Gateway:         fe80::7454:7dff:fe92:9837


    Address:         2601:40d:8001:d500:70c9:27da:96f:30c5
    Prefix:          64
    Gateway:         fe80::7454:7dff:fe92:9837


    Address:         2601:40d:8001:d500:<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         fe80::7454:7dff:fe92:9837


    Address:         fe80::<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         fe80::7454:7dff:fe92:9837


    Address:         2601:40d:8001:d500::efa7
    Prefix:          128
    Gateway:         ::


    DNS:             2001:558:feed::2
    DNS:             2001:558:feed::1


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


[[/etc/NetworkManager/system-connections/Zarape4_2.4]] (600 root)
[connection] id=Zarape4_2.4 | type=802-11-wireless
[802-11-wireless] ssid=Zarape4_2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tim Hortons WiFi]] (600 root)
[connection] id=Tim Hortons WiFi | type=802-11-wireless
[802-11-wireless] ssid=Tim Hortons WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Target Guest Wi-Fi]] (600 root)
[connection] id=Target Guest Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=Target Guest Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ATT7572]] (600 root)
[connection] id=ATT7572 | type=802-11-wireless
[802-11-wireless] ssid=ATT7572 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Walmartwifi]] (600 root)
[connection] id=Walmartwifi | type=802-11-wireless
[802-11-wireless] ssid=Walmartwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: America/Toronto (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Zarape4_2.4' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Zarape4_2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Subway_Gateway_859' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Subway_Gateway_859"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Saline Inn Guest' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Saline Inn Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'DTMIMID001B' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"DTMIMID001B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '\00\00\00' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'xfinitywifi' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
          Cell 07 - Address: <MAC 'CBCI-2AB2-2.4' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"CBCI-2AB2-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'xfinitywifi' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago


##### module infos ######################


[wl]
filename:       /lib/modules/3.19.0-59-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.19.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46EBD6732E992614FD7F01B
depends:        
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


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
blacklist bcma


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[  493.943119] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)


########## wireless info END ############


```

---

### Post by praseodym on 2016-05-25
Hi,

change the encryption mode to pure WPA2-AE (CCMP) in your router. You can also try upgrading the driver
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```
Worked without error? Then reboot

---

### Post by james214 on 2016-05-27
Well, it's not my router that's the problem. I get an intermittent connection when using public routers.  Panera Bread... the library... Tim Horton's... everywhere, really. And my phone with Android always connects just fine.

---

### Post by him610 on 2016-05-28
I think your problem is because your country code is set to US instead of CA
Can be corrected...
```
sudo iw reg set CA
```

Make it permanent...
```
sudo nano /etc/default/crda
```
Change the last line to read, ```
REGDOMAIN=CA
```
Review, save, reboot then go to Tim Horton's, better?

---

### Post by james214 on 2016-06-03
Interesting. I live in the U.S., not Canada. But I've noticed my web browser's spell check seems to be set in the Canadian spellings.  I live in Michigan -- everything should be set to U.S.

---

### Post by him610 on 2016-06-03
From your Wireless-Info > Region: America/Toronto (based on set time zone)

I apologize for suggesting for you to set the incorrect country code. Between the line above and your reference to Tim Horton's I wrongly assumed you lived in Canada. In my initial reply, please substitute US for CA (or your correct country code.)

Good luck.

---

### Post by james214 on 2016-06-25
So... is changing the country code really going to fix my intermittent Wifi problem? How does this work exactly?

---

### Post by praseodym on 2016-06-25
Yes, country codes are legally binding, otherwise different numbers of available channels could be used. For the interruption with different routers, try Wicd instead:

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
Deactivate the networkmanager from autostart.

---

