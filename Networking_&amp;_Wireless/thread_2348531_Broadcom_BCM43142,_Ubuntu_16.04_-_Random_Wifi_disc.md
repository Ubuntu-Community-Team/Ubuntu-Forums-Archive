---
title: "Broadcom BCM43142, Ubuntu 16.04 - Random Wifi disconnections and OS freezes"
date: 2017-01-04
forum: Networking &amp; Wireless
---

### Post by rivendil on 2017-01-04
Hi. I´ve recently installed Ubuntu 16.04 LTS and noticed Wifi randomly disconnects and sometimes pc freezes completely (when using wifi).
I tried different solutions like the ones posted in the links below and other forums: 
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
However, none of these actually fixed the problem.

Below is the script output us suggested in [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Any ideas? Thanks.


```

########## wireless info START ##########

Report from: 04 Jan 2017 16:07 ART -0300

Booted last: 04 Jan 2017 00:00 ART -0300

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 03eb:8c1d Atmel Corp. 
Bus 001 Device 006: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 004: ID 1bcf:2c66 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
7: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
8: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              565248  1 wl
ideapad_laptop         24576  0
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
sparse_keymap          16384  1 ideapad_laptop
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
wmi                    20480  1 ideapad_laptop
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::bf2e:1f14:7123:70ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256153 errors:0 dropped:0 overruns:0 frame:4231
          TX packets:162827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358226560 (358.2 MB)  TX bytes:19106073 (19.1 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11abg  ESSID:"MiRedWifi"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'MiRedWifi' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2480     1  0 14:57 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MiRedWifi 
GENERAL.CON-UUID:                       d25eabef-422b-4529-94dd-b72ad1ffcf09
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     36 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d25eabef-422b-4529-94dd-b72ad1ffcf09 | MiRedWifi 
IP4.ADDRESS[1]:                         192.168.0.171/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             190.105.0.2
IP4.DNS[2]:                             190.105.0.3
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1483559341
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.171
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 190.105.0.2 190.105.0.3
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         fe80::bf2e:1f14:7123:70ee/64
IP6.GATEWAY:                            

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MiRedWifi  <MAC 'MiRedWifi' [AC2]>  Infra  10    2457 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
MiRedWifi  <MAC 'MiRedWifi' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       yes     * 

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

[[/etc/NetworkManager/system-connections/MiRedWifi]] (600 root)
[connection] id=MiRedWifi | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=MiRedWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MiRedWifi ]] (600 root)
[connection] id=MiRedWifi  | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=MiRedWifi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

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

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Current Frequency:2.457 GHz (Channel 10)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.457 GHz (Channel 10)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'MiRedWifi' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"MiRedWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MiRedWifi' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"MiRedWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
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
filename:       /lib/modules/4.4.0-57-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[  974.657962] wl 0000:01:00.0 wlp1s0: renamed from wlan0
[  974.748544] wlp1s0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[  974.779991] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  986.348992] wl 0000:01:00.0 wlp1s0: renamed from wlan0
[  986.448901] wlp1s0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[  986.479116] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[ 4234.391820] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by Hadaka on 2017-01-04
Hi, your wireless report indicates you have 2 connections named the 
same and on the same channel.
```
SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MiRedWifi  <MAC 'MiRedWifi' [AC2]>  Infra  10    2457 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
MiRedWifi  <MAC 'MiRedWifi' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       yes     * 
```
and the connections are not configured the same.. one has TKIP..that needs to be removed and configured for
AES CCMP...wpa2 ccmp and a different connection name...ssid...and not mixed mode.."WPA1 WPA2"
Currently your computer gets confused where to connect and freezes up because of this.
your reports shows your region as..America/Argentina/Buenos_Aires...*IF correct please copy and paste...
```
sudo iw reg set AR
sudo sed -i 's/=.*/=AR/' /etc/default/crda
```
finally this link shows the computer models that are compatible and certified for your wifi card
*IS Your Lenovo on the list ??..page3..
[https://certification.ubuntu.com/catalog/component/pci/14e4%3A4365/?&page=3](https://certification.ubuntu.com/catalog/component/pci/14e4%3A4365/?&page=3)
If after you make the changes to your router/ssid duplicate connection verify your Lenovo is on the list,
and are still having difficulties, please report back with a new fresh wireless report.
Thanks.

---

### Post by rivendil on 2017-01-04
> your reports shows your region as..America/Argentina/Buenos_Aires...*IF correct please copy and paste...
Indeed. I´m from Buenos Aires, Argentina.

> *IS Your Lenovo on the list ??..page3..
No it´s not. I have a Lenovo Yoga 2 11

> If after you make the changes to your router/ssid duplicate connection verify your Lenovo is on the list,
and are still having difficulties, please report back with a new fresh wireless report.
Thanks.
Okay. I will eliminate the duplicate connection and test how it goes. Then come back with the results.

Thanks!

---

### Post by rivendil on 2017-01-08
Update: Okay so I tested browsing with the new configuration. Actually, the duplicated connection was the wifi extender/booster I have in my house. I changed that connection so that it matches the configuration of the "real" connection. I also changed its ssid now called "MiRedWifiExt". The freezing seemed to stop. However, I still get random disconnections. Also, when I go to the wifi icon and click on "edit connections" I see several connections with the same name but increasing number (see image attached). I don´t know why that happens, I never added those connections.

Here is the result of the script:
```

########## wireless info START ##########

Report from: 08 Jan 2017 16:50 ART -0300

Booted last: 08 Jan 2017 00:00 ART -0300

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 03eb:8c1d Atmel Corp. 
Bus 001 Device 006: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 004: ID 1bcf:2c66 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
cfg80211              565248  1 wl
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::106b:8762:28ef:fa96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:558 errors:0 dropped:0 overruns:0 frame:865
          TX packets:623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225996 (225.9 KB)  TX bytes:100829 (100.8 KB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11abg  ESSID:"MiRedWifi"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'MiRedWifi' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2187     1  0 16:48 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MiRedWifi 1
GENERAL.CON-UUID:                       441a5e0b-c553-45b1-a710-8e5dd054e860
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   441a5e0b-c553-45b1-a710-8e5dd054e860 | MiRedWifi 1
IP4.ADDRESS[1]:                         192.168.0.105/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             190.105.0.2
IP4.DNS[2]:                             190.105.0.3
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1483908553
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.105
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 190.105.0.2 190.105.0.3
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         fe80::106b:8762:28ef:fa96/64
IP6.GATEWAY:                            

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Motorola      <MAC 'Motorola' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
MiRedWifi     <MAC 'MiRedWifi' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2      yes     * 
MiRedWifiExt  <MAC 'MiRedWifiExt' [AN3]>  Infra  10    2457 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2      no        

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

[[/etc/NetworkManager/system-connections/MiRedWifi]] (600 root)
[connection] id=MiRedWifi | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=MiRedWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MiRedWifi 1]] (600 root)
[connection] id=MiRedWifi 1 | type=wifi | permissions=user:mariano:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=MiRedWifi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

country AR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.457 GHz (Channel 10)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'MiRedWifi' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MiRedWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Motorola' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Motorola"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SUPERWIFI' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SUPERWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-57-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[  171.932825]  [<ffffffffc0a8d955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  171.932906]  [<ffffffffc0a8cfb0>] wl_event_handler+0x60/0x1d0 [wl]
[  171.932988]  [<ffffffffc0a8cf50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  176.848533] CPU: 2 PID: 463 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-57-generic #78-Ubuntu
[  176.848639]  [<ffffffffc0a8d955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  176.848681]  [<ffffffffc0a8cfb0>] wl_event_handler+0x60/0x1d0 [wl]
[  176.848723]  [<ffffffffc0a8cf50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  181.660324] CPU: 2 PID: 463 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-57-generic #78-Ubuntu
[  181.660444]  [<ffffffffc0a8d955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  181.660494]  [<ffffffffc0a8cfb0>] wl_event_handler+0x60/0x1d0 [wl]
[  181.660544]  [<ffffffffc0a8cf50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  261.392716] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

---

### Post by rivendil on 2017-01-08
Ok so computer still freezes. I was connected to "MiRedWifiExt" and while executing sudo apt-get update it totally froze.

---

### Post by Hadaka on 2017-01-09
Hi, lets try this...
your latest wireless report shows..
```
ideapad_bluetooth: Bluetooth
    Soft blocked [COLOR=#ff0000]yes[/COLOR]
```
Please Copy and paste...
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
The reports shows you were on "MiRedWifi"  not the "MiRedWifiExt"
and Power Management ON..that needs to be off.
```
MiRedWifi     <MAC '[COLOR=#ff0000]MiRedWifi[/COLOR]' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2      yes     *
wlp1s0    IEEE 802.11abg  ESSID "MiRedWifi"  
          Mode Managed  Frequency 2.457 GHz  Access Point: <MAC 'MiRedWifi' [AC1]>   
          Retry short limit 7   RTS thr off   Fragment thr off
          Power Management [COLOR=#ff0000]on[/COLOR] 
```
Please Copy and paste...
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
The wireless dmesg report shows...
```
wl_notify_[COLOR=#ff0000]roaming[/COLOR]_status+0xc5/0x140 [wl]
```
that is because you have 4 access points listed as 1 thru 4 for MiRedWifi.
Please click your wifi signal icon..network manager..and then Edit Connections.
next click Wireless and delete ALL of the connections.
connect your computer to your router with a cable and do...
```
 sudo apt-get update
```
when that is complete/.. BOOT and then remove the cable and add your 
wireless connection of "MiRedWifi" Please do not add the "MiRedWifiExt" untill
after you have tested and ran a new wireless report if there are problems.
always make sure only the 1 entry for MiRedWifi is there..delete any others created
by your repeated attempts to connect.
thanks.,

---

