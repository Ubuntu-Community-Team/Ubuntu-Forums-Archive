---
title: "Unstable wifi connection on HP 625 after 14.04 upgrade"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by serbriang on 2014-07-03
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]After I upgraded my laptop to Ubuntu 14.04, the wifi connection worked perfectly, as it always has with Ubuntu. However, about two weeks ago the connection became really unstable. The connection frequently drops, fails to connect or is simply very slow. The results of the wifi script are as as follows: 

[/COLOR]```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux brian-HP-625-ubuntu 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1475]
    Kernel driver in use: r8169
06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: wl


##### lsusb #####


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:0403 Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl


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


wlan0     IEEE 802.11abg  ESSID:"TDC-F534"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search home


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [TDC-F534] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    lindegade241salth: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    TDC-9285:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *TDC-F534:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    yousee:          Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.14
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


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"TDC-F534"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00085444432D46353334
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 07064E4120010D14
                    IE: Unknown: DD7F0050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F59311102100035444431023000C486F6D65426F782D5644534C102400043132333410420004353637381054000800060050F20400011011000C486F6D65426F782D5644534C10080002000A103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"lindegade241salth"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00116C696E64656761646532343173616C7468
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444B20010D10
          Cell 03 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TDC-9285"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00085444432D39323835
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210005536167656D102300084661737433357878102400043132333410420004353637381054000800060050F20400011011001146617374333578782D536167656D204150100800020084103C000101


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
          Current Frequency:2.437 GHz (Channel 6)


##### modinfo #####


filename:       /lib/modules/3.13.0-30-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


##### modules #####


lp
rtc


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


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   15.079169] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.086058] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   15.124415] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   15.419285] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   15.981427] wl 0000:06:00.0: no hotplug settings from platform
[   16.289840] wl 0000:06:00.0: no hotplug settings from platform
[   18.881723] wl 0000:06:00.0: no hotplug settings from platform
[   19.082333] wl 0000:06:00.0: no hotplug settings from platform
[   30.413860] wl 0000:06:00.0: no hotplug settings from platform
[  750.100103] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  874.556872] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  999.116091] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1123.675320] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1248.234801] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1372.793811] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1497.250583] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1621.809883] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1746.369142] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1870.928402] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1995.487667] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2120.046910] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2244.503755] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2369.063023] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2493.555261] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2618.095417] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2742.634862] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2867.174776] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2991.714594] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3116.254725] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3240.794266] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3365.334109] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3489.874097] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3614.413594] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3738.953774] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3863.493358] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3988.033348] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4112.573338] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4237.113057] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4361.652968] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4486.192735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4610.732513] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4735.272345] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4859.812270] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4984.352112] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5108.891822] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5233.431512] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5357.973528] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5482.532781] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5607.092356] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5731.651213] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5856.210613] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5980.769893] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6105.329167] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6229.786137] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6354.345291] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6478.904574] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6603.463858] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6728.023134] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6852.582411] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6977.039254] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7101.598429] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7226.157753] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7350.717094] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7475.276377] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7599.733222] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7724.292507] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7848.851781] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 7973.411457] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8097.970339] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8222.531231] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8346.986458] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8471.545743] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8596.105389] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8720.664261] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8845.223530] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 8969.680382] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9094.239648] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9218.798973] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9343.358141] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9467.917510] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9592.374356] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9716.933613] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9841.493029] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9966.052152] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10090.611426] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10215.170797] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10339.627536] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10464.186841] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10588.746090] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10713.305308] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10837.864659] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[10962.321475] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11086.880749] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11211.440021] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11335.999292] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11460.558566] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11585.117735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11709.574686] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11834.133961] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11958.693236] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12083.252511] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12207.812192] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12332.268634] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12456.827911] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12581.387190] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12705.947889] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12830.506046] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:78:9e:4f:f5:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13063.223294] ERROR @wl_dev_intvar_get : error (-1)
[13063.223302] ERROR @wl_cfg80211_get_tx_power : error (-1)


########## wireless info END ############
```[COLOR=#000000]

Here's the script as an attachment:

[/COLOR][ATTACH]254422[/ATTACH][COLOR=#000000]

Does anybody have any idea how I can fix this, or at the very least diagnose the problem? I'm usually very good with Ubuntu, but this one has me completely stumped and searching for an answer makes me feel as though I'm reading a different language.

Thanks in advance.[/COLOR]

---

### Post by praseodym on 2014-07-03
Hi,

the driver shows "wl", the proprietary station driver, the interface name is "wlan0" from the native driver. Try that one instead. Via cable connection:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Reboot. If necessary change the encryption mode to pure WPA2-AES instead of mixed mode WPA/WPA2.

---

### Post by serbriang on 2014-07-04
Hi! Thanks for the answer. The only command that gave any result was the first:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source[/FONT][/COLOR]
```



I already had the linux-firmware-nonfree, and the sudo rm commands resulted in "no such file". 

Finally, the final 4commands - the sudo sed - all resulted in "sed: no input files"

What to do?

---

### Post by varunendra on 2014-07-04
Did you reboot after running the purge command? The sed errors you got are fine, it just means there were no files blacklisting correct drivers.

If you still can't scan or connect to available wireless networks, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

This script is a modified one and will give us much more info than the regular one.

---

### Post by serbriang on 2014-07-04
I just rebooted - I expected to get a result other than the sed errors, but of course that makes sense. ;)

I am using wireless right now without issue, though I am only about a minute into it. I'll check back in if it does not work by running the other script that you recommended to me.

For now, I'd prefer not to mark this as solved until I am sure that it is - if that's acceptable with you.

Thank you very much.

---

### Post by varunendra on 2014-07-04
> **serbriang said:**
> For now, I'd prefer not to mark this as solved until I am sure that it is - if that's acceptable with you.

That's perfectly okay, in fact recommended, that you test the connection stability for a reasonably long time, and mark the thread as [SOLVED] only when you are satisfied. The current driver in use would be "brcmsmac", which is supposed to work nicely with your card. Just remember _NOT_ to install the "STA" driver again (the one proposed by the "Additional Drivers" program - that one breaks the "brcmsmac" driver).

---

### Post by serbriang on 2014-07-04
Thanks again! 

I'd also like to ask if would you have any idea as to why it suddenly started like it did, well after my upgrade to 14.04? I can't seem to recall any updates that would have effected me, and looking though my update history I couldn't pinpoint it. If there's something I know about now, I can be on guard for it in the future.

---

### Post by varunendra on 2014-07-04
> **serbriang said:**
> Thanks again! 

I'd also like to ask if would you have any idea as to why it suddenly started like it did, well after my upgrade to 14.04? I can't seem to recall any updates that would have effected me, and looking though my update history I couldn't pinpoint it. If there's something I know about now, I can be on guard for it in the future.

Your card is supported by both the native driver "brcmsmac" and the proprietary driver "wl" (also called "STA" driver, the package that installs it is "bcmwl-kernel-source"). If the 'STA' (or "wl") driver gets installed somehow (by accepting the recommendation of "Additional Drivers" program, or by following some tutorial etc.), it 'blacklists' the native one to avoid conflicts.

The proprietary one sometimes works okay, but sometimes not so good. Whereas the native one almost always works better with this card that you have (except in kernel versions earlier than 3.5). So there may be two reasons for the problem that occurred -

**1)** Maybe you were always using the "wl" driver and it was working okay until the last version. The last version started showing troubles it is known for and we moved you to the native driver which, we hope, will keep working better for you.

**2)** Maybe you were always using the native "brcmsmac" driver until the problem. Maybe the problem began with an accidental installation of the "wl" driver. We just switched you back to the native driver that usually works better.

To check which driver you are using, use the following command -
```
lsmod | egrep 'wl|brcm|b43'
```
We never expect the third variant "b43" to load with this card. But in recent versions, it has started loading with "brcmsmac" due to a bug, which causes problems. In an ideal condition, you should only see "brcmsmac" in the above output, with its supporting drivers. No "b43", no "wl".

---

### Post by serbriang on 2014-07-04
At any rate, at least I know to be on guard for it - thanks for your answer!

---

### Post by varunendra on 2014-07-04
You're welcome! I'd be waiting curiously for your feedback, especially to see if a kernel upgrade causes the b43 trouble or if it has been fixed now. If not, that is quite easy to fix as well, but we love to see things working by themselves, without needing any intervention. :)

---

