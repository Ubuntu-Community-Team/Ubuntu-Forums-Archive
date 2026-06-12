---
title: "Wifi manager defaulting to wep"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by rmasp98 on 2016-01-29
I am running ubuntu 14.04 and have just done a big update (I haven't used this computer in a while - ~400mb) and after the update I rebooted and upon restart it did not automatically connect me to the wifi. When I tried manually connecting, it automatically asked for a wep key instead of the wpa2 password. I can get around this by editing the connection security settings to wpa2 but that only works for that session. The next day when I log onto my computer, it no longer recognises the ssid of the previous edited wifi connection and tries to make a new one with wep again (called "old ssid 2").

This is also not an isolated incident because the same happened with my laptop which is also running ubuntu 14.04.

Sorry if I missed any information out but I am fairly new to the ways of the forum. Thank you for any help

Below are the results of the wifi script that is generally ask for:

```


########## wireless info START ##########


Report from: 29 Jan 2016 18:09 GMT +0000


Booted last: 29 Jan 2016 18:04 GMT +0000


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-76-generic #120-Ubuntu SMP Mon Jan 18 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05e3:0616 Genesys Logic, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 003 Device 005: ID 0b05:1786 ASUSTek Computer, Inc. USB-N10 802.11n Network Adapter [Realtek RTL8188SU]
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


cfg80211              484040  0 
r8712u                184158  0 
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1747 errors:0 dropped:40 overruns:0 frame:0
          TX packets:1347 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1445873 (1.4 MB)  TX bytes:260595 (260.5 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"VM657364-2G"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'VM657364-2G' [AC1]>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=73/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       716     1  0 18:04 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [VM657364-2G 2] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    BTHub3-KHZ6:     Infra, <MAC 'BTHub3-KHZ6' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2 Enterprise
    SKYE3E3A:        Infra, <MAC 'SKYE3E3A' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    BTHub3-N83C:     Infra, <MAC 'BTHub3-N83C' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60
    BTWiFi-with-FON: Infra, <MAC 'BTWiFi-with-FON' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    VM257795-2G:     Infra, <MAC 'VM257795-2G' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    *VM657364-2G:    Infra, <MAC 'VM657364-2G' [AC1]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 96 WEP


  IPv4 Settings:
    Address:         192.168.0.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


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


Sorry, try again.
[[/etc/NetworkManager/system-connections/VM657364-2G 2]] (600 root)
[connection] id=VM657364-2G 2 | type=802-11-wireless
[802-11-wireless] ssid=VM657364-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/VM277502-2G]] (600 root)
[connection] id=VM277502-2G | type=802-11-wireless
[802-11-wireless] ssid=VM277502-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


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


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM657364-2G' [AC1]>
                    ESSID:"VM657364-2G"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 22.5 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'BTWifi-X' [AC2]>
                    ESSID:"BTWifi-X"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f201
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    Signal level=44/100  
          Cell 03 - Address: <MAC 'BTHub3-KHZ6' [AC3]>
                    ESSID:"BTHub3-KHZ6"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=58/100  
          Cell 04 - Address: <MAC 'BTWifi-with-FON' [AC4]>
                    ESSID:"BTWifi-with-FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=62/100  
          Cell 05 - Address: <MAC 'BTWiFi-with-FON' [AC5]>
                    ESSID:"BTWiFi-with-FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=7/100  
          Cell 06 - Address: <MAC 'BTHub3-N83C' [AC6]>
                    ESSID:"BTHub3-N83C"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-76-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-76-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        48:96:E7:E7:A5:A8:CC:7D:65:5D:1C:FF:9B:E9:CC:10:86:64:96:FB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[r8712u]
filename:       /lib/modules/3.13.0-76-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     A3EDB8E0F617968816DC0C5
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-76-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        48:96:E7:E7:A5:A8:CC:7D:65:5D:1C:FF:9B:E9:CC:10:86:64:96:FB
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   13.010554] usb 3-4: Direct firmware load failed with error -2
[   13.011456] Bluetooth: can't load firmware, may not work correctly
[   13.194012] usb 3-3.3: Product: ASUS EZ N Network Adapter
[   13.199639] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   13.200117] r8712u: Staging version
[   13.200125] r8712u: register rtl8712_netdev_ops to netdev_ops
[   13.200128] usb 3-3.3: r8712u: USB_SPEED_HIGH with 4 endpoints
[   13.200797] usb 3-3.3: r8712u: Boot from EFUSE: Autoload OK
[   13.554317] usb 3-3.3: r8712u: CustomerID = 0x0010
[   13.554322] usb 3-3.3: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[   13.554325] usb 3-3.3: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   14.275687] r8712u 3-3.3:1.0 wlan0: 1 RCR=0x153f00e
[   14.276146] r8712u 3-3.3:1.0 wlan0: 2 RCR=0x553f00e
[   14.379489] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  150.959014] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  151.059041] r8712u 3-3.3:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC 'VM657364-2G' [AC1]>, seq = 0, tid = 0
[  154.591373] r8712u 3-3.3:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC 'VM657364-2G' [AC1]>, seq = 0, tid = 4


########## wireless info END ############



```

---

### Post by ajgreeny on 2016-01-29
Not sure about the default to WEP instead of WPA, but can I ask if you have the proposed update repos enabled as that has caused a few users to lose all connectivity?

If so see [http://ubuntuforums.org/showthread.php?t=2311717&p=13431089#post13431089](http://ubuntuforums.org/showthread.php?t=2311717&p=13431089#post13431089) for what to try next.

---

### Post by rmasp98 on 2016-01-30
I don't have proposed enabled and I haven't lost all connectivity. It is still there, just trying authenticate in the wrong way

---

### Post by jeremy31 on 2016-01-30
You will have to change the encryption settings on the router to WPA2 as it currently shows it is using only WEP
```
[COLOR=#000000][FONT=Ubuntu Mono]*VM657364-2G:    Infra, <MAC 'VM657364-2G' [AC1]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 96 WEP
```[/FONT][/COLOR]

---

### Post by rmasp98 on 2016-01-30
That's kinda the problem. My router itself is definitely set to wpa2 default because it has no problem with any other (non ubuntu) device using the wpa2 password, plus it works fine with my Fedora boot. The problem seems to be that it is ignoring the router's default setting and using wep instead. And as I said in the original post, setting the security to WPA2 manually within ubuntu only works for one connection session (i.e. until the turn the computer off)

---

### Post by jeremy31 on 2016-01-30
See what this command returns in Fedora, if it works ```
iwlist scan | egrep -i 'ssid|cipher'
```

---

### Post by rmasp98 on 2016-01-30
Here are the results of that command:

```
   iwlist scan | egrep -i 'ssid|cipher'enp2s0    Interface doesn't support scanning.


virbr0-nic  Interface doesn't support scanning.


virbr0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


                    ESSID:"VM657364-2G"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                    ESSID:"VM257795-2G"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                    ESSID:"BTWifi-X"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                    ESSID:"BTHub3-KHZ6"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                    ESSID:"SKYE3E3A"
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                    ESSID:"BTWifi-with-FON"
                    ESSID:""
                    ESSID:"BTHub3-N83C"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP


  
```

---

### Post by jeremy31 on 2016-01-30
I would change the wifi router encryption to WPA2 only without TKIP, save setting and reboot router and see if Ubuntu functions correctly

---

### Post by rmasp98 on 2016-01-31
I tried forcing to AES encryption (the only other alternative) and it no longer allowed me to connect at all with Ubuntu. I feel like this is trying to solve a symptom rather than the actual cause. As this is affecting none of my other devices and occurred after a change to the OS and not the router, I am fairly sure that this is a problem with the OS but I don't know enough about how all the network manager stuff works to even start on fixing it

---

### Post by jeremy31 on 2016-01-31
I would delete the connections from Network Manager and see if adding it back allows you to select WPA WPA2-Personal

---

### Post by rmasp98 on 2016-02-02
Sorry, tried that one already. Thank you for all the suggestions

---

### Post by rmasp98 on 2016-02-04
Sorry I already tried that. I also tested another wireless card to see if it was that that went wrong but the new card doesn't work either. Thank you for your help

---

### Post by jeremy31 on 2016-02-04
Can you put the wireless router on channel 1, 9, or 13 for a test.  It might help to set the country code ```
sudo iw reg set GB
```
```
gksudo gedit /etc/default/crda
``` and change the last line to be ```
REGDOMAIN=GB
```

Save, exit, reboot

---

### Post by yonnie on 2016-02-06
I'm having the same described issues with several laptops, different brands, Dell, HP, MSI, ASUS.  I've had a similar issue with connecting twice for years, been long time issue with most distro's not just 14.04.  Lubuntu, Kubuntu, Ubuntu, Xubuntu, PCLOS, Antix, .... .  The problem is something to do with the basic wireless manager code and I wish somebody would fix it.

I login using a wpa2-aes psk, the connection works for awhile then quits.  Can't log back in because the security thinks I need to input a "wep" key.  I get around this issue by using an ethernet cable and turning off the wifi.  Now, more of the equipment I need to work with is wireless only and the problem has jumped from being an annoying nuisance to serious.  In some cases I've had to finish configurations of the job equipment using my Android phone.  Android supposedly uses much of the Linux code base, how is it they fixed the problem we still have?

---

