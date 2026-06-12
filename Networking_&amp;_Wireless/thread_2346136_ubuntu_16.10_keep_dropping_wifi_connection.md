---
title: "ubuntu 16.10 keep dropping wifi connection"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by bboylilou2016 on 2016-12-11
Hello
I recently installed ubuntu 16.10 without any problem on my pc hp desktop then its network card is down so I have to buy a wifi adapter RTL8187 to connect to my router adsl while ubuntu recognize this adapter.
The problem is that after 5 min I can not access the internet I ping on the @ ip of my router I receive no response the query its reject and the icon of wifi is always display the status connect.I find a lot of the solution on this problem on the internet I try all the solution but still the same problem.
I do dual boot windows 7 and ubuntu I have tested a lot of times this adapter wifi on windows 7 it works very well without any problem I remain connected throughout the day.
My router is configured to use the wireless mode option: 802.11b + g .
Someone can help me  please I like to work with ubuntu but this problem is really fateful:(:(.
thank you in advance.
cordially.

---

### Post by guimaster on 2016-12-11
I have an Asus Adapter (RTL8192CU). I find that if I am pinging a website such as Google or Yahoo, that I will not lose my connection. The issue seems to be that Ubuntu is putting the device to sleep when not in use, and it's not waking back up when needed.

If you want to test this, start pinging a website like google.com as soon as you boot your computer. Allow the pinging to continue, and go on with your normal activities. See if you lose your connection or not.

---

### Post by ian-weisser on 2016-12-11
Please [read the sticky]("https://ubuntuforums.org/showthread.php?t=370108") for troubleshooting wireless in this forum.
Please provide the information requested in the sticky.
Since you seem to have two wireless interfaces (card and dongle), please provide the information for both.

---

### Post by bboylilou2016 on 2016-12-12
Hello,
I now test ubuntu 16.10 on a virtual machine, it remains the same problem.
I installed the wificheck script and here are the results:
> 
```


>>    cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"

>>    lsusb 

Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

>>    lspci -k -nn | grep -A 3 -i net 


>>    sudo lshw -C network 

  *-network
       description: Interface réseau sans fil
       identifiant matériel: 2
       information bus: usb@1:1
       nom logique: wlx24050f4a6f97
       numéro de série: 24:05:0f:4a:6f:97
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=4.8.0-22-generic firmware=N/A ip=192.168.1.166 link=yes multicast=yes wireless=IEEE 802.11

>>    lsmod 

Module                  Size  Used by
ccm                    20480  2
arc4                   16384  2
rtl8187                40960  0
mac80211              757760  1 rtl8187
eeprom_93cx6           16384  1 rtl8187
cfg80211              581632  2 mac80211,rtl8187
snd_ens1371            28672  2
vmw_balloon            20480  0
snd_ac97_codec        131072  1 snd_ens1371
gameport               16384  1 snd_ens1371
ac97_bus               16384  1 snd_ac97_codec
snd_pcm               110592  2 snd_ac97_codec,snd_ens1371
joydev                 20480  0
input_leds             16384  0
snd_seq_midi           16384  0
serio_raw              16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_ens1371
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    86016  11 snd_seq,snd_ac97_codec,snd_timer,snd_rawmidi,snd_ens1371,snd_seq_device,snd_pcm
soundcore              16384  1 snd
vmw_vmci               69632  1 vmw_balloon
shpchp                 36864  0
i2c_piix4              24576  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               36864  1 ip_tables
autofs4                40960  2
vmw_pvscsi             24576  0
vmxnet3                61440  0
hid_generic            16384  0
usbhid                 53248  0
hid                   118784  2 hid_generic,usbhid
vmwgfx                241664  3
psmouse               131072  0
ttm                   102400  1 vmwgfx
drm_kms_helper        167936  1 vmwgfx
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 vmwgfx,ttm,drm_kms_helper
mptspi                 24576  2
e1000                 143360  0
ahci                   36864  0
libahci                32768  1 ahci
mptscsih               40960  1 mptspi
mptbase               102400  2 mptscsih,mptspi
scsi_transport_spi     32768  1 mptspi
pata_acpi              16384  0
floppy                 73728  0
fjes                   28672  0

```
```


>>    iwconfig 

wlx24050f4a6f97  IEEE 802.11  ESSID:"TP-LINK_69991E"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: EC:08:6B:69:99:1E   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2709  Invalid misc:341   Missed beacon:0


>>    ifconfig -a 

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Boucle locale)
        RX packets 63196  bytes 3845624 (3.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 63196  bytes 3845624 (3.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx24050f4a6f97: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.166  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::9b1a:659:c586:e53b  prefixlen 64  scopeid 0x20<link>
        ether 24:05:0f:4a:6f:97  txqueuelen 1000  (Ethernet)
        RX packets 22293  bytes 24879854 (24.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18839  bytes 2263858 (2.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


>>    sudo iwlist scan 

wlx24050f4a6f97  Scan completed :
          Cell 01 - Address: EC:08:6B:69:99:1E
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_69991E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001054f37f3c
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 000E54502D4C494E4B5F363939393145
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601EC086B69991E1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
                    IE: Unknown: DD07000C4300000000


>>    uname -r -m 

4.8.0-22-generic x86_64

>>    cat /etc/network/interfaces 

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

>>    nm-tool 


>>    nmcli dev wifi 

*  SSID            MODE   CHAN  DÉBIT    SIGNAL  BARS  SÉCURITÉ 
*  TP-LINK_69991E  Infra  3     54 Mo/s  72      &#9602;&#9604;&#9606;_  WPA2     

>>    nmcli connection show 

NOM               UUID                                  TYPE             PÉRIPHÉRIQUE    
TP-LINK_69991E 1  b44e875e-b412-45b2-8a4f-80f6e68f943a  802-11-wireless  wlx24050f4a6f97 
TP-LINK_69991E    70f08467-35b5-440d-8b50-f7399b32e917  802-11-wireless  --              

>>    sudo rfkill list 

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


and here is the result of wireless-info script :
```


########## wireless info START ##########

Report from: 12 Dec 2016 11:55 WET +0000

Booted last: 12 Dec 2016 00:00 WET +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

##### kernel ############################

Linux 4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:15:00 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

##### lsusb #############################

Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8187                40960  0
mac80211              757760  1 rtl8187
eeprom_93cx6           16384  1 rtl8187
cfg80211              581632  2 mac80211,rtl8187

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 62343  bytes 3794369 (3.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 62343  bytes 3794369 (3.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx24050f4a6f97: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.166  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::9b1a:659:c586:e53b  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 22290  bytes 24879438 (24.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18818  bytes 2261851 (2.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

wlx24050f4a6f97  IEEE 802.11  ESSID:"TP-LINK_69991E"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'TP-LINK_69991E' [AC1]>   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2709  Invalid misc:341   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx24050f4a6f97
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx24050f4a6f97
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx24050f4a6f97

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       837     1  0 10:49 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx24050f4a6f97
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Manufacturer_Realtek_RTL8187_
GENERAL.PRODUCT:                        RTL8187_Wireless
GENERAL.DRIVER:                         rtl8187
GENERAL.DRIVER-VERSION:                 4.8.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb1/1-1/1-1:1.0/net/wlx24050f4a6f97
GENERAL.IP-IFACE:                       wlx24050f4a6f97
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TP-LINK_69991E 1
GENERAL.CON-UUID:                       b44e875e-b412-45b2-8a4f-80f6e68f943a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   70f08467-35b5-440d-8b50-f7399b32e917 | TP-LINK_69991E
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   b44e875e-b412-45b2-8a4f-80f6e68f943a | TP-LINK_69991E 1
IP4.ADDRESS[1]:                         192.168.1.166/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP6.ADDRESS[1]:                         fe80::9b1a:659:c586:e53b/64
IP6.GATEWAY:                            

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
TP-LINK_69991E  <MAC 'TP-LINK_69991E' [AC1]>  Infra  3     2422 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2      yes     * 

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

[[/etc/NetworkManager/system-connections/TP-LINK_69991E]] (600 root)
[connection] id=TP-LINK_69991E | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_69991E
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/TP-LINK_69991E 1]] (600 root)
[connection] id=TP-LINK_69991E 1 | type=wifi | permissions=user:toto:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_69991E
[ipv4] method=manual
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Casablanca (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlx24050f4a6f97  11 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)

wlx24050f4a6f97  Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_69991E' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_69991E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010533bae79
                    Extra: Last beacon: 464ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8187]
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     745646D3ABF7B00F320D6AB
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8187.conf]
options rtl8187  debug=0 disqble_watchdog=N fwlps=N swlps=Y swenc=Y ips=N msi=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  807.773438] rtl8187: unknown parameter 'debug' ignored
[  807.773540] rtl8187: unknown parameter 'disqble_watchdog' ignored
[  807.773542] rtl8187: unknown parameter 'fwlps' ignored
[  807.773543] rtl8187: unknown parameter 'swlps' ignored
[  807.773543] rtl8187: unknown parameter 'swenc' ignored
[  807.773544] rtl8187: unknown parameter 'ips' ignored
[  807.773545] rtl8187: unknown parameter 'msi' ignored
[  810.325071] ieee80211 phy0: hwaddr <MAC address>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  810.508248] rtl8187: Customer ID is 0x00
[  810.569057] rtl8187: wireless switch is on
[  810.776583] rtl8187 1-1:1.0 wlx24050f4a6f97: renamed from wlan0
[  810.992168] IPv6: ADDRCONF(NETDEV_UP): wlx24050f4a6f97: link is not ready (repeated 3 times)
[  829.702514] wlx24050f4a6f97: authenticate with <MAC 'TP-LINK_69991E' [AC1]>
[  830.634225] wlx24050f4a6f97: send auth to <MAC 'TP-LINK_69991E' [AC1]> (try 1/3)
[  830.639137] wlx24050f4a6f97: authenticated
[  830.660729] wlx24050f4a6f97: associate with <MAC 'TP-LINK_69991E' [AC1]> (try 1/3)
[  830.666698] wlx24050f4a6f97: RX AssocResp from <MAC 'TP-LINK_69991E' [AC1]> (capab=0x431 status=0 aid=6)
[  830.676193] wlx24050f4a6f97: associated
[  830.677069] IPv6: ADDRCONF(NETDEV_CHANGE): wlx24050f4a6f97: link becomes ready

########## wireless info END ############


```

thank you

---

### Post by bboylilou2016 on 2016-12-12
i did it the packet is dropped its shows me when i ping [www.google.com](www.google.com) or to my router 192.168.1.1 or any other website 
192.168.1.166 : destination host unreachable

---

### Post by guimaster on 2016-12-12
My Asus USB-N13 adapter was giving that "destination host unreachable error" before as well, but has since worked fine. Now I just keep a ping open to my gateway IP, and it keeps my connection alive.

I'm sorry I can't be of more help. Hopefully someone more knowledgeable will come along and provide you some assistance. I'm not a Linux Geek.

---

