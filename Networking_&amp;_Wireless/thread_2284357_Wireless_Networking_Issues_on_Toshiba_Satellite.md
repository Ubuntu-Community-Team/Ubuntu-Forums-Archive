---
title: "Wireless Networking Issues on Toshiba Satellite"
date: 2015-06-29
forum: Networking &amp; Wireless
---

### Post by MLAQTS on 2015-06-29
Hello, everyone.
I've recently been trying to get an old Toshiba Satellite A105-S4284 back in working order, by replacing its original Windows XP with Ubunto 15.04. Everything seems to be going quite well, except for the issues I describe in this thread, which I suppose is why I posted it in the first place.

The machine has an Intel Corporation PRO/Wireless 3945ABG as it's network controller. Here's the portion of the output regarding the network controller when I run 
```

sudo lspci -vnn

```
```

05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at da000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945

```
Here is the output when I run
```

dmesg | grep -i iwl

```
```

[    7.520932] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    7.520938] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[    7.521011] iwl3945 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    7.574620] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    7.574628] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    7.683233] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'

```
One problem seems to be that wireless LAN is hard blocked by the machine, as shown by the "Wireless is disabled by hardware switch" message in the network-manager hover menu. Indeed, when I run 
```

sudo rfkill list all

```
, the output is:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
However, there is no physical Wifi switch that I know of on my machine, and the Fn+F8 key combination does not appear to be functional, even when pressed before the Ubuntu operating system loads. I can resolve the hard block temporarily by running 
```

sudo modprobe -r iwl3945
sudo rfkill unblock all
sudo modprobe iwl3945

```
, and the output of 
```

sudo rfkill list all

```
changes to
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
, but my actual wireless connection still does not function properly, and the "Wireless is disabled by hardware switch" message is replaced by "Device not ready". However, the output of 
```

sudo rfkill list all

``` 
reverts to 
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
whenever I restart my system. Curiously enough though, the aforementioned fix does not function when I replace the default network-manager with the wicd network manager, as suggested by many threads, [this one]("http://ubuntuforums.org/showthread.php?t=2187645") resembling my own situation the most closely. When I do such, the output of 
```

sudo rfkill list all

```
remains as
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
Also, performing the Toshiba system reset, by holding the power button for 30 seconds with the battery removed, doesn't seem to affect my situation at all, neither does the solution offered by [this thread]("http://ubuntuforums.org/showthread.php?t=820297"). The output from
```

sudo iwlist wlan0 scan 

```
being
```

wlan0     Interface doesn't support scanning : Network is down

```
both before and after I apply [chili555]("http://ubuntuforums.org/member.php?u=35909")'s solution.

I have considered updating my system BIOS, although I believe that'll be quite difficult, since my machine was not built to support Linux, and so the BIOS update files are all .exe Windows executable files. However, if someone were to inform me of how I might practically update my BIOS, perhaps by providing a method of obtaining a mountable image file to do such, that may prove to be quite helpful. I do own a Windows 7 machine, if that ever becomes necessary.

Apologies for my poor formatting in this thread, as I'm fairly new to BBcode and forums in general. I do in fact notice my excessive use of [code/] tags, among numerous other design fallacies. This problem isn't urgent, as I'm only restoring this machine as a fun project out of the boredom of summer break, but please help me regardless, as I'm sure you will seeing from all the helpful responses elsewhere on this forum.

Also, if anyone thinks that the output file from the wireless info script would be useful in resolving this issue, I would be glad to attach that to this thread as well.

---

### Post by stanleyp2 on 2015-06-29
reinstall grub often fixes my satellite hardware problems

---

### Post by MLAQTS on 2015-06-29
Thank you for the reply. Unfortunately, reinstalling grub (either through the "grub-install command" directly or through "apt-get install --reinstall grub") does not seem to have any noticeable effect on my situation,

---

### Post by wildmanne39 on 2015-06-29
Let's create a custom file that should unblock the wifi at boot up.

```
sudo gedit /etc/rc.local
```
then add these 3 lines to the file:
```
modprobe -r iwl3945
rfkill unblock all
modprobe iwl3945
```
Proofread carefully, save and close gedit. Reboot, is it unblocked?
if so I believe you may need a parameter set also, please do only if your wifi is scanning and not connecting:
```
sudo su
echo options iwl3945 disable_hw_scan=1 swcrypto=1 > /etc/modprobe.d/iwl3945.conf
```
Reboot does it connect if not run the wireless script in my signature and post the results here using code tages.

---

### Post by MLAQTS on 2015-06-29
Appending to rc.local does unblock the ports, according to "rfkill list all", but I am still unable to either scan for or connect to any wireless network. The Wi-Fi network section of the network-manager hover menu is greyed out, and shows "Wi-Fi Networks device not ready". Neither am I able to connect to the network when I add it manually from the "Edit Connections..." window.

Below is the output of the wireless script:
```


########## wireless info START ##########

Report from: 29 Jun 2015 10:27 EDT -0400

Booted last: 29 Jun 2015 10:19 EDT -0400

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:34:06 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Kernel driver in use: iwl3945

07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff10]
    Kernel driver in use: e100

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 22d4:2100  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

iwl3945                65536  0 
iwlegacy               90112  1 iwl3945
mac80211              626688  2 iwl3945,iwlegacy
cfg80211              462848  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.18  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe5f:7215/64 Scope:Link
          inet6 addr: 2601:100:8001:fab:2a0:d1ff:fe5f:7215/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2043 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:860029 (860.0 KB)  TX bytes:239088 (239.0 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 75.75.75.75
nameserver 75.75.76.76
search hsd1.ga.comcast.net

##### network managers ##################

Installed:

    Wicd

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     38AF47414DCF3CBFB173CB3
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     752C696EB47FC8BDCF872BB
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     88CC41451370601B0D885E4
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

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

iwl3945

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2015-06-29
The information from the script shows it is still hard blocked.

---

### Post by MLAQTS on 2015-06-29
Apologies for that, it seems that I accidentally attached the output  from a previous run of the wireless script, rather than the one  generated after applying your suggested changes to rc.local. Here is the updated output of the wireless script:
```


########## wireless info START ##########

Report from: 29 Jun 2015 22:37 EDT -0400

Booted last: 29 Jun 2015 22:36 EDT -0400

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:34:06 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Kernel driver in use: iwl3945

07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff10]
    Kernel driver in use: e100

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 22d4:2100  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                65536  0 
iwlegacy               90112  1 iwl3945
mac80211              626688  2 iwl3945,iwlegacy
cfg80211              462848  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.18  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:100:8001:fab:9c3a:f298:3c6e:2752/64 Scope:Global
          inet6 addr: fe80::2a0:d1ff:fe5f:7215/64 Scope:Link
          inet6 addr: 2601:100:8001:fab:2a0:d1ff:fe5f:7215/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43839 (43.8 KB)  TX bytes:27744 (27.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    1024   0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ga.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       544     1 19 22:36 ?        00:00:14 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/100 VE Network Connection
GENERAL.DRIVER:                         e100
GENERAL.DRIVER-VERSION:                 3.5.24-k2-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:07:08.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Ethernet Main
GENERAL.CON-UUID:                       b77ff44a-a013-4800-a274-78b224404ec8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b77ff44a-a013-4800-a274-78b224404ec8 | Ethernet Main
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 10.0.0.18/24, gw = 10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ga.comcast.net.
DHCP4.OPTION[1]:                        network_number = 10.0.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1436236617
DHCP4.OPTION[9]:                        domain_name = hsd1.ga.comcast.net.
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 604800
DHCP4.OPTION[16]:                       ip_address = 10.0.0.18
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         ip = 2601:100:8001:fab:9c3a:f298:3c6e:2752/64, gw = fe80::faed:a5ff:feb2:54b1
IP6.ADDRESS[2]:                         ip = 2601:100:8001:fab:2a0:d1ff:fe5f:7215/64, gw = fe80::faed:a5ff:feb2:54b1
IP6.ADDRESS[3]:                         ip = fe80::2a0:d1ff:fe5f:7215/64, gw = fe80::faed:a5ff:feb2:54b1
IP6.ROUTE[1]:                           dst = 2601:100:8001:fab::/64, nh = ::, mt = 1
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:85:17:6e:fa:e2:c3:3:ef:48:9d:fb:72:bb:3c:7a:4a
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1
DHCP6.OPTION[5]:                        dhcp6_unknown_16 = 0:0:11:8b:0:a:65:52:6f:75:74:65:72:31:2e:30
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:<MAC address>

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 3945ABG [Golan] Network Connection
GENERAL.DRIVER:                         iwl3945
GENERAL.DRIVER-VERSION:                 3.19.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/Main]] (600 root)
[connection] id=Main | type=wifi
[wifi] ssid=HOME-54B2
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     38AF47414DCF3CBFB173CB3
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     752C696EB47FC8BDCF872BB
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     88CC41451370601B0D885E4
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        8A:8E:2F:48:DA:82:74:90:2F:AA:E5:56:85:5A:2B:2B:43:5C:2A:00
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

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

iwl3945

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwl3945.conf]
options iwl3945 disable_hw_scan=1

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

modprobe -r iwl3945
rfkill unblock all
modprobe iwl3945

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   30.818999] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   30.819005] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   30.819081] iwl3945 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[   30.859842] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   30.859848] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   30.860548] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   30.999782] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9

########## wireless info END ############

```

---

### Post by wildmanne39 on 2015-06-29
Go to top right corner of the screen and click on network manager make sure networking and wireless networks are enabled, then remove all connections from network manager and reboot and let network manager look for the networks itself. Then change the settings in network manager to match the screenshots.

If it does not connect post the contents of:
```
sudo gedit /etc/modprobe.d/iwl3945.conf
```
Thanks

---

### Post by MLAQTS on 2015-06-29
The network manager is able to locate my ethernet connection, although it is still unable to find any available Wi-Fi network. The Wi-Fi Network portion of the network-manager hover menu is still greyed out, and reads "device not ready".

Below are the contents of my iwl3945.conf:
```

options iwl3945 disable_hw_scan=1

```

---

### Post by wildmanne39 on 2015-06-30
Reset your router and make sure that wireless in the router is enabled and that it is on a channel that your wifi card picks up like 1 or 11.
Thanks

---

### Post by MLAQTS on 2015-06-30
Manually changing the router's channel and resetting it does not seem to have any effect on my situation. I don't believe that the issue is related to my router, as the system is unable to scan for any nearby Wi-Fi source at all, whereas my Windows 7 machine can locate multiple, including those of my neighbours.

---

### Post by MLAQTS on 2015-06-30
After browsing around the internet for a little while, I found a situation quite similar to my own [here]("http://ubuntuforums.org/showthread.php?t=1881752"). However, when running
```

sudo ifconfig wlan0 up

```
, as part of the solution offered by [canucked]("http://ubuntuforums.org/member.php?u=540942"), the terminal returns
```

SIOCSIFFLAGS: Operation not possible due to RF-kill

```
Also, when I execute
```

sudo lshw -class network

```
, terminal returns
```

  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:a6:d3:ad
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.19.0-21-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:da000000-da000fff

```
, along with information which describes my ethernet.

Hopefully, this information may prove helpful in the diagnosis and resolution of my current problem.

---

### Post by Jack_Roman on 2015-07-10
> **MLAQTS said:**
> After browsing around the internet for a little while, I found a situation quite similar to my own [here]("http://ubuntuforums.org/showthread.php?t=1881752"). However, when running
```

sudo ifconfig wlan0 up

```
, as part of the solution offered by [canucked]("http://ubuntuforums.org/member.php?u=540942"), the terminal returns
```

SIOCSIFFLAGS: Operation not possible due to RF-kill

```
Also, when I execute
```

sudo lshw -class network

```
, terminal returns
```

  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:a6:d3:ad
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.19.0-21-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:da000000-da000fff

```
, along with information which describes my ethernet.

Hopefully, this information may prove helpful in the diagnosis and resolution of my current problem.

MLAQTS were you ever able to resolve your wireless connection issues with your Toshiba Satellite A105 S4284? The reason why I am asking is that I have the same laptop model# and in order to enable Wifi there is a physical Wifi switch located on the right side of this laptop, closest to the the two USB ports. Once you switch it on, it will glow orange to indicate that the Wifi card is active.

---

