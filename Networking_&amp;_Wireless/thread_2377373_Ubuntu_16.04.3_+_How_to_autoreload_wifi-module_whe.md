---
title: "Ubuntu 16.04.3 + How to autoreload wifi-module when waking from suspend?"
date: 2017-11-12
forum: Networking &amp; Wireless
---

### Post by Janiporo on 2017-11-12
I try to make this short as possible.

USB Stick is: 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter

I have this problem that I loose wifi --> 1 time out of every 6 suspend-wake up-cycles, approx.

I need to run these when computer wakes up from suspend (so that my usb-wifi stick reboots):
```
rmmod mt7601u
modprobe mt7601u
```

I have tried many different options, none have worked. Tried to launch correctly modified [/etc/rc.local]("https://ubuntuforums.org/etc/rc.local") automatically, I could not get it to run. Manually running sudo [/etc/rc.local]("https://ubuntuforums.org/etc/rc.local") works fine.

So how? Please, step by step instructions, or any different ideas. Must be permanent solution, even after kernel update.

---

### Post by Hadaka on 2017-11-12
Hi try this..
```
echo mt7601u | sudo tee -a /etc/modules
```

Is the internal wifi driver blacklisted ? if NO then run this command to determine the driver.
```
lspci -nnk | awk 'c&&!--c;/0280/{c=2}'
```
To blacklist the Kernel driver in use [COLOR=#ff0000]XXXXXX[/COLOR] do.
```
echo **[COLOR=#ff0000]YOUR_DRIVER [/COLOR]**|sudo tee -a /etc/modprobe.d/blacklist.conf
```

*Example from my computer..
 ```
hadaka@~$ lspci -nnk | awk 'c&&!--c;/0280/{c=2}'
    Kernel driver in use**[COLOR=#ff0000]->[/COLOR]** b43-pci-bridge
```
so the b43-pci-bridge would get blacklisted.
Also make sure the Connect Automatically box is checked in your network connections box

---

### Post by Janiporo on 2017-11-13
```
echo mt7601u | sudo tee -a /etc/modules
```
tells me:
```
mt7601u
```

```
lspci -nnk | awk 'c&&!--c;/0280/{c=2}'
```
displays nothing

should it NOT be lspci, since this is USB?

Or did I do something wrong? :roll:

USB-stick is connected and there of course the "Connect automatically"-box is ticked.

---

### Post by Janiporo on 2017-11-13
Googled around and found this:
```
 inxi -Nn
```
gives me:
```
Network:   Card-1: NVIDIA MCP77 Ethernet driver: forcedeth
           IF: enp0s10 state: down mac: 00:25:22:74:dc:3b
           Card-2: Ralink MT7601U Wireless Adapter driver: mt7601u
           IF: wlx20e11705ee69 state: N/A mac: N/A

```
It tells me I should blacklist mt7601u ? (figured this name earlier, but what did I do wrong?)
after manually editing blacklist.conf:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and added following at the end of the file, did not help:
```
blacklist mt7601u
```

I must be at the wrong path here... :roll:

---

### Post by Hadaka on 2017-11-13
Hi, I asked if the internal wifi card's driver..lspci.. was blacklisted. NOT
the usb...lsusb.
Let's start by removing the usb driver from blacklisting.
please do..
```
[COLOR=#000000]sudo sed -i '/mt7601u/ d' /etc/[/COLOR][COLOR=#000000][FONT=&quot]modprobe.d/blacklist.conf[/FONT][/COLOR]
```

Now let's see what the driver for the internal card is..as it may be conflicting
with the external usb module.. please do and post.
```
lspci -nnk | grep -iA2 0280
```
The INTERNAL card driver is the driver that needs blackisting.
Thanks.

---

### Post by Janiporo on 2017-11-13
```
lspci -nnk | grep -iA2 0280
```
says nothing

For the record, this is not a laptop, and there is no internal wifi-card either. (I posted in the original post mistakenly that this is a card, I meant USB-stick, will edit that)

---

### Post by Hadaka on 2017-11-13
ok, thanks for that information. please connect to the internet and then
from a terminal..ctrl/alt/t...Copy and Paste..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
From your directory please copy,paste and post the **wireless-info.txt**
thanks.

*Even though you ill be attached to the internet with a wired connection
it will still produce the **wireless-info.txt **

---

### Post by Janiporo on 2017-11-14
Here you go. Fresh boot with USB-wifi stick inserted:

```

########## wireless info START ##########

Report from: 14 Nov 2017 12:03 EET +0200

Booted last: 14 Nov 2017 00:00 EET +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.10.0-38-generic #42~16.04.1-Ubuntu SMP Tue Oct 10 16:32:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: ASRock Incorporation K10N78FullHD-hSLI R3.0 Ethernet [1849:0760]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 09da:000a A4Tech Co., Ltd. Optical Mouse Opto 510D / OP-620D
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 048d:1336 Integrated Technology Express, Inc. SD/MMC Cardreader
Bus 001 Device 003: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04b4:0100 Cypress Semiconductor Corp. Cino FuzzyScan F760-B
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mac80211              782336  1 mt7601u
cfg80211              602112  2 mac80211,mt7601u

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s10   Link encap:Ethernet  HWaddr <MAC 'enp0s10' [IF1]>  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c12a:6e74:104a:def8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930145 (930.1 KB)  TX bytes:277064 (277.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48884 (48.8 KB)  TX bytes:48884 (48.8 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp0s10   no wireless extensions.

lo        no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp0s10
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s10
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s10

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       822     1  0 12:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s10
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP77 Ethernet (K10N78FullHD-hSLI R3.0 Ethernet)
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s10' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/net/enp0s10
GENERAL.IP-IFACE:                       enp0s10
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kiinteä yhteys 1
GENERAL.CON-UUID:                       3684fdc8-11e7-34c6-ac84-c16325311b8b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3684fdc8-11e7-34c6-ac84-c16325311b8b | Kiinteä yhteys 1
IP4.ADDRESS[1]:                         192.168.1.70/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             195.74.0.47
IP4.DNS[2]:                             195.197.54.100
IP6.ADDRESS[1]:                         fe80::c12a:6e74:104a:def8/64
IP6.GATEWAY:                            
IP6.DNS[1]:                             fe80::1

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MediaTek
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         mt7601u
GENERAL.DRIVER-VERSION:                 4.10.0-38-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d3fbafaf-0306-424e-b5bd-c53c336f0a9c | SIPULI 1

SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
SIPULI  <MAC 'SIPULI' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
SIPULI  <MAC 'SIPULI' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SIPULI]] (600 root)
[connection] id=SIPULI | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=SIPULI
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SIPULI 1]] (600 root)
[connection] id=SIPULI 1 | type=wifi | autoconnect=false | permissions=user:mummola:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=SIPULI
[ipv4] method=manual
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Helsinki (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s10   no frequency information.

lo        no frequency information.

wlx<IF from MAC [IF2]>  14 channels in total; available frequencies :
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

enp0s10   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'SIPULI' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"SIPULI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063199db0e6
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SIPULI' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"SIPULI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d1dee9a1d3
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.10.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-38-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-38-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

mt7601u
mt7601u
mt7601u
mt7601u
mt7601u
mt7601u
mt7601u

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

rmmod mt7601u
modprobe mt7601u

wait 5

gnome-calculator

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.703833] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[    6.147288] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[    6.147818] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[    6.771268] mt7601u 1-3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[    6.789233] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[   11.834632] mt7601u 1-3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   11.863037] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)

########## wireless info END ############


```

As you can see there are two identicals SSID:s (SIPULI) Since other one is repeater. But I do not think that is the problem, since wireless part in network manager does not start at all sometimes.

Also (if I remember correctly) this info was taken when the wireless WAS available in network manager (but not connected). Should I do this when the problem is active?

/etc/rc.local is trying to reboot this wifi-module, but I can not get it to run when waking from hibernate. It also starts calculator, so I can deffinetely see that it has been run.

---

### Post by Hadaka on 2017-11-14
"As you can see there are two identicals SSID:s (SIPULI) Since other one is repeater. But I do not think that is the problem"
This is indeed a HUGE problem..
[AC2] has mixed mode..WPA1 WPA2 ..should be wapa2 only same as [AC1]
[AC2] has TKIP that causes issues. change in router/repeater ? to ccmp wapa2 same as [AC1]
[AC2] has same SSID as [AC1]..this will neve work being that close together...change it.
Please disconnect the repeater while you are getting this wifi working correctly.

SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
SIPULI  <MAC 'SIPULI' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
SIPULI  <MAC 'SIPULI' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2  no

2   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'SIPULI' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key-on
                    ESSID:"SIPULI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063199db0e6
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SIPULI' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key-on
                    ESSID:"SIPULI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d1dee9a1d3
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

The wait command and rmmod command are not the best choice.
please sudo gedit /etc/rc.local and chnage rmmod to rm -rf mt7601u
replace modprobe mt7601u to sleep 10 &&  modprobe mt7601u
delete the wait 5 command.
##### rc.local ##########################
rmmod mt7601u     **[COLOR=#ff0000]<-  [/COLOR]****rm -rf mt7601u**
modprobe mt7601u **[COLOR=#ff0000]<- [/COLOR][COLOR=#000000]sleep 10 && modprobe mt7601u[/COLOR]**
wait 5                   **[COLOR=#ff0000]<- [/COLOR][COLOR=#000000]delete[/COLOR]**
gnome-calculator
exit 0

next..the country code is not defined..this also causes drops and issues.
Please copy and paste.
```
sudo iw reg set FI
sudo sed -i 's/=.*/=FI/' /etc/default/crda
```
 When all the above has been corrected..
remove wired connection..boot and test wireless
Thanks.

---

### Post by Janiporo on 2017-11-14
I will. But I have no way to run that rc.local automatically (waking up from suspend)

I disconnected the repeater and when I get this to work, I will later reconfig that and give that different SSID.

---

### Post by Hadaka on 2017-11-14
what do you mean by ?
"I will. But I have no way to run that rc.local automatically." ???

Would you like a terminal command line way ??

---

### Post by Janiporo on 2017-11-14
Now that I have repeater disconnected and did what you told, still wireless does not start. In fact now running /etc/rc.local manually nothing happens to the wireless (but calculator starts in 10 sec)

Manually running:
```
sudo rmmod mt7601u
sudo modprobe mt7601u
```
starts wireless fine.

---

### Post by Janiporo on 2017-11-14
I know how to run /etc/rc.local manually, but how do I get it to run when my computer wakes up from suspend? That is when the problem occurs

---

### Post by Janiporo on 2017-11-14
According to this --> [https://mariogalan.com/en/content/execute-script-after-suspend-ubuntu-1604](https://mariogalan.com/en/content/execute-script-after-suspend-ubuntu-1604)
I should make a script that runs rc.local when waking from suspend. It does not say how to make it to run, and all details are missing, can you help about that?

Should it be:
```
[FONT=monospace][COLOR=#666666]*#!/bin/sh*[/COLOR]

[COLOR=#666666]*# Execute fancontrol*[/COLOR]

[COLOR=#000000]**case**[/COLOR] [COLOR=#ff0000]"$1"[/COLOR] [COLOR=#000000]**in**[/COLOR]
        post[COLOR=#7a0874]**)**[/COLOR]
          [COLOR=#000000]**/etc/rc.local**[/COLOR] 
                [COLOR=#000000]**;;**[/COLOR]
[COLOR=#000000]**esac**[/COLOR]
[/FONT]


```

EDIT: how do I make it to execute, what should be the name? Full instructions, please :roll:

---

### Post by Hadaka on 2017-11-14
ok here are step-by-step instructions to build a script to do the same
commands as you are doing manually, we will be writing the script to
your home directory. and activating it from rc.local file.

The script name is **start-wifi** it will be written to your home directory.
The command in /etc/rc.local executes the start-wifi in the home directory.
From your home directory.
Open a terminal and do..
```
 gedit start-wifi
```
*Then Copy and Paste all 4 lines of the script to the gedit editor.
^Replace 'your-password' with your password
*The Script
```
#!bin/bash
PATH=$PATH:~/usr/bin
echo 'your-password' | sudo -S rm -rf mt7601u
echo 'your-password' | sudo -S modprobe mt7601u
```
*After you have copied the 4 lines of the script to gedit
*Save and close gedit.

*Back to the terminal and do..
```
 sudo chmod u+x start-wifi
```
*Then do ...
```
sudo gedit /etc/rc.local
```
*Delete all the lines and replace with..
```
/home/Janiporo/start-wifi
gnome-calculator
exit 0
```
*Save and close gedit.

***REMOVE Wired connection ***
*Back to terminal and do..
```
sudo reboot
```
It should fly.
***I assumed this would be correct.../home/Janiporo/start-wifi
If it is not "Janiporo" please change it to match what is on your home directory prompt.

---

### Post by Janiporo on 2017-11-15
I am 100% sure this will not work, since rc.local is not executed at any point. And I need it to run when coming back from suspend.

Can you tell me how to run /etc/rc.local when waking from suspend?

---

### Post by Hadaka on 2017-11-15
Try this method..
[https://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130](https://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130)

hope this works for you.

---

### Post by Janiporo on 2017-11-15
It seemed the last one helped, but it does not work after 10 suspend/resume-cycles. (So I am back at the starting point)

I really want to run /etc/rc.local automatically when resuming from suspend, do you have any idea how to make it do that in ubuntu 16.04?

And I need it to run as sudo, since rmmod needs that.

Remember, when problem occurs, no SSID is available in network manager.

I am back with this in rc.local (Since this is only way I get it to work, your suggestions for rmmod-substitute settings did not work)

```
#!/bin/sh
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 5

rmmod mt7601u

sleep 1

modprobe mt7601u

sleep 1

gnome-calculator

exit 0
```

I am trying some other settings, please tell me, if you can help more.

---

### Post by Janiporo on 2017-11-16
I found the solution to run /etc/rc.local when resuming from suspend. It is here --> [https://ubuntuforums.org/showthread.php?t=2377764](https://ubuntuforums.org/showthread.php?t=2377764)

---

