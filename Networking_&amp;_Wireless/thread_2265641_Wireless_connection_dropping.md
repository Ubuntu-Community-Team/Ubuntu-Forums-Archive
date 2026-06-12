---
title: "Wireless connection dropping"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by kevin149 on 2015-02-16
Good evening all, I have recently only just installed Ubuntu on my system and repleaced WIndows as I hate Microsoft :)
I have been reading a lot on these forums recently and tried many f the sugestions and although I have only just installed it I think I'am starting t pick up things as I go along.

I have a problem with my wireless that is causing me a headache and I cannot seem to fix, my connection will be fine for around 15-30 minutes then all of a sudden a it will just stop and if I have a web page up it will just keep loading and then not work. I always have to restart the laptop to get it woring again, I have tried a few suggestions on here and none at minute seem to have helped. 
Would anoyne be able to help and I will do my best to provide any information you need!

Thank you in advance for any help :)

---

### Post by jeremy31 on 2015-02-16
We could use a little more info that could be provided by reading [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and running the wireless script and posting the results using code tags [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) if it is text to preserve the format

---

### Post by kevin149 on 2015-02-16
OKay thank you for quick reply, I think this is the details you require. 

```
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380c]
    Kernel driver in use: r8169

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 5986:055d Acer, Inc 
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630669  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr f0:76:1c:21:68:7f  
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f276:1cff:fe21:687f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:456541 (456.5 KB)  TX bytes:140661 (140.6 KB)

wlan0     Link encap:Ethernet  HWaddr c0:38:96:01:cc:6d  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c238:96ff:fe01:cc6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1867865 (1.8 MB)  TX bytes:375347 (375.3 KB)


##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHub5-3S9M"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:91:F9:45:47:E8   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-18 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################


NetworkManager Tool

State: connected (global)

- Device: wlan0  [BTHub5-3S9M] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        C0:38:96:01:CC:6D

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKY22366:        Infra, C0:3E:0F:32:6D:C5, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SKY17209:        Infra, 00:25:69:0F:43:3A, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    TALKTALK7F7B46:  Infra, 68:A0:F6:7F:7B:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTHub4-SRMG:     Infra, CC:33:BB:48:16:D6, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *BTHub5-3S9M:    Infra, 00:91:F9:45:47:E8, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BTHomeHub2-84ZN: Infra, 00:24:17:A7:57:1B, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTWiFi:          Infra, 02:24:17:A7:57:1C, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    BTWiFi-with-FON: Infra, 02:24:17:A7:57:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 27

  IPv4 Settings:
    Address:         192.168.1.73
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:76:1C:21:68:7F

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.74
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



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
```

---

### Post by jeremy31 on 2015-02-16
See [http://ubuntuforums.org/showthread.php?t=2245164&p=13222964#post13222964](http://ubuntuforums.org/showthread.php?t=2245164&p=13222964#post13222964) as it should work for your wifi chipset too

---

### Post by kevin149 on 2015-02-16
> **jeremy31 said:**
> See [http://ubuntuforums.org/showthread.php?t=2245164&p=13222964#post13222964](http://ubuntuforums.org/showthread.php?t=2245164&p=13222964#post13222964) as it should work for your wifi chipset too

Thank you I will give that a try just now, can I just ask about the "After a kernel update you will need to" section. Do I just enter that as well? Or does that involve something else. Sorry if I'm asking too many questions here just wanting to make sure I understand correctly?
Thanks

---

### Post by jeremy31 on 2015-02-16
Wait until the issues happen again before running the part about after a kernel update.  Right now you have 3.13.0-45 and you can check the kernel with ```
uname -r
``` in terminal

---

### Post by kevin149 on 2015-02-16
> **jeremy31 said:**
> Wait until the issues happen again before running the part about after a kernel update.  Right now you have 3.13.0-45 and you can check the kernel with ```
uname -r
``` in terminal

Updated it now so hopefully it will work and there wil be no more wireless issues!

Thank you

---

### Post by kevin149 on 2015-02-16
Damm never lasted long as it has laready dropped again since installing the information. 
Is there anything else I can do?

---

### Post by jeremy31 on 2015-02-16
Run ```
./wireless_script
``` in terminal and post the new info as the last one was cut short

---

### Post by kevin149 on 2015-02-17
> **jeremy31 said:**
> Run ```
./wireless_script
``` in terminal and post the new info as the last one was cut short

Hi, is this correct?


```
########## wireless info START ##########

Report from: 17 Feb 2015 15:06 GMT +0000

Booted last: 17 Feb 2015 15:01 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380c]
    Kernel driver in use: r8169

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 5986:055d Acer, Inc 
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             125361  0 
rtl8723_common         23914  1 rtl8723be
btcoexist              54531  1 rtl8723be
rtl_pci                39740  1 rtl8723be
rtlwifi               105368  2 rtl_pci,rtl8723be
mac80211              572528  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              505345  2 mac80211,rtlwifi
compat                 15137  5 cfg80211,mac80211,btcoexist,rtlwifi,rtl8723be
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f276:1cff:fe21:687f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1730073 (1.7 MB)  TX bytes:145282 (145.2 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c238:96ff:fe01:cc6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1075230 (1.0 MB)  TX bytes:187315 (187.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHub5-3S9M"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'BTHub5-3S9M' [AN4]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [BTHub5-3S9M] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKY22366:        Infra, <MAC 'SKY22366' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SKY17209:        Infra, <MAC 'SKY17209' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA
    BTHub4-SRMG:     Infra, <MAC 'BTHub4-SRMG' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    *BTHub5-3S9M:    Infra, <MAC 'BTHub5-3S9M' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA2
    TALKTALK7F7B46:  Infra, <MAC 'TALKTALK7F7B46' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.73
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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
    Address:         192.168.1.74
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

[[/etc/NetworkManager/system-connections/BTHub5-3S9M]] (600 root)
[connection] id=BTHub5-3S9M | type=802-11-wireless
[802-11-wireless] ssid=BTHub5-3S9M | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-45-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     5D113E08097276ABF2EF3C6
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)

parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.13.0-45-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
vermagic:       3.13.0-45-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.13.0-45-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7C41A4007A6094567567091
depends:        mac80211,rtlwifi
vermagic:       3.13.0-45-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.13.0-45-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     44A5F49216740D2B9E16476
depends:        mac80211,compat,cfg80211
vermagic:       3.13.0-45-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
srcversion:     2E526B72B7E114629FB8EA1
depends:        cfg80211,compat
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     07F008E2B6279F6399E5939
depends:        compat
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.358276] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   12.365986] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.366551] rtlwifi: rtlwifi: wireless switch is on
[   16.330490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   18.108049] wlan0: authenticate with <MAC 'BTHub5-3S9M' [AN4]>
[   18.108054] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[   18.140192] wlan0: send auth to <MAC 'BTHub5-3S9M' [AN4]> (try 1/3)
[   18.144463] wlan0: authenticated
[   18.146555] wlan0: associate with <MAC 'BTHub5-3S9M' [AN4]> (try 1/3)
[   18.153949] wlan0: RX AssocResp from <MAC 'BTHub5-3S9M' [AN4]> (capab=0x431 status=0 aid=2)
[   18.154805] wlan0: associated
[   18.154844] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-02-17
Can you change your wifi router to channel 3 or 13 and try?

---

### Post by kevin149 on 2015-02-17
> **jeremy31 said:**
> Can you change your wifi router to channel 3 or 13 and try?

Okay I have changed to channel 3.

---

### Post by kevin149 on 2015-02-17
Channel 3 done the same so now giving 13 a go.

---

### Post by jeremy31 on 2015-02-17
If it still has issues```
echo "options rtl8723be fwlps=0 swlps=0 swenc=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```and reboot

---

### Post by kevin149 on 2015-02-17
> **jeremy31 said:**
> If it still has issues```
echo "options rtl8723be fwlps=0 swlps=0 swenc=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```and reboot

Okay I'm now trying this as changing the wireless channels has sadly not worked and the connection still drops out.
Thanks again for all these suggestions I'm just hoping one will work!

---

### Post by kevin149 on 2015-02-19
> **jeremy31 said:**
> If it still has issues```
echo "options rtl8723be fwlps=0 swlps=0 swenc=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```and reboot

This has helped as I have only had one dropout since and it is much more stable. Not that I'm very technical but I'm just wondering what exactly this has done?

---

### Post by jeremy31 on 2015-02-19
Shut off power save and turned on software encryption

---

### Post by kevin149 on 2015-02-19
> **jeremy31 said:**
> Shut off power save and turned on software encryption

Thats great well it's still working great!

---

