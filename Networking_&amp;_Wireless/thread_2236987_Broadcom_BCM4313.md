---
title: "Broadcom BCM4313"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by nhuthaotran on 2014-07-30
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux Bi-Inspiron-N4030 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
13:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Dell Device [1028:0466]
    Kernel driver in use: atl1c

##### lsusb #####

Bus 002 Device 003: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:6488 Microdia 
Bus 001 Device 010: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 009: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 008: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search domain.name

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Khanh Son:       Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    kissty_shop:     Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WPA
    Thanh phong:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    NAM:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    HienHanhlau3:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    Home:            Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA
    Hien Hanh:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Happy Zone 2:    Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WEP
    Domino:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2
    Tuankiet2:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TranHoangBaoNam: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    Happy Zone:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Cuong:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    DUC THUAN - TO:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Hao Nam 2:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    linksys1:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    73 LLQ:          Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA2
    thanhhong:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    PHOI:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    nhivnm:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    KISSTYSHOP:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA
    Dong Nhi:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2

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

##### iwlist #####

Aquiring of root rights failed.

##### iwlist channel #####

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### modules #####

lp

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   13.490025] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.495061] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.546779] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.623388] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  325.392603] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  325.392773] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  325.392878] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  329.205761] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  329.205793] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  335.205929] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  335.205958] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  341.207155] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  341.207186] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  347.209113] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  347.209150] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  353.210120] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  353.210150] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  359.213983] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  359.214014] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  365.213840] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  365.213871] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  371.214705] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  371.214737] ERROR @wl_cfg80211_get_station : Wrong Mac address
[ 1042.853832] ERROR @wl_dev_intvar_get : error (-1)
[ 1042.853841] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1329.737558] ERROR @wl_dev_intvar_get : error (-1)
[ 1329.737563] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1546.272704] ERROR @wl_dev_intvar_get : error (-1)
[ 1546.272709] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1590.469494] ERROR @wl_dev_intvar_get : error (-1)
[ 1590.469499] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2010.357470] ERROR @wl_dev_intvar_get : error (-1)
[ 2010.357476] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2057.812542] ERROR @wl_dev_intvar_get : error (-1)
[ 2057.812549] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2215.677764] ERROR @wl_dev_intvar_get : error (-1)
[ 2215.677773] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 4693.032825] ERROR @wl_dev_intvar_get : error (-1)
[ 4693.032830] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############
```


Could somebody please help me?

I am running ubun 14.04.

I cannot connect to the wifi network provided by my router. But my laptop works just fine with the wifi at other places.

When I connect to wifi networks at my home, the symbol on the upper right corner looks like the symbol of "wifi-connected lying in a computer screen". 

(Sorry for my bad English)

Please help me.

---

### Post by bapoumba on 2014-07-30
Moved to its own thread.

---

### Post by varunendra on 2014-07-30
Welcome to Ubuntu Forums nhuthaotran! :)

With respect to this -
> **nhuthaotran said:**
> ```
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
```

Please open a terminal (Ctrl-Alt-T) and install the firmware for the native driver that we wifi troubleshooters believe is better for your card -
```
sudo apt-get install linux-firmware-nonfree
```
Then purge the current "wl" driver which we think can be problematic with the card you have -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and see if the wireless is working any better. If not, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) . Please note that it is a slightly different script than the one you already used above, so please read the instructions carefully.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

And have you manually saved any settings in the Network Manager? I'm concerned about those "Wrong MAC address" errors in the dmesg part of the script.

---

### Post by nhuthaotran on 2014-07-30
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Bi-Inspiron-N4030 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
Memory : 3834 MB
Uptime : 17:13:20 up 10 min,  2 users,  load average: 0,56, 0,34, 0,20


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
13:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Dell Device [1028:0466]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:6488 Microdia 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface            Soft blocked  Hard blocked
0: phy0: Wireless LAN          no            no
1: brcmwl-0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl
wmi                    18673  1 dell_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | atl1c  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | wl     | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    nhivnm:          Infra, <MAC C-01 nhivnm>, Freq 2427 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    Thanh phong:     Infra, <MAC C-06 Thanh phong>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Khanh Son:       Infra, <MAC C-04 Khanh Son>, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    kissty_shop:     Infra, <MAC C-10 kissty_shop>, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WPA
    HienHanhlau3:    Infra, <MAC C-NA HienHanhlau3 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Tuankiet2:       Infra, <MAC C-12 Tuankiet2>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Home:            Infra, <MAC C-09 Home>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    Hien Hanh:       Infra, <MAC C-08 Hien Hanh>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    PHOI:            Infra, <MAC C-NA PHOI 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Happy Zone 2:    Infra, <MAC C-02 Happy Zone 2>, Freq 2427 MHz, Rate 54 Mb/s, Strength 42 WEP
    NAM:             Infra, <MAC C-13 NAM>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Happy Zone:      Infra, <MAC C-05 Happy Zone>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Cuong:           Infra, <MAC C-NA Cuong 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    73 LLQ:          Infra, <MAC C-07 73 LLQ>, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Domino:          Infra, <MAC C-03 Domino>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA2
    DUC THUAN - TO:  Infra, <MAC C-NA DUC THUAN - TO 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Linksys2.4:      Infra, <MAC C-NA Linksys2.4 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Mr_Siro:         Infra, <MAC C-NA Mr_Siro 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    NgoFamily:       Infra, <MAC C-NA NgoFamily 1>, Freq 2432 MHz, Rate 54 Mb/s, Strength 15 WPA2
    TranHoangBaoNam: Infra, <MAC C-NA TranHoangBaoNam 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA
    MrSiro2:         Infra, <MAC C-NA MrSiro2 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WPA
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Ash                  : ssid=Ash | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Domino               : ssid=Domino | permissions=user:guest-930k0E:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Domino 1             : ssid=Domino | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
DUC THUAN - TO       : ssid=DUC THUAN - TO | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Happy Zone 2         : ssid=Happy Zone 2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
hcmus-viber-public   : ssid=hcmus-viber-public | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TranHoangBaoNam      : ssid=TranHoangBaoNam | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search domain.name


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.467/1.468/1.470/0.038 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.027/0.033/0.039/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : vi_VN)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     26 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 nhivnm>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"nhivnm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Happy Zone 2>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Happy Zone 2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
          Cell 03 - Address: <MAC C-03 Domino>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Domino"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Khanh Son>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Khanh Son"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Happy Zone>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Happy Zone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Thanh phong>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Thanh phong"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 73 LLQ>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"73 LLQ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 Hien Hanh>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Hien Hanh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 Home>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 kissty_shop>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"kissty_shop"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 dung>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"dung"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Tuankiet2>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Tuankiet2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 NAM>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NAM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[dell_wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[wl]
filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=8e2c0745-0b06-404a-8287-47f0313b2272 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.913147] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.913461] audit: initializing netlink socket (disabled)
[   13.618131] wmi: Mapper loaded
[   13.701113] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.704146] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.759611] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.851467] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   16.277270] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  604.861511] ERROR @wl_dev_intvar_get : error (-1)
[  604.861519] ERROR @wl_cfg80211_get_tx_power : error (-1)

    ======== Done ========
```


I don't know if this is relevant, but I set the MAC address filter for my wifi connection.

I added the MAC address of my laptop and I can use the wifi with no problem in Win7.

Thank you.

---

### Post by varunendra on 2014-07-30
> **nhuthaotran said:**
> ```
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: **[COLOR="#FF0000"]wl[/COLOR]**
```

The "wl" driver is still there. Did you follow the instructions to purge it? Please do it now. This kind of problem usually doesn't need more than two-three posts. Please read the broadcom sticky in this forum section.

The MAC filter may cause problems in some cases, but for now, please just do as recommended about the driver. We'll address other issues later if required.

---

### Post by nhuthaotran on 2014-07-30
Wow, it is working just fine now. :p

THANK YOU VERY MUCH FOR HELPING ME OUT.

---

### Post by varunendra on 2014-07-30
Glad it worked as expected. :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. It helps others by indicating that the thread contains a possible solution to the problem mentioned in the title.

---

