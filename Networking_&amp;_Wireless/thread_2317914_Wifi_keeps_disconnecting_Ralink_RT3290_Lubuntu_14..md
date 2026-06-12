---
title: "Wifi keeps disconnecting Ralink RT3290 Lubuntu 14.04.4 LTS Asus X750JB-DB71"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by jesusguevarautomotriz on 2016-03-21
My WiFi is keeps disconnecting (random disconnects) , attempts to connect
Y may happen some of the following things
It connects again,
Not connect again
 WiFi Network Manager applet and does not detect the WiFi network to which it was connected previously, while another Laptop with Windows located right next remains connected to the WiFi network and continuous regular internet browsing.
Network Manager WiFi applet  and does not shows any WiFi network.

To recover the connection I do

sudo service restart network-manager
and / or multiple attempts through the Network Manager applet until it connects.

I reviewed this, but I'm not sure which solution to apply
[Hp RT5390 Ralink random disconnects - Ubuntu Forums.]("http://ubuntuforums.org/showthread.php?t=2278494")
[Wireless network configuration, Random disconnections - ]("http://Random%20disconnections")[ArchWiki ]("https://wiki.archlinux.org/index.php/ArchWiki:About")
[Unstable wifi connection on Ubuntu 14.04 Trusty Tahr - zeroset Blog]("http://zeroset.mnim.org/2014/04/22/unstable-wifi-connection-on-ubuntu-14-04-trusty-tahr-ctrl-event-disconnected-reason4-locally_generated1/")[URL="http://askubuntu.com/questions/504777/unstable-wireless-connection-in-ubuntu-14-04"]
Unstable wireless connection in Ubuntu 14.04[/URL]
[Unstable Wifi Connection Ubuntu 14.04]("http://askubuntu.com/questions/543602/unstable-wifi-connection-ubuntu-14-04")
[URL="http://askubuntu.com/questions/694167/wifi-get-disconnected-automaticallyhttp://askubuntu.com/questions/694167/wifi-get-disconnected-automatically"]Wifi get disconnected automatically
[/URL][Ralink rt3290 wifi driver is not working in Ubuntu 14.04]("http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04")
[URL="http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working"]How do I get a Ralink RT3290 wireless card working?
[/URL][[ubuntu] Upgrade 12.04 to 14.04 - wifi frequently disconnects with no auto reconnect]("http://ubuntuforums.org/showthread.php?t=2219917")
[Wifi keeps disconnecting and extremely slow at low signal Ubuntu 13.04 - Ubuntu4questions Blog]("https://ubuntu4questions.wordpress.com/2015/05/07/wifi-keeps-disconnecting-and-extremely-slow-at-low-signal-ubuntu-13-04/")
[Unstable wifi connection after 14.04 upgrade]("http://ubuntuforums.org/showthread.php?t=2219014")
[ubuntu 14.04 wireless constantly disconnects]("http://askubuntu.com/questions/457729/ubuntu-14-04-wireless-constantly-disconnects")
and some others, I have seen many solutions, but I can not know what is suitable for my case.

I disabled (ignore) IPV6 at Network Manager.
Restart NetworkManager


I also do
```
sudo apt-get update;sudo apt-get dist-upgrade
```


```

########## wireless info START ##########

Report from: 21 Mar 2016 00:52 VET -0430

Booted last: 20 Mar 2016 21:24 VET -0430

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-83-generic #127-Ubuntu SMP Fri Mar 11 00:25:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. Device [105b:e055]
    Kernel driver in use: rt2800pci

04:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:570c Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              630728  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  1 nouveau
video                  19476  3 i915,nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi

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
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93332482 (93.3 MB)  TX bytes:19245939 (19.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ollysgonzalez"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ollysgonzalez' [AC1]>   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:213  Invalid misc:299   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      6831     1  0 Mar20 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

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

- Device: wlan0  [ollysgonzalez] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
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
    *ollysgonzalez:  Infra, <MAC 'ollysgonzalez' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 71 WPA WPA2
    FamilyRodriguez2:Infra, <MAC 'FamilyRodriguez2' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2

  IPv4 Settings:
    Address:         192.168.1.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             200.44.32.12
    DNS:             200.109.78.12

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
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ollysgonzalez]] (600 root)
[connection] id=ollysgonzalez | type=802-11-wireless
[802-11-wireless] ssid=ollysgonzalez | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Caracas (based on set time zone)

country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ollysgonzalez' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"ollysgonzalez"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000399b9e0370
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FamilyRodriguez2' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"FamilyRodriguez2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000829343e
                    Extra: Last beacon: 256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C88E1E4BD840C950F493E4
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A6B5D01725492005F5918FA
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1B9A9CB4CAAB78DFE7974EA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-83-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     05D0444BE5CC949584FB8E4
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-83-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-83-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        18:CE:1F:FC:4C:EF:B7:29:B5:A2:97:0C:A4:C2:7A:A4:8D:EB:F3:06
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0'  [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan0"

##### dmesg #############################

[10547.730036]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.110 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=33331 PROTO=TCP SPT=443 DPT=43635  WINDOW=0 RES=0x00 RST URGP=0 
[10575.045748] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.162 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=51 ID=42581 PROTO=TCP SPT=443 DPT=58751 WINDOW=0 RES=0x00  RST URGP=0 
[10575.046231] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.162 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=51  ID=42582 PROTO=TCP SPT=443 DPT=58751 WINDOW=0 RES=0x00 RST URGP=0 
[10597.254759]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.69 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=24405 PROTO=TCP SPT=443 DPT=45152  WINDOW=0 RES=0x00 RST URGP=0 
[10602.684726] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[10676.081994] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.78 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=28664 PROTO=TCP SPT=443 DPT=50833 WINDOW=0 RES=0x00 RST URGP=0 
[10676.083982]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.78 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=28665 PROTO=TCP SPT=443 DPT=50833  WINDOW=0 RES=0x00 RST URGP=0 
[10679.887632] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=209.85.200.94 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=41 ID=31451 PROTO=TCP SPT=443 DPT=35780 WINDOW=0 RES=0x00  RST URGP=0 
[10679.888777] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=209.85.200.94 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=41  ID=31452 PROTO=TCP SPT=443 DPT=35780 WINDOW=0 RES=0x00 RST URGP=0 
[10728.789622]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36  TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[10744.308805] [UFW BLOCK]  IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.69 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=53 ID=30951 PROTO=TCP SPT=443 DPT=45174 WINDOW=0 RES=0x00  RST URGP=0 
[10744.309412] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.69 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=30953 PROTO=TCP SPT=443 DPT=45174 WINDOW=0 RES=0x00 RST URGP=0 
[10833.755077]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.219.130 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=16332 PROTO=TCP SPT=443 DPT=56254  WINDOW=0 RES=0x00 RST URGP=0 
[10833.755573] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.130 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=16333 PROTO=TCP SPT=443 DPT=56254 WINDOW=0 RES=0x00  RST URGP=0 
[10854.887414] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1  DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[10870.074870]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.110 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=53998 PROTO=TCP SPT=443 DPT=43756  WINDOW=0 RES=0x00 RST URGP=0 
[10899.654296] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.101 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=53 ID=35393 PROTO=TCP SPT=443 DPT=33157 WINDOW=0 RES=0x00  RST URGP=0 
[10899.655012] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.101 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=35395 PROTO=TCP SPT=443 DPT=33157 WINDOW=0 RES=0x00 RST URGP=0 
[10913.997351]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=41331 PROTO=TCP SPT=443 DPT=38312  WINDOW=0 RES=0x00 RST URGP=0 
[10913.998304] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=51 ID=41332 PROTO=TCP SPT=443 DPT=38312 WINDOW=0 RES=0x00  RST URGP=0 
[10941.836550] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.78 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=26641 PROTO=TCP SPT=443 DPT=50999 WINDOW=0 RES=0x00 RST URGP=0 
[10941.838246]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.78 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=26642 PROTO=TCP SPT=443 DPT=50999  WINDOW=0 RES=0x00 RST URGP=0 
[10953.873455] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=74.125.141.156 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=43 ID=50105 PROTO=TCP SPT=443 DPT=42295 WINDOW=0 RES=0x00  RST URGP=0 
[10953.874806] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=74.125.141.156 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=43  ID=50106 PROTO=TCP SPT=443 DPT=42295 WINDOW=0 RES=0x00 RST URGP=0 
[10963.097177]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=74.125.141.95 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=43 ID=53959 PROTO=TCP SPT=443 DPT=50324  WINDOW=0 RES=0x00 RST URGP=0 
[10971.626272] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.162 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=51 ID=6727 PROTO=TCP SPT=443 DPT=59026 WINDOW=0 RES=0x00  RST URGP=0 
[10980.988642] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1  DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[11035.346199]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=6848 PROTO=TCP SPT=443 DPT=38528  WINDOW=0 RES=0x00 RST URGP=0 
[11035.348777] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=51 ID=6849 PROTO=TCP SPT=443 DPT=38528 WINDOW=0 RES=0x00  RST URGP=0 
[11035.350488] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=51  ID=6850 PROTO=TCP SPT=443 DPT=38528 WINDOW=0 RES=0x00 RST URGP=0 
[11046.985361]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.219.133 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=58838 PROTO=TCP SPT=443 DPT=60260  WINDOW=0 RES=0x00 RST URGP=0 
[11071.833030] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.78 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=53 ID=47895 PROTO=TCP SPT=443 DPT=51252 WINDOW=0 RES=0x00  RST URGP=0 
[11100.084013] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.78 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=6869 PROTO=TCP SPT=443 DPT=51256 WINDOW=0 RES=0x00 RST URGP=0 
[11107.090121]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36  TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[11131.296223] [UFW BLOCK]  IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.208.163 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=46 ID=495 PROTO=TCP SPT=443 DPT=34180 WINDOW=0 RES=0x00  RST URGP=0 
[11199.107950] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.133 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=22624 PROTO=TCP SPT=443 DPT=60300 WINDOW=0 RES=0x00 RST URGP=0 
[11199.110757]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.219.133 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=22626 PROTO=TCP SPT=443 DPT=60300  WINDOW=0 RES=0x00 RST URGP=0 
[11199.112320] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.133 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=22627 PROTO=TCP SPT=443 DPT=60300 WINDOW=0 RES=0x00  RST URGP=0 
[11215.084992] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.110 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=58917 PROTO=TCP SPT=443 DPT=44109 WINDOW=0 RES=0x00 RST URGP=0 
[11215.086690]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.110 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=58918 PROTO=TCP SPT=443 DPT=44109  WINDOW=0 RES=0x00 RST URGP=0 
[11233.191209] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[11247.320161] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.78 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=27693 PROTO=TCP SPT=443 DPT=36345 WINDOW=0 RES=0x00 RST URGP=0 
[11277.268584]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=719 PROTO=TCP SPT=443 DPT=38613  WINDOW=0 RES=0x00 RST URGP=0 
[11277.270938] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=720 PROTO=TCP SPT=443 DPT=38613 WINDOW=0 RES=0x00  RST URGP=0 
[11293.084543] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.142 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=18027 PROTO=TCP SPT=443 DPT=45074 WINDOW=0 RES=0x00 RST URGP=0 
[11347.439305]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.101 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=40089 PROTO=TCP SPT=443 DPT=33490  WINDOW=0 RES=0x00 RST URGP=0 
[11347.442231] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.101 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=53 ID=40090 PROTO=TCP SPT=443 DPT=33490 WINDOW=0 RES=0x00  RST URGP=0 
[11347.443866] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.101 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=40091 PROTO=TCP SPT=443 DPT=33490 WINDOW=0 RES=0x00 RST URGP=0 
[11359.292678]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36  TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2  (repeated 2 times)
[11607.284707]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.219.142 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=39712 PROTO=TCP SPT=443 DPT=45107  WINDOW=0 RES=0x00 RST URGP=0 
[11607.287143] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.142 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=53 ID=39714 PROTO=TCP SPT=443 DPT=45107 WINDOW=0 RES=0x00  RST URGP=0 
[11611.495226] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1  DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[11648.151256]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.101 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=8149 PROTO=TCP SPT=443 DPT=33511  WINDOW=0 RES=0x00 RST URGP=0 
[11737.596630] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[11743.521113] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=192.168.1.1 DST=192.168.1.109 LEN=294 TOS=0x00 PREC=0x00 TTL=64  ID=23047 PROTO=UDP SPT=1900 DPT=41045 LEN=274 
[11745.486109] [UFW  BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0'  [IF]>:e0:b9:a5:63:b5:c7:08:00 SRC=192.168.1.107 DST=192.168.1.109  LEN=424 TOS=0x00 PREC=0x00 TTL=128 ID=19447 PROTO=UDP SPT=1900 DPT=41045  LEN=404 
[11820.394067] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.78 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=57179 PROTO=TCP SPT=443 DPT=51350 WINDOW=0 RES=0x00 RST URGP=0 
[11820.394838]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.78 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=57181 PROTO=TCP SPT=443 DPT=51350  WINDOW=0 RES=0x00 RST URGP=0 
[11863.697956] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[11907.120512] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.66 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=49958 PROTO=TCP SPT=443 DPT=44963 WINDOW=0 RES=0x00 RST URGP=0 
[11939.708851]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=42223 PROTO=TCP SPT=443 DPT=44972  WINDOW=0 RES=0x00 RST URGP=0 
[11939.709360] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=42225 PROTO=TCP SPT=443 DPT=44972 WINDOW=0 RES=0x00  RST URGP=0 
[11949.643847] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.101 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=4631 PROTO=TCP SPT=443 DPT=33555 WINDOW=0 RES=0x00 RST URGP=0 
[11949.645587]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.101 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=4632 PROTO=TCP SPT=443 DPT=33555  WINDOW=0 RES=0x00 RST URGP=0 
[11989.799096] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[12049.791653] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.131 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=31953 PROTO=TCP SPT=443 DPT=54837 WINDOW=0 RES=0x00 RST URGP=0 
[12057.784174]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=42268 PROTO=TCP SPT=443 DPT=45002  WINDOW=0 RES=0x00 RST URGP=0 
[12057.786666] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=42270 PROTO=TCP SPT=443 DPT=45002 WINDOW=0 RES=0x00  RST URGP=0 
[12057.787650] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.66 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=42271 PROTO=TCP SPT=443 DPT=45002 WINDOW=0 RES=0x00 RST URGP=0 
[12060.803422]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.219.65 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=16271 PROTO=TCP SPT=443 DPT=58334  WINDOW=0 RES=0x00 RST URGP=0 
[12060.805856] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.65 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=51 ID=16272 PROTO=TCP SPT=443 DPT=58334 WINDOW=0 RES=0x00  RST URGP=0 
[12060.807907] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.65 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=51  ID=16275 PROTO=TCP SPT=443 DPT=58334 WINDOW=0 RES=0x00 RST URGP=0 
[12064.775139]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=24340 PROTO=TCP SPT=443 DPT=45012  WINDOW=0 RES=0x00 RST URGP=0 
[12064.777870] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=53 ID=24341 PROTO=TCP SPT=443 DPT=45012 WINDOW=0 RES=0x00  RST URGP=0 
[12064.779742] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.66 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=24342 PROTO=TCP SPT=443 DPT=45012 WINDOW=0 RES=0x00 RST URGP=0 
[12074.027609]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=11635 PROTO=TCP SPT=443 DPT=44998  WINDOW=0 RES=0x00 RST URGP=0 
[12115.900657] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[12120.644447] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.163 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=59742 PROTO=TCP SPT=443 DPT=55728 WINDOW=0 RES=0x00 RST URGP=0 
[12163.215975]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=74.125.141.190 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=44 ID=62553 PROTO=TCP SPT=443 DPT=39599  WINDOW=0 RES=0x00 RST URGP=0 
[12164.216401] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.142 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=34863 PROTO=TCP SPT=443 DPT=45231 WINDOW=0 RES=0x00  RST URGP=0 
[12164.218255] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.142 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=34864 PROTO=TCP SPT=443 DPT=45231 WINDOW=0 RES=0x00 RST URGP=0 
[12179.272755]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.78 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=13565 PROTO=TCP SPT=443 DPT=51452  WINDOW=0 RES=0x00 RST URGP=0 
[12239.980233] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=200.44.26.34 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=58 ID=11193 DF PROTO=TCP SPT=443 DPT=35127 WINDOW=0  RES=0x00 RST URGP=0 
[12241.946836] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.219.67 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=51  ID=7742 PROTO=TCP SPT=443 DPT=33891 WINDOW=0 RES=0x00 RST URGP=0 
[12242.001710]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36  TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[12256.911202] [UFW BLOCK]  IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=1724 PROTO=TCP SPT=443 DPT=38779 WINDOW=0 RES=0x00  RST URGP=0 
[12256.912152] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=1727 PROTO=TCP SPT=443 DPT=38779 WINDOW=0 RES=0x00 RST URGP=0 
[12304.209396]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.66 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=62584 PROTO=TCP SPT=443 DPT=45076  WINDOW=0 RES=0x00 RST URGP=0 
[12362.014306] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=19812 PROTO=TCP SPT=443 DPT=38821 WINDOW=0 RES=0x00  RST URGP=0 
[12362.016246] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC  'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.67 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=52  ID=19813 PROTO=TCP SPT=443 DPT=38821 WINDOW=0 RES=0x00 RST URGP=0 
[12362.018053]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.67 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=19814 PROTO=TCP SPT=443 DPT=38821  WINDOW=0 RES=0x00 RST URGP=0 
[12368.103035] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00  TTL=1 ID=0 PROTO=2 
[12400.937151] [UFW BLOCK] IN=wlan0 OUT=  MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez' [AC1]>:08:00  SRC=216.58.192.69 DST=192.168.1.109 LEN=40 TOS=0x00 PREC=0x00 TTL=53  ID=63287 PROTO=TCP SPT=443 DPT=45797 WINDOW=0 RES=0x00 RST URGP=0 
[12441.713171]  [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC  'ollysgonzalez' [AC1]>:08:00 SRC=216.58.192.78 DST=192.168.1.109  LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=22357 PROTO=TCP SPT=443 DPT=51505  WINDOW=0 RES=0x00 RST URGP=0 
[12482.801790] [UFW BLOCK] IN=wlan0  OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'ollysgonzalez'  [AC1]>:08:00 SRC=216.58.219.131 DST=192.168.1.109 LEN=40 TOS=0x00  PREC=0x00 TTL=52 ID=12557 PROTO=TCP SPT=443 DPT=54959 WINDOW=0 RES=0x00  RST URGP=0 

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-03-21
Disable UFW and see if it works better as it appears to be blocking mDNS

---

### Post by jesusguevarautomotriz on 2016-03-21
I do

```
$ sudo ufw disable.
```

I, waiting behavior

---

### Post by jesusguevarautomotriz on 2016-03-21
I was disconnected again, it tries to connect but never achieved.
I do, 

```
sudo service network-manager restart
```


and after several attempts connect again, but remains very unstable
Some outputs

```
[43918.609581] wlan0: authenticate with e4:d3:32:7b:0e:90
[43918.625408] wlan0: send auth to e4:d3:32:7b:0e:90 (try 1/3)
[43918.666451] wlan0: send auth to e4:d3:32:7b:0e:90 (try 2/3)
[43918.712977] wlan0: send auth to e4:d3:32:7b:0e:90 (try 3/3)
[43918.748067] wlan0: authentication with e4:d3:32:7b:0e:90 timed out
[43920.815355] wlan0: authenticate with e4:d3:32:7b:0e:90
[43920.831178] wlan0: send auth to e4:d3:32:7b:0e:90 (try 1/3)
[43920.872742] wlan0: send auth to e4:d3:32:7b:0e:90 (try 2/3)
[43920.906246] wlan0: send auth to e4:d3:32:7b:0e:90 (try 3/3)
[43920.946861] wlan0: authentication with e4:d3:32:7b:0e:90 timed out
[43933.077107] wlan0: authenticate with e4:d3:32:7b:0e:90
[43933.092951] wlan0: send auth to e4:d3:32:7b:0e:90 (try 1/3)
[43933.111263] wlan0: send auth to e4:d3:32:7b:0e:90 (try 2/3)
[43933.150453] wlan0: send auth to e4:d3:32:7b:0e:90 (try 3/3)
[43933.186284] wlan0: authentication with e4:d3:32:7b:0e:90 timed out
[43944.193437] wlan0: authenticate with e4:d3:32:7b:0e:90
[43944.197856] wlan0: send auth to e4:d3:32:7b:0e:90 (try 1/3)
[43944.217696] wlan0: send auth to e4:d3:32:7b:0e:90 (try 2/3)
[43944.243170] wlan0: send auth to e4:d3:32:7b:0e:90 (try 3/3)
[43944.282115] wlan0: authentication with e4:d3:32:7b:0e:90 timed out


```

and 

```
[44128.171616] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[44128.171619] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44128.171621] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44128.171622] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[44128.171624] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44128.171625] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44129.310286] wlan0: authenticate with e4:d3:32:7b:0e:90
[44129.326099] wlan0: send auth to e4:d3:32:7b:0e:90 (try 1/3)
[44129.328108] wlan0: authenticated
[44129.330007] wlan0: associate with e4:d3:32:7b:0e:90 (try 1/3)
[44129.333853] wlan0: RX AssocResp from e4:d3:32:7b:0e:90 (capab=0x431 status=0 aid=3)
[44129.333951] wlan0: associated
[44129.334093] cfg80211: Calling CRDA for country: CN
[44129.338647] cfg80211: Regulatory domain changed to country: CN
[44129.338654] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[44129.338658] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[44129.338662] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[44129.338665] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[44129.338668] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm)
[44129.338671] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm)


```

---

### Post by jeremy31 on 2016-03-21
There are a few issues, your country code is set to China when it appears that you are  in Venezuela
```
sudo iw reg set VE
sudo sed -i 's/^REG.*=$/&VE/' /etc/default/crda
```

I don't remember seeing the NetworkManager.conf quite like yours
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo sed -i 's/managed=true/managed=false/' /etc/NetworkManager/NetworkManager.conf
```

Reboot[/FONT][/COLOR]

---

### Post by jesusguevarautomotriz on 2016-03-21
Changes applied waiting behavior.

Here is my

/etc/network/interfaces

```

# interfaces(5) file used by ifup(8) and ifdown(8) 
auto lo 
iface lo inet loopback

```

I should put something like this? What should be the correct setting?

```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhc

```

---

### Post by jesusguevarautomotriz on 2016-03-22
Thank you very much for all your answers.

Moments after making the changes I had two disconnections. From then until now seems to be stable, they can leave the topic open a few days and then then mark it as SOLVED.

---

### Post by jesusguevarautomotriz on 2016-03-24
Now my WIFI connection seems to be much more stable than before, but still Keeps disconnecting, now a few times within a day, my last record have been in a range of 5 hours plus or minus.

---

