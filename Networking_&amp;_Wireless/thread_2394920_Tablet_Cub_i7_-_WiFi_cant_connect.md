---
title: "Tablet Cub i7 - WiFi cant connect"
date: 2018-06-23
forum: Networking &amp; Wireless
---

### Post by trucho2020 on 2018-06-23
Hello guys
I just installed Lubuntu 18.04 in my Cube i& but I can't connect to the WiFi (same problem with Android 7.1.2 and 8.1RC)
Android gave me Authentication Erroro and it was impossible to log in.
Lubuntu can't connect either but no message

Here is the wireless_infor.txt script

```

########## wireless info START ##########

Report from: 23 Jun 2018 14:29 MDT -0600

Booted last: 23 Jun 2018 00:00 MDT -0600

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Lubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:5830 Realtek Semiconductor Corp. 
Bus 001 Device 021: ID 0911:2188 Philips Speech Processing 
Bus 001 Device 025: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 019: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 009: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 013: ID 0bda:5875 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
cfg80211              622592  1 mac80211

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
3: wlx<IF from MAC [IF1]>: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF1]>' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       520     1  0 13:35 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.15.0-20-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.2/net/wlx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,3,4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1c4444c4-9867-4a6f-9f79-77cfbc2eea48 | Tricolor-2.4G
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   781ec5cc-4808-4234-9a75-388af16c6608 | DD-WRT-2.4G
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   7a8c5816-adef-4611-a73b-04804b996bde | Tricolor-2.4G 1

SSID           BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
DD-WRT-2.4G    <MAC 'DD-WRT-2.4G' [AC1]>  Infra  6     2437 MHz  195 Mbit/s  67      â–‚â–„â–†_  WPA2       no             
Tricolor-2.4G  <MAC 'Tricolor-2.4G' [AC2]>  Infra  1     2412 MHz  195 Mbit/s  64      â–‚â–„â–†_  WPA1 WPA2  no             

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Tricolor-2.4G]] (600 root)
[connection] id=Tricolor-2.4G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Tricolor-2.4G
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DD-WRT-2.4G]] (600 root)
[connection] id=DD-WRT-2.4G | type=wifi | permissions=user:marcel:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=DD-WRT-2.4G
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Tricolor-2.4G 1]] (600 root)
[connection] id=Tricolor-2.4G 1 | type=wifi | permissions=user:marcel:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Tricolor-2.4G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Edmonton (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlx<IF from MAC [IF1]>  14 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'DD-WRT-2.4G' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"DD-WRT-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000286e6469f
                    Extra: Last beacon: 636ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Tricolor-2.4G' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Tricolor-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000062cfac3180
                    Extra: Last beacon: 904ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@gmail.com>
srcversion:     E7E78FAA920143C9B0CB35A
depends:        mac80211
retpoline:      Y
intree:         Y
name:           rtl8xxxu
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1775.679975] wlx<IF from MAC [IF1]>: authentication with <MAC 'DD-WRT-2.4G' [AC1]> timed out
[ 1777.749263] wlx<IF from MAC [IF1]>: authenticate with <MAC 'DD-WRT-2.4G' [AC1]>
[ 1777.753120] wlx<IF from MAC [IF1]>: send auth to <MAC 'DD-WRT-2.4G' [AC1]> (try 1/3)
[ 1777.955938] wlx<IF from MAC [IF1]>: send auth to <MAC 'DD-WRT-2.4G' [AC1]> (try 2/3)
[ 1778.159956] wlx<IF from MAC [IF1]>: send auth to <MAC 'DD-WRT-2.4G' [AC1]> (try 3/3)
[ 1778.363958] wlx<IF from MAC [IF1]>: authentication with <MAC 'DD-WRT-2.4G' [AC1]> timed out
[ 1788.441394] wlx<IF from MAC [IF1]>: authenticate with <MAC 'DD-WRT-2.4G' [AC1]>
[ 1788.443547] wlx<IF from MAC [IF1]>: send auth to <MAC 'DD-WRT-2.4G' [AC1]> (try 1/3)
[ 1788.644039] wlx<IF from MAC [IF1]>: send auth to <MAC 'DD-WRT-2.4G' [AC1]> (try 2/3)
[ 1788.847989] wlx<IF from MAC [IF1]>: send auth to <MAC 'DD-WRT-2.4G' [AC1]> (try 3/3)
[ 1789.052039] wlx<IF from MAC [IF1]>: authentication with <MAC 'DD-WRT-2.4G' [AC1]> timed out
[ 1796.006572] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF1]>: link is not ready
[ 2429.561153] wlx<IF from MAC [IF1]>: authenticate with <MAC 'Tricolor-2.4G' [AC2]>
[ 2429.564995] wlx<IF from MAC [IF1]>: send auth to <MAC 'Tricolor-2.4G' [AC2]> (try 1/3)
[ 2429.768014] wlx<IF from MAC [IF1]>: send auth to <MAC 'Tricolor-2.4G' [AC2]> (try 2/3)
[ 2429.972018] wlx<IF from MAC [IF1]>: send auth to <MAC 'Tricolor-2.4G' [AC2]> (try 3/3)
[ 2430.176000] wlx<IF from MAC [IF1]>: authentication with <MAC 'Tricolor-2.4G' [AC2]> timed out
[ 2441.245394] wlx<IF from MAC [IF1]>: authenticate with <MAC 'Tricolor-2.4G' [AC2]>
[ 2441.251520] wlx<IF from MAC [IF1]>: send auth to <MAC 'Tricolor-2.4G' [AC2]> (try 1/3)
[ 2441.452012] wlx<IF from MAC [IF1]>: send auth to <MAC 'Tricolor-2.4G' [AC2]> (try 2/3)
[ 2441.656019] wlx<IF from MAC [IF1]>: send auth to <MAC 'Tricolor-2.4G' [AC2]> (try 3/3)
[ 2441.859914] wlx<IF from MAC [IF1]>: authentication with <MAC 'Tricolor-2.4G' [AC2]> timed out
[ 2454.008653] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF1]>: link is not ready

########## wireless info END ############



```

---

