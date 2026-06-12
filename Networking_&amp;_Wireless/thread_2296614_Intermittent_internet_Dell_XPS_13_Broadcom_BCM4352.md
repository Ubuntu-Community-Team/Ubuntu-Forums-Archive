---
title: "Intermittent internet Dell XPS 13 Broadcom BCM4352 Ubuntu 14.04"
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by momchil3 on 2015-09-27
Dear all,

I have tried everything described in the two sticky pages on top of this forum, and I keep having the same problem, so I resort to writing a message.

Basically, I connect to my home wireless, and I constantly stay connected to the network, *however*, the connection to the internet is intermittent. Every 5-10 minutes it's gone or very slow for a minute or two. This is an illustration:

```

ping -i 5 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=25 ttl=55 time=9.33 ms
64 bytes from 8.8.8.8: icmp_seq=26 ttl=55 time=9.53 ms
64 bytes from 8.8.8.8: icmp_seq=27 ttl=55 time=9.97 ms
64 bytes from 8.8.8.8: icmp_seq=28 ttl=55 time=9.01 ms
64 bytes from 8.8.8.8: icmp_seq=29 ttl=55 time=9.52 ms
64 bytes from 8.8.8.8: icmp_seq=30 ttl=55 time=9.77 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=55 time=9.44 ms
64 bytes from 8.8.8.8: icmp_seq=38 ttl=55 time=2139 ms
64 bytes from 8.8.8.8: icmp_seq=39 ttl=55 time=2651 ms
64 bytes from 8.8.8.8: icmp_seq=40 ttl=55 time=686 ms
64 bytes from 8.8.8.8: icmp_seq=41 ttl=55 time=1270 ms
64 bytes from 8.8.8.8: icmp_seq=42 ttl=55 time=21.9 ms
64 bytes from 8.8.8.8: icmp_seq=43 ttl=55 time=30.3 ms
64 bytes from 8.8.8.8: icmp_seq=44 ttl=55 time=22.0 ms
64 bytes from 8.8.8.8: icmp_seq=45 ttl=55 time=11.6 ms
64 bytes from 8.8.8.8: icmp_seq=46 ttl=55 time=9.67 ms
64 bytes from 8.8.8.8: icmp_seq=47 ttl=55 time=9.77 ms
64 bytes from 8.8.8.8: icmp_seq=48 ttl=55 time=9.84 ms
```

I know that this is not related to my service since it never happens under windows (nor to my flatmates). 

I have run the wireless-info script provided here twice, when everything is running fine:

```
 

########## wireless info START ##########


Report from: 27 Sep 2015 14:36 CEST +0200


Booted last: 27 Sep 2015 14:35 CEST +0200


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0c45:670c Microdia 
Bus 001 Device 003: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0 
snd_soc_rt286          32768  1 snd_soc_sst_broadwell
sparse_keymap          16384  1 dell_wmi
snd_soc_core          196608  3 snd_soc_sst_haswell_pcm,snd_soc_sst_broadwell,snd_soc_rt286
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
wl                   6369280  0 
cfg80211              524288  1 wl
snd_pcm               106496  8 snd_soc_core,snd_hda_codec_hdmi,snd_soc_sst_haswell_pcm,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 dell_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.33  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1686 errors:0 dropped:0 overruns:0 frame:4748
          TX packets:1578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1237918 (1.2 MB)  TX bytes:247335 (247.3 KB)
          Interrupt:19 


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"WN-5363C5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WN-5363C5' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       822     1  0 14:35 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [WN-5363C5] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           117 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Ali:             Infra, <MAC 'Ali' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    PLD-21547:       Infra, <MAC 'PLD-21547' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Laus Dreamteam:  Infra, <MAC 'Laus Dreamteam' [AC4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Ali:             Infra, <MAC 'Ali' [AN4]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    ASUS:            Infra, <MAC 'ASUS' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    *WN-5363C5:      Infra, <MAC 'WN-5363C5' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2


  IPv4 Settings:
    Address:         192.168.0.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254


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


[[/etc/NetworkManager/system-connections/FREE_MONTE_VERITA]] (600 root)
[connection] id=FREE_MONTE_VERITA | type=802-11-wireless
[802-11-wireless] ssid=FREE_MONTE_VERITA | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Sumner]] (600 root)
[connection] id=Sumner | type=802-11-wireless
[802-11-wireless] ssid=Sumner | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ApartamentA214]] (600 root)
[connection] id=ApartamentA214 | type=802-11-wireless
[802-11-wireless] ssid=ApartamentA214 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/blauw_huis]] (600 root)
[connection] id=blauw_huis | type=802-11-wireless
[802-11-wireless] ssid=blauw_huis | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Momo]] (600 root)
[connection] id=Momo | type=802-11-wireless
[802-11-wireless] ssid=Momo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/epfl]] (600 root)
[ipv6] method=auto
[connection] id=epfl | type=802-11-wireless
[802-11-wireless] ssid=epfl | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/entypo]] (600 root)
[connection] id=entypo | type=802-11-wireless
[802-11-wireless] ssid=entypo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BRXXL5]] (600 root)
[connection] id=BRXXL5 | type=802-11-wireless
[802-11-wireless] ssid=BRXXL5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WN-5363C5]] (600 root)
[connection] id=WN-5363C5 | type=802-11-wireless
[802-11-wireless] ssid=WN-5363C5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/M-Tel_39B2]] (600 root)
[connection] id=M-Tel_39B2 | type=802-11-wireless
[802-11-wireless] ssid=M-Tel_39B2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Academy - 6597]] (600 root)
[connection] id=Academy - 6597 | type=802-11-wireless
[802-11-wireless] ssid=Academy - 6597 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz
          Channel 96 : 5.48 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'WN-5363C5' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"WN-5363C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Ali' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Ali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'PLD-21547' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"PLD-21547"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Laus Dreamteam' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Laus Dreamteam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/3.19.0-28-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6897BDA643816808DF92DC2
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
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


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


rfkill block bluetooth


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/powersaverXPS13Vivid] (644 root)
if on_ac_power; then
  # Remount ext filesystems 
  mount -o remount,commit=5,atime /
  # Disable SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done
  # Set the Intel wifi to no power savings.
  iw dev wlan0 set power_save off
  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs
  # turn off pci runtime powermanagement
  for pcidev in /sys/bus/pci/devices/0000\:0*/power/control
    do echo on > $pcidev
  done
  # enable the NMI watchdog
  echo 1 > /proc/sys/kernel/watchdog
  # disable autosuspend for a USB dev
  echo on > /sys/bus/usb/devices/1-3/power/control
  
  # mess with the intel HDMI audio
  echo '1' > '/sys/module/snd_hda_intel/parameters/power_save'
else # Save power, we are on battery
  # remount the file system to reduce journaling
  mount -o remount,commit=180,relatime /
  # SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done
  # Set the Intel wifi to power savings.
  iw dev wlan0 set power_save on
  # Set kernel dirty page value to higher numbers
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
  # turn on pci runtime powermanagement
  for pcidev in /sys/bus/pci/devices/0000\:0*/power/control
    do echo auto > $pcidev
  done
  # disable the NMI watchdog
  echo 0 > /proc/sys/kernel/watchdog
  # enable autosuspend for a USB dev
  echo auto > /sys/bus/usb/devices/1-3/power/control
  
  # mess with the intel HDMI audio
  echo '' > '/sys/module/snd_hda_intel/parameters/power_save'
fi


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    1.872748] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    1.880234] rt286 i2c-INT343A:00: Device with ID register 10ec0288 is not rt286
[    1.923988] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    1.923993] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[   83.704494] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############
```

and when it's not:

```



########## wireless info START ##########


Report from: 27 Sep 2015 14:39 CEST +0200


Booted last: 27 Sep 2015 14:35 CEST +0200


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0c45:670c Microdia 
Bus 001 Device 003: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0 
snd_soc_rt286          32768  1 snd_soc_sst_broadwell
sparse_keymap          16384  1 dell_wmi
snd_soc_core          196608  3 snd_soc_sst_haswell_pcm,snd_soc_sst_broadwell,snd_soc_rt286
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
wl                   6369280  0 
cfg80211              524288  1 wl
snd_pcm               106496  8 snd_soc_core,snd_hda_codec_hdmi,snd_soc_sst_haswell_pcm,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 dell_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.33  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5563 errors:0 dropped:0 overruns:0 frame:10367
          TX packets:4780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5168033 (5.1 MB)  TX bytes:826096 (826.0 KB)
          Interrupt:19 


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"WN-5363C5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WN-5363C5' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       822     1  0 14:35 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [WN-5363C5] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           117 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Ali:             Infra, <MAC 'Ali' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    PLD-21547:       Infra, <MAC 'PLD-21547' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Laus Dreamteam:  Infra, <MAC 'Laus Dreamteam' [AC2]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Ali:             Infra, <MAC 'Ali' [AN4]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    ASUS:            Infra, <MAC 'ASUS' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    *WN-5363C5:      Infra, <MAC 'WN-5363C5' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2


  IPv4 Settings:
    Address:         192.168.0.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254


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


[[/etc/NetworkManager/system-connections/FREE_MONTE_VERITA]] (600 root)
[connection] id=FREE_MONTE_VERITA | type=802-11-wireless
[802-11-wireless] ssid=FREE_MONTE_VERITA | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Sumner]] (600 root)
[connection] id=Sumner | type=802-11-wireless
[802-11-wireless] ssid=Sumner | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ApartamentA214]] (600 root)
[connection] id=ApartamentA214 | type=802-11-wireless
[802-11-wireless] ssid=ApartamentA214 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/blauw_huis]] (600 root)
[connection] id=blauw_huis | type=802-11-wireless
[802-11-wireless] ssid=blauw_huis | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Momo]] (600 root)
[connection] id=Momo | type=802-11-wireless
[802-11-wireless] ssid=Momo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/epfl]] (600 root)
[ipv6] method=auto
[connection] id=epfl | type=802-11-wireless
[802-11-wireless] ssid=epfl | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/entypo]] (600 root)
[connection] id=entypo | type=802-11-wireless
[802-11-wireless] ssid=entypo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BRXXL5]] (600 root)
[connection] id=BRXXL5 | type=802-11-wireless
[802-11-wireless] ssid=BRXXL5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WN-5363C5]] (600 root)
[connection] id=WN-5363C5 | type=802-11-wireless
[802-11-wireless] ssid=WN-5363C5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/M-Tel_39B2]] (600 root)
[connection] id=M-Tel_39B2 | type=802-11-wireless
[802-11-wireless] ssid=M-Tel_39B2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Academy - 6597]] (600 root)
[connection] id=Academy - 6597 | type=802-11-wireless
[802-11-wireless] ssid=Academy - 6597 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz
          Channel 96 : 5.48 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'WN-5363C5' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"WN-5363C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Laus Dreamteam' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Laus Dreamteam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 21304ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Ali' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Ali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'PLD-21547' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"PLD-21547"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/3.19.0-28-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6897BDA643816808DF92DC2
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
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


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


rfkill block bluetooth


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/powersaverXPS13Vivid] (644 root)
if on_ac_power; then
  # Remount ext filesystems 
  mount -o remount,commit=5,atime /
  # Disable SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done
  # Set the Intel wifi to no power savings.
  iw dev wlan0 set power_save off
  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs
  # turn off pci runtime powermanagement
  for pcidev in /sys/bus/pci/devices/0000\:0*/power/control
    do echo on > $pcidev
  done
  # enable the NMI watchdog
  echo 1 > /proc/sys/kernel/watchdog
  # disable autosuspend for a USB dev
  echo on > /sys/bus/usb/devices/1-3/power/control
  
  # mess with the intel HDMI audio
  echo '1' > '/sys/module/snd_hda_intel/parameters/power_save'
else # Save power, we are on battery
  # remount the file system to reduce journaling
  mount -o remount,commit=180,relatime /
  # SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done
  # Set the Intel wifi to power savings.
  iw dev wlan0 set power_save on
  # Set kernel dirty page value to higher numbers
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
  # turn on pci runtime powermanagement
  for pcidev in /sys/bus/pci/devices/0000\:0*/power/control
    do echo auto > $pcidev
  done
  # disable the NMI watchdog
  echo 0 > /proc/sys/kernel/watchdog
  # enable autosuspend for a USB dev
  echo auto > /sys/bus/usb/devices/1-3/power/control
  
  # mess with the intel HDMI audio
  echo '' > '/sys/module/snd_hda_intel/parameters/power_save'
fi


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    1.872748] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    1.880234] rt286 i2c-INT343A:00: Device with ID register 10ec0288 is not rt286
[    1.923988] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    1.923993] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[   83.704494] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)


########## wireless info END ############
```

There are some differences, but I don't know what they mean.

Bottom line - help, please? It's pretty annoying and it has made me use Windows most of the time, which I really would rather not do. :)

---

### Post by TCP_RDG on 2015-10-30
Me too in the same boat. DELL XPS 13 (2015 model 9343). Hope someone help us with this

---

### Post by leith98b on 2016-01-28
I'm having the same problems.  Has anyone found a solution?  I'll post some of my wireless-info as well.

---

