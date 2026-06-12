---
title: "Belkin USB Wifi Not working RTL8188SU - rtlwifi/rtl8712u.bin"
date: 2016-12-28
forum: Networking &amp; Wireless
---

### Post by xptriado on 2016-12-28
Hi, could you help me with my USB Wifi dongle please, anyone had any issues?

**_I think this is an issue with the driver rlt8712u ?_**

lsusb gives me this:

```
Bus 002 Device 003: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]


```

iwconfig gives me this:

```
wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

dmesg -c . upon inserting usb pen

```

[ 3718.819805] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[ 3718.914909] usb 2-1.2: New USB device found, idVendor=050d, idProduct=945a
[ 3718.914919] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3718.914925] usb 2-1.2: Product: Belkin USB Wireless Adaptor
[ 3718.914930] usb 2-1.2: Manufacturer: Manufacturer Realtek 
[ 3718.914934] usb 2-1.2: SerialNumber: 00e04c000001
[ 3718.915669] r8712u: Staging version
[ 3718.915708] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 3718.915718] usb 2-1.2: r8712u: USB_SPEED_HIGH with 4 endpoints
[ 3718.916364] usb 2-1.2: r8712u: Boot from EFUSE: Autoload OK
[ 3719.671719] usb 2-1.2: r8712u: CustomerID = 0x0000
[ 3719.671730] usb 2-1.2: r8712u: MAC Address from efuse = 08:86:3b:0f:f5:9a
[ 3719.671736] usb 2-1.2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3720.411724] r8712u 2-1.2:1.0 wlan1: 1 RCR=0x153f00e
[ 3720.412585] r8712u 2-1.2:1.0 wlan1: 2 RCR=0x553f00e
[ 3720.519341] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3720.519874] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3720.827271] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

/etc/network/interfaces
```
auto lo
iface lo inet loopback


```

/etc/wpa_supplicant/wpa_supplicant.conf  (xxxxxxx ommitting personal data)
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=2
network={
  ssid="xxxxxxxxxxxxxxxxxxxxxxx"
  scan_ssid=1
  proto=RSN
  key_mgmt=WPA-PSK
  pairwise=CCMP
  group=CCMP
# choose one of the following
# run wpa_passphrase "ssid"
  psk="xxxxxxxxxxxxxxxxxx"
}

```

modprobe
```
sudo modprobe r8712u
```  gives no output

lsmod
```
lsmod | grep r8712
r8712u                184158  0 

```

```
sudo ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 08:86:3b:0f:f5:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```
sudo ifup wlan1
Ignoring unknown interface wlan1=wlan1.

```

```
sudo ifdown wlan1
ifdown: interface wlan1 not configured

```


thank you!!

---

### Post by wildmanne39 on 2016-12-28
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by praseodym on 2016-12-29
Please try

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
Re-plug the stick

---

### Post by xptriado on 2016-12-29
> **praseodym said:**
> Please try

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
Re-plug the stick

i tried the commands but no luck. In network-manager it says "Disconnected". But the light is blinking in the Belkin USB pen.

Additionally, I have this line now,everytime I boot, maybe from some failed command I ran yesterday and I cant seem to get it out.

```
/var/log/apt/term.log:libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rtl8712.conf line 1: ignoring bad line starting with 'opions'
``` 

However, I check /etc/modprobe.d/rtl8712.conf and there is no such file.
```

 sudo ls /etc/modprobe.d/
alsa-base.conf            blacklist-modem.conf     iwlwifi.conf
blacklist-ath_pci.conf        blacklist-oss.conf         mlx4.conf
blacklist.conf            blacklist-rare-network.conf  r8712u.conf
blacklist-firewire.conf     blacklist-watchdog.conf     vmwgfx-fbdev.conf
blacklist-framebuffer.conf  fbdev-blacklist.conf

```

I think I may have an issue now in the modprobe.d config files: seems  like its parsing a rtl8712.conf and r8712.conf ... but the driver is the  same so it is probably some mistake I done yesterday. How to untangle  this?
```

sudo echo "options rtl8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/rtl8712u.conf
options rtl8712u low_power=1 power_mgnt=0 ht_enable=0
rui@laptop:~$ sudo modprobe -rfv rtl8712u
modprobe: FATAL: Module rtl8712u not found.

```

This is now my r8712u.conf

```

sudo cat /etc/modprobe.d/r8712u.conf 
options r8712u low_power=1 power_mgnt=0 ht_enable=0

```


I ran apt-get update and upgrade.

This is the wireless info script result:
```


########## wireless info START ##########

Report from: 29 Dec 2016 17:29 WET +0000

Booted last: 29 Dec 2016 17:16 WET +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/rui/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6617]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 003: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8712u                184158  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  0 
wmi                    19177  2 acer_wmi,mxm_wmi
video                  19476  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2563 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1438656 (1.4 MB)  TX bytes:372013 (372.0 KB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:"ZON-DAB0"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'ZON-DAB0' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:61   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       758     1  0 17:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF3]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: wlan0  [ZON-DAB0] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ZON-D730:        Infra, <MAC 'ZON-D730' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    MEO-7BF2BD:      Infra, <MAC 'MEO-7BF2BD' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40
    *ZON-DAB0:       Infra, <MAC 'ZON-DAB0' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AC6]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 15
    NOS-5200:        Infra, <MAC 'NOS-5200' [AC5]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

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

[[/etc/NetworkManager/system-connections/ZON-DAB0 1]] (600 root)
[connection] id=ZON-DAB0 1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=shared

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET | type=802-11-wireless | permissions=user:rui:;
[802-11-wireless] ssid=FON_ZON_FREE_INTERNET | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ZON-DAB0]] (600 root)
[connection] id=ZON-DAB0 | type=802-11-wireless
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-DAB0 2]] (600 root)
[connection] id=ZON-DAB0 2 | type=802-11-wireless
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.472 GHz (Channel 13)

wlan1     No scan results

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ZON-DAB0' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ZON-DAB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000238932ce14
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MEO-7BF2BD' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"MEO-7BF2BD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030285a5e959
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ZON-D730' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ZON-D730"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a6a6ea807a
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a6a6ea834f
                    Extra: Last beacon: 72ms ago
          Cell 05 - Address: <MAC 'NOS-5200' [AC5]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"NOS-5200"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000404965ccc01
                    Extra: Last beacon: 11140ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC6]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000404965cd22c
                    Extra: Last beacon: 11140ms ago

##### module infos ######################

[r8712u]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 0
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 1
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

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF3]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[   20.691973] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   20.692643] r8712u: Staging version
[   20.692657] r8712u: register rtl8712_netdev_ops to netdev_ops
[   20.692661] usb 2-1.2: r8712u: USB_SPEED_HIGH with 4 endpoints
[   20.693255] usb 2-1.2: r8712u: Boot from EFUSE: Autoload OK
[   21.351753] usb 2-1.2: r8712u: CustomerID = 0x0000
[   21.351764] usb 2-1.2: r8712u: MAC Address from efuse = <MAC 'wlan1' [IF3]>
[   21.351771] usb 2-1.2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   22.579271] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   22.596098] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   22.659211] tg3 0000:01:00.0 eth0: Link is down
[   23.310810] r8712u 2-1.2:1.0 wlan1: 1 RCR=0x153f00e
[   23.311702] r8712u 2-1.2:1.0 wlan1: 2 RCR=0x553f00e
[   23.418551] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 3 times)
[   24.652054] wlan0: authenticate with <MAC 'ZON-DAB0' [AC1]>
[   24.670002] wlan0: send auth to <MAC 'ZON-DAB0' [AC1]> (try 1/3)
[   24.712926] wlan0: authenticated
[   24.713588] wlan0: associate with <MAC 'ZON-DAB0' [AC1]> (try 1/3)
[   24.721357] wlan0: RX AssocResp from <MAC 'ZON-DAB0' [AC1]> (capab=0xc31 status=0 aid=3)
[   24.721415] wlan0: associated
[   24.721449] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

---

### Post by praseodym on 2016-12-29
> ```
/var/log/apt/term.log:libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rtl8712.conf line 1: ignoring bad line starting with '[COLOR="#FF0000"]opions[/COLOR]'
```
Typo?

Please check:
```

grep opions /etc/modprobe.d/*
grep 8712 /etc/modprobe.d/*
```

The driver is named r8712u, not rtl8712u:

```
r8712u                184158  0 
ath9k                 164164  0 
```
What about the internal Atheros card? Please try for this:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Also change the encryption mode to WPA2-AES (CCMP), not mixed mode.

Additionally, Wicd and NWM are installed in parallel. Try Wicd first:
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

Country is Portugal, so change the country code settings to:
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=PT/g" /etc/default/crda 
```
Reboot after that.

---

### Post by xptriado on 2016-12-29
regarding the mixed mode and wpa2 where to modify it? I understand this is to do with the ath9k but its working properly. The ath9k is internal so I wanted to configure the belkin as it gives me better reception

I ran the commands successfully but not change in "symptoms". 

Also I still have on boot this error message about the "opions". Where is the rtl8712u.conf file in module.d coming from?

```

rui@laptop:~$ sudo grep opions /etc/modprobe.d/*
rui@laptop:~$ sudo grep 8712 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:#blacklist r8712u
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it8712f_wdt
/etc/modprobe.d/r8712u.conf:options r8712u low_power=1 power_mgnt=0 ht_enable=0
/etc/modprobe.d/rtl8712u.conf:options rtl8712u low_power=1 power_mgnt=0 ht_enable=0
rui@laptop:~$ 

```

---

### Post by wildmanne39 on 2016-12-29
Try:
```
sudo modprobe -rv ath9k
sudo modprobe -v r8712u low_power=1 power_mgnt=0 ht_enable=0
```
does it connect now? please post any errors here, rebooting will revert theses changes so do not reboot unless you can not connect.

---

### Post by xptriado on 2016-12-29
I ran the commands but no change.

```

rui@laptop:~$ sudo modprobe -rv ath9k
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
rui@laptop:~$ sudo modprobe -v r8712u low_power=1 power_mgnt=0 ht_enable=0
rui@laptop:~$ 


```


I replugged the USB and here is my new script results:

```


########## wireless info START ##########

Report from: 29 Dec 2016 21:27 WET +0000

Booted last: 29 Dec 2016 18:16 WET +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/rui/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6617]

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)

##### lsusb #############################

Bus 002 Device 005: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b209 Chicony Electronics Co., Ltd
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              484040  0
r8712u                184158  0
acer_wmi               32522  0
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  0
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
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
    Wicd

Running:

root      9769     1  0 21:24 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

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

[[/etc/NetworkManager/system-connections/ZON-DAB0 1]] (600 root)
[connection] id=ZON-DAB0 1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=shared

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET | type=802-11-wireless | permissions=user:rui:;
[802-11-wireless] ssid=FON_ZON_FREE_INTERNET | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ZON-DAB0]] (600 root)
[connection] id=ZON-DAB0 | type=802-11-wireless
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-DAB0 2]] (600 root)
[connection] id=ZON-DAB0 2 | type=802-11-wireless
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     14 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     No scan results

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8712u]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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
ht_enable: 0
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 1
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

[/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0

[/etc/modprobe.d/rtl8712u.conf]
options rtl8712u low_power=1 power_mgnt=0 ht_enable=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[11304.046930] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[11304.250376] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[11304.638162] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[11304.745742] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[11430.005425] r8712u: Staging version
[11430.005450] r8712u: register rtl8712_netdev_ops to netdev_ops
[11430.005455] usb 2-1.2: r8712u: USB_SPEED_HIGH with 4 endpoints
[11430.006002] usb 2-1.2: r8712u: Boot from EFUSE: Autoload OK
[11430.738117] usb 2-1.2: r8712u: CustomerID = 0x0000
[11430.738131] usb 2-1.2: r8712u: MAC Address from efuse = <MAC 'wlan1' [IF2]>
[11430.738139] usb 2-1.2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[11430.765773] systemd-udevd[9957]: renamed network interface wlan0 to wlan1
[11431.477741] r8712u 2-1.2:1.0 wlan1: 1 RCR=0x153f00e
[11431.478479] r8712u 2-1.2:1.0 wlan1: 2 RCR=0x553f00e
[11431.585692] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 3 times)

########## wireless info END ############




```


And this is dmesg -c results upon replugging:
```

[11427.064732] usb 2-1.2: USB disconnect, device number 4
[11429.910132] usb 2-1.2: new high-speed USB device number 5 using ehci-pci
[11430.004914] usb 2-1.2: New USB device found, idVendor=050d, idProduct=945a
[11430.004920] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11430.004923] usb 2-1.2: Product: Belkin USB Wireless Adaptor
[11430.004926] usb 2-1.2: Manufacturer: Manufacturer Realtek
[11430.004928] usb 2-1.2: SerialNumber: 00e04c000001
[11430.005425] r8712u: Staging version
[11430.005450] r8712u: register rtl8712_netdev_ops to netdev_ops
[11430.005455] usb 2-1.2: r8712u: USB_SPEED_HIGH with 4 endpoints
[11430.006002] usb 2-1.2: r8712u: Boot from EFUSE: Autoload OK
[11430.738117] usb 2-1.2: r8712u: CustomerID = 0x0000
[11430.738131] usb 2-1.2: r8712u: MAC Address from efuse = 08:86:3b:0f:f5:9a
[11430.738139] usb 2-1.2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[11430.765773] systemd-udevd[9957]: renamed network interface wlan0 to wlan1
[11431.477741] r8712u 2-1.2:1.0 wlan1: 1 RCR=0x153f00e
[11431.478479] r8712u 2-1.2:1.0 wlan1: 2 RCR=0x553f00e
[11431.585692] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[11431.586191] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[11431.893584] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

---

### Post by xptriado on 2016-12-29
i see it says "staging version". could this be the reason? i think its the firmware which is defect?

---

### Post by xptriado on 2016-12-29
I can  now see networks and connect!!!!! After I sent you my last  message the screen locked, and now when I unlocked it I noticed I can  see networks. So i'm posting new dmesg and script...maybe there is some  difference?

I don't know what I did,this is the history. I think it was those commands together with locking the screen?!
```

499  sudo grep opions /etc/modprobe.d/*
  500  sudo grep 8712 /etc/modprobe.d/*
  501  sudo modprobe -rv ath9k
  502  sudo modprobe -v r8712u low_power=1 power_mgnt=0 ht_enable=0
  503  iwconfig
  504  dhclient
  505  sudo dhclient
  506  sudo dmesg -c
  507  sudo wpa_supplicant wlan1
  508  sudo wpa_supplicant -i wlan1 -c /etc/wpa_supplicant/wpa_supplicant.conf 
  509  sudo iwconfig wlan1
  510  sudo ifconfig wlan1
  511  sudo wpa_supplicant -i wlan1 -c /etc/wpa_supplicant/wpa_supplicant.conf 
  512  sudo apt-get remove wicd
  513  sudo service network-manager start
  514  sudo ifdown wlan1
  515  sudo ifup wlan1
  516  sudo ifdown wlan1
  517  dmesg -c
  518  sudo dmesg -c
  519  sudo iwconfig wlan1
  520  sudo ifconfig wlan1
  521  lsusb
  522  sudo service network-manager restart
  523  sudo rm wireless-info.t*
  524  sudo ./wireless-info 
  525  sudo rm wireless-info.t*
  526  sudo ./wireless-info 
  527  sudo dmesg -c
  528  sudo gedit wireless-info.txt 
  529  sudo modprobe -rv ath9k
  530  sudo modprobe -v ath9k
  531  sudo modprobe -rv ath9k
  532  sudo modprobe -v r8712u low_power=1 power_mgnt=0 ht_enable=0
  533  sudo gedit wireless-info.txt
  534  sudo modprobe -v ath9k
  535  sudo gedit wireless-info.txt
  536  sudo dmesg -c
  537  iwconfi
  538  iwconfig
  539  ifconfig
  540  sudo rm wireless-info.txt
  541  sudo ./wireless-info 
  542  sudo gedit wireless-info.txt
  543  ls -l
  544  sudo gedit wireless-info.txt
  545  sudo history
  546  history

```


```
rui@laptop:~$ sudo dmesg -c
[14751.089660] wlan0: deauthenticated from 00:05:ca:7e:da:b8 (Reason: 7)
[14751.125869] cfg80211: Calling CRDA to update world regulatory domain
[14751.136942] cfg80211: World regulatory domain updated:
[14751.136949] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14751.136950] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.136952] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.136954] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14751.136955] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.136956] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.136969] cfg80211: Calling CRDA for country: PT
[14751.141132] cfg80211: Regulatory domain changed to country: PT
[14751.141137] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14751.141139] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14751.141140] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14751.141142] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14751.141143] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14751.141144] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[14751.163722] wlan0: authenticate with 00:05:ca:7e:da:b8
[14751.188300] wlan0: send auth to 00:05:ca:7e:da:b8 (try 1/3)
[14751.193138] wlan0: authenticated
[14751.195485] wlan0: associate with 00:05:ca:7e:da:b8 (try 1/3)
[14751.203429] wlan0: RX AssocResp from 00:05:ca:7e:da:b8 (capab=0xc31 status=0 aid=2)
[14751.203509] wlan0: associated
[14751.205227] wlan0: deauthenticated from 00:05:ca:7e:da:b8 (Reason: 7)
[14751.223207] cfg80211: Calling CRDA to update world regulatory domain
[14751.231714] cfg80211: World regulatory domain updated:
[14751.231721] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14751.231723] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.231724] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.231726] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14751.231727] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.231729] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.231748] cfg80211: Calling CRDA for country: PT
[14751.240731] cfg80211: Regulatory domain changed to country: PT
[14751.240737] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14751.240741] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14751.240744] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14751.240747] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14751.240750] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14751.240753] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[14755.838709] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14756.144981] tg3 0000:01:00.0: irq 44 for MSI/MSI-X
[14756.170426] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[14756.321924] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14756.509898] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[14757.408059] wlan0: authenticate with 00:05:ca:bc:d7:39
[14757.426293] wlan0: send auth to 00:05:ca:bc:d7:39 (try 1/3)
[14757.427872] wlan0: authenticated
[14757.429060] wlan0: associate with 00:05:ca:bc:d7:39 (try 1/3)
[14757.436729] wlan0: RX AssocResp from 00:05:ca:bc:d7:39 (capab=0xc21 status=0 aid=4)
[14757.436799] wlan0: associated
[14757.436840] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
rui@laptop:~$ 


```

and the script
```

########## wireless info START ##########

Report from: 29 Dec 2016 22:35 WET +0000

Booted last: 29 Dec 2016 18:16 WET +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/rui/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6617]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 006: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
r8712u                184158  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  0 
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.3.19  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202620215 (202.6 MB)  TX bytes:9554075 (9.5 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:"FON_ZON_FREE_INTERNET"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'FON_ZON_FREE_INTERNET' [AC2]>   
          Bit Rate=19.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:62   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 wlan0
192.168.3.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root      9769     1  0 21:24 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF3]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ZON-D730:        Infra, <MAC 'ZON-D730' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 43 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 46
    ZON-DAB0:        Infra, <MAC 'ZON-DAB0' [AC3]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2

- Device: wlan0  [FON_ZON_FREE_INTERNET] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           19 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ZON-D730:        Infra, <MAC 'ZON-D730' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    ZON-DAB0:        Infra, <MAC 'ZON-DAB0' [AC3]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 42

  IPv4 Settings:
    Address:         192.168.3.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.1

    DNS:             192.168.3.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

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

[[/etc/NetworkManager/system-connections/ZON-DAB0 1]] (600 root)
[connection] id=ZON-DAB0 1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=shared

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET | type=802-11-wireless | permissions=user:rui:;
[802-11-wireless] ssid=FON_ZON_FREE_INTERNET | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ZON-DAB0]] (600 root)
[connection] id=ZON-DAB0 | type=802-11-wireless
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-DAB0 2]] (600 root)
[connection] id=ZON-DAB0 2 | type=802-11-wireless
[802-11-wireless] ssid=ZON-DAB0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

country PT:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.442 GHz (Channel 7)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'ZON-D730' [AC1]>
                    ESSID:"ZON-D730"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 02 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC2]>
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Signal level=43/100  
          Cell 03 - Address: <MAC 'ZON-DAB0' [AC3]>
                    ESSID:"ZON-DAB0"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aaebf5b04a
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: <MAC 'ZON-D730' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ZON-D730"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aaebf5ad01
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ZON-DAB0' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ZON-DAB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027ce3dec5d
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8712u]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

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
ht_enable: 0
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 1
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

[/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0

[/etc/modprobe.d/rtl8712u.conf]
options rtl8712u low_power=1 power_mgnt=0 ht_enable=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0'  [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0'  [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1'  [IF3]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan1"
# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

########## wireless info END ############

```

Can  you tell me how you got to that command? THe fact this works now after  locking the screen and those commands is nothing short of voodoo lol

---

### Post by xptriado on 2016-12-29
and now the iwconfig is very different, no more unassigned..IEEE 802 instead

```
wlan1     IEEE 802.11bg  ESSID:"ZON-DAB0"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:05:CA:7E:DA:B8   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/100  Signal level=44/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by xptriado on 2016-12-29
reboot, and still connects. reppluged the usb wifi, and it still connects flawlessly now.

got this messages on dmesg-c upon reppluging:

```
rui@laptop:~$ sudo dmesg -c
[  132.129064] usb 2-1.2: USB disconnect, device number 4
[  134.058405] usb 2-1.2: new high-speed USB device number 5 using ehci-pci
[  134.153520] usb 2-1.2: New USB device found, idVendor=050d, idProduct=945a
[  134.153528] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  134.153534] usb 2-1.2: Product: Belkin USB Wireless Adaptor
[  134.153539] usb 2-1.2: Manufacturer: Manufacturer Realtek 
[  134.153543] usb 2-1.2: SerialNumber: 00e04c000001
[  134.154326] r8712u: Staging version
[  134.154364] r8712u: register rtl8712_netdev_ops to netdev_ops
[  134.154373] usb 2-1.2: r8712u: USB_SPEED_HIGH with 4 endpoints
[  134.155014] usb 2-1.2: r8712u: Boot from EFUSE: Autoload OK
[  134.910335] usb 2-1.2: r8712u: CustomerID = 0x0000
[  134.910344] usb 2-1.2: r8712u: MAC Address from efuse = 08:86:3b:0f:f5:9a
[  134.910350] usb 2-1.2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  135.742147] r8712u 2-1.2:1.0 wlan1: 1 RCR=0x153f00e
[  135.743050] r8712u 2-1.2:1.0 wlan1: 2 RCR=0x553f00e
[  135.849907] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  135.850438] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  136.157935] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready


```

the messages seem exactly the same as in the very first dmesg -c i posted... voodoo?

---

### Post by wildmanne39 on 2016-12-29
The:
```
sudo modprobe -rv ath9k
```
removed the driver for your internal card and the next command loaded the driver for your usb device.

This commands came from years of research and learning on the internet.

---

### Post by xptriado on 2016-12-30
.

---

### Post by wildmanne39 on 2016-12-30
I am not sure why it was not immediate either, but I am glad it is working.

---

