---
title: "[SOLVED] Network manager - can't save a VPN connection"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by PaulBx on 2015-06-22
I am trying to get a VPN connection going. I have already verified I can make the connection manually, but it is tedious so I wanted to add it to the network manager. When I go into the network manager "edit connections" and select "add" for OpenVPN, I get the window for editing a VPN connection, but the "save" button is greyed out no matter what I do. On the other hand if I try to "add" an ethernet connection for example, the save button is always available.

Yes the network manager plugin for openvpn is installed, as well as openvpn itself. I tried "gksudo nm-connection-editor" but it didn't help.

$ uname -a
Linux len780 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by PaulBx on 2015-06-22
Here's the network script results
```


########## wireless info START ##########

Report from: 22 Jun 2015 12:47 PDT -0700

Booted last: 22 Jun 2015 10:22 PDT -0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, elevator=deadline

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo Device [17aa:3218]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 003: ID 5986:0295 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630728  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
ath3k                  13318  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.5.5  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::2289:84ff:fe8e:e68c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.5.1     0.0.0.0         UG    0      0        0 eth0
192.168.5.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       937     1  0 10:22 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Ethernet1Static] ----------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.5.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.5.1

    DNS:             192.168.5.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=OregonHome3 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=OregonHome3
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/OregonHome4]] (600 root)
[connection] id=OregonHome4 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=OregonHome4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Big_Bear]] (600 root)
[connection] id=Big_Bear | type=802-11-wireless
[802-11-wireless] ssid=Big_Bear | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Chinook Winds Casino Resort]] (600 root)
[connection] id=Chinook Winds Casino Resort | type=802-11-wireless
[802-11-wireless] ssid=Chinook Winds Casino Resort | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Lynn's House]] (600 root)
[connection] id=Lynn's House | type=802-11-wireless
[802-11-wireless] ssid=HOME-88A9
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/HamiltonLodging]] (600 root)
[connection] id=HamiltonLodging | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=HamiltonLodging | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Nobody_Here_But_Us_Chickens]] (600 root)
[connection] id=Nobody_Here_But_Us_Chickens | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=Nobody_Here_But_Us_Chickens | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/greenturtle]] (600 root)
[connection] id=greenturtle | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=greenturtle | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/V7Q4H]] (600 root)
[connection] id=V7Q4H | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=V7Q4H | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/BlueMarlin]] (600 root)
[connection] id=BlueMarlin | type=802-11-wireless
[802-11-wireless] ssid=BlueMarlin | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/OregonHome]] (600 root)
[connection] id=OregonHome | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=OregonHome | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/bluewhale]] (600 root)
[connection] id=bluewhale | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=bluewhale | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/OregonHome5]] (600 root)
[connection] id=OregonHome5 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=OregonHome5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-55-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-55-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-55-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     65C14EF588BF1A68181643C
depends:        ath
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-55-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-55-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2CE061809D3601D619ACB8E
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-55-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     22618C9A8AD682CBE73FFF2
depends:        
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/3.13.0-55-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     F1C87C8A7868D706DFF07B4
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-55-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        13:DF:A5:11:F1:4D:87:06:C6:AC:E2:7E:0C:6A:7D:14:69:B9:EA:7F
sig_hashalgo:   sha512

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

##### /etc/modules ######################

loop
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

/usr/local/bin/chkboot.sh&

echo deadline > /sys/block/sda/queue/scheduler
echo 1        > /sys/block/sda/queue/iosched/fifo_batch

iw reg set US
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

##### dmesg #############################

[   19.416328] ath: phy0: Set BT/WLAN RX diversity capability
[   19.425119] ath: phy0: ASPM enabled: 0x42
[   19.425123] ath: EEPROM regdomain: 0x65
[   19.425124] ath: EEPROM indicates we should expect a direct regpair map
[   19.425127] ath: Country alpha2 being used: 00
[   19.425128] ath: Regpair used: 0x65
[   19.994649] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by PaulBx on 2015-06-22
I found a thread with more information:
[http://ubuntuforums.org/showthread.php?t=2166664&highlight=save+vpn+config](http://ubuntuforums.org/showthread.php?t=2166664&highlight=save+vpn+config)

Apparently you need to have the "CA" field pointing at a separate file rather than just having it pulled directly out of the .ovpn file, even though the network manager interface suggests that having no special ca file is OK. :roll:

Anyway when I did that, the save button un-greyed itself, so I am marking this solved, FWIW!

However moving on, it (who knows what - no identifier) nagged me for a password for some keyring so I gave it one. Then it needs this password each time I try to run the thing - annoying (yet another password to remember). Also you cannot just start the VPN access directly from the network manager icon as that box is greyed out when you go to select it. You (apparently) first have to connect to eth0 normally, THEN go do the VPN connection. And in my case, this second connection timed out. So, I give up! The whole point of a gui is to makes things easy and obvious, and at this point getting my VPN connection from the command line is easier than doing it in network manager, which is apparently not ready for prime time with VPN connections.

This little game of guessing how to un-grey buttons is for the birds. The computer knows what is missing, but is coy about telling you what it is.

Bleah! :mad:

---

