---
title: "Ubuntu 14.04 Wired Cable Unplugged"
date: 2015-01-30
forum: Networking &amp; Wireless
---

### Post by robert156 on 2015-01-30
I recently installed Ubuntu 14.04 LTS on a Dell 1500 Vostro, the wireless connection works fine, but it is unable to detect that the ethernet cable is plugged in. This seems to stem from the Broadcom Drivers.

I've followed the approach suggested by Camilo Cienfuegos in this thread: [http://ubuntuforums.org/showthread.php?t=2115659&page=2&highlight=BCM4401-B0](http://ubuntuforums.org/showthread.php?t=2115659&page=2&highlight=BCM4401-B0) by going:

```

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree

```

and modified /etc/modules so that it looked like this:
```

# /etc/modules: kernel modules to load at boot time

lp
#rtc
b43

```

but this failed to work (bcmwl-kernel-source wasn't installed), so I changed /etc/modules back to its original form and ran:
```
sudo apt-get purge --auto-remove linux-firmware-nonfree
```

While this is a wired and not a wireless issue, below is the output from this script:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

```


########## wireless info START ##########

Report from: 29 Jan 2015 23:25 NZDT +1300

Booted last: 29 Jan 2015 23:20 NZDT +1300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44

0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1020]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
mxm_wmi                13021  1 nouveau
dell_laptop            18168  0 
iwl3945                73259  0 
iwlegacy              100569  1 iwl3945
mac80211              630669  2 iwl3945,iwlegacy
dcdbas                 14928  1 dell_laptop
cfg80211              484040  3 iwl3945,iwlegacy,mac80211
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau
ssb                    62379  1 b44

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
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe10:e9be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5628650 (5.6 MB)  TX bytes:266604 (266.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:":-D"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC ':-D' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [:-D] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TELECOM-RMCK9T:  Infra, <MAC 'TELECOM-RMCK9T' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TNCAP217695:     Infra, <MAC 'TNCAP217695' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    vodafoneAFC5:    Infra, <MAC 'vodafoneAFC5' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    *:-D:            Infra, <MAC ':-D' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/:-D]] (600 root)
[connection] id=:-D | type=802-11-wireless
[802-11-wireless] ssid=:-D | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TELECOM-RMCK9T]] (600 root)
[connection] id=TELECOM-RMCK9T | type=802-11-wireless
[802-11-wireless] ssid=TELECOM-RMCK9T | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC ':-D' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:":-D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f6958aae2
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'vodafoneAFC5' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"vodafoneAFC5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000056c83ec27
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TNCAP217695' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TNCAP217695"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     63597F7C72B07A97B142DC2
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     A847A747E4E6066D74E1D6A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   25.567527] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   25.637924] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   28.286417] wlan0: authenticate with <MAC ':-D' [AC1]>
[   28.288318] wlan0: send auth to <MAC ':-D' [AC1]> (try 1/3)
[   28.290182] wlan0: authenticated
[   28.290379] iwl3945 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   28.290384] iwl3945 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   28.292054] wlan0: associate with <MAC ':-D' [AC1]> (try 1/3)
[   28.294932] wlan0: RX AssocResp from <MAC ':-D' [AC1]> (capab=0x411 status=0 aid=4)
[   28.296189] wlan0: associated
[   28.296226] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

Any help getting my ethernet connection up and running would be great!

---

### Post by Hadaka on 2015-01-30
Hi robert156, looks like you have a bit of a mess here.
lets start by understanding that you are new and learning.
to find your wireless and wired cards...wireless...and Ethernet
one command is...
```
lspci -nnk | egrep '0200|0280'
```
0200 being your ethernet card and 0280 your wireless card
you have a broadcom Ethernet card and an intel wireless card.
the commands you issued were directed at the wireless not the wired-Ethernet
lets do some housekeeping,please do..
```
sudo sed -i '/b43/ d' /etc/modules
```
this deletes b43 from /etc/modules...because you dont have a broadcom wireless card...you have an intel
card with driver-iwl3945. forcing the load of b43 on top of the iwl3945 will cause a conflict.
the driver for your ethernet card..
Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
is B44
please do..
```
sudo modprobe -rf b44
sudo modprobe -v b44
dmesg | grep b44
```
post the output of the dmesg please
the error code CABLE UNPLUGGED is usually acurate
tripple check both ends of your ethernet cable and the small
wire connections in the connectors,also check to see the card if
firmly seated. i suspect you have a simple unplug or a bad ethernet cable.
welcome to linux

---

### Post by robert156 on 2015-01-30
Hi Hadaka, I'm slowly learning my way around the terminal.
I've run your commands (I guess these revert my mistakes) and here is the output from dmesg:

```

[    1.148246] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.168601] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:9c:b6:84
[  165.812333] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[  165.812346] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[  176.812206] b44 ssb0:0 eth0: Link is down
[  219.812336] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[  219.812349] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[  263.812255] b44 ssb0:0 eth0: Link is down
[  342.911640] b44 ssb0:0 eth0: powering down PHY
[  353.692357] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[  353.712903] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:9c:b6:84

```

You are right, the problem is with the physical connection, the pins inside the ethernet plug on the laptop aren't quite high enough. If I hold the cable at the right angle the connection establishes...

However, the wireless connection is now playing up. It shows it as connected, but it isn't being assigned an IP, Gateway or Mask.

---

### Post by Hadaka on 2015-01-30
Hi, if you read the output from your last dmesg
you can see that your Ethernet =B44 connection
is on/off/on/off..that is due to the ethernet cable
poor physical connection. It also means the computer
doesnt know if it should be wireless or wired connected.
wired usually dominates the connection, but yours is flakey.
remove the ethernet cable and boot your computer, I think your
wireless problem will clear.
thanks.

---

### Post by robert156 on 2015-01-30
I attempted this, but it's still unable to make connection. Is there another way to reset the wireless to fix this issue?

---

### Post by Hadaka on 2015-01-30
please post the ouput of..
```
cat /etc/modules
```
then do..
```
sudo modprobe -rf iwl3945
sudo modprobe -v iwl3945
```
that help?

---

### Post by robert156 on 2015-01-30
Here's what is in modules
```

robert@vostro:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc

```

and the output after running modprobe

```

robert@vostro:~$ sudo modprobe -v iwl3945
insmod /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko 
insmod /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko 

```

Unfortunately the wireless is still acting the same, as in it connects, but there is no data throughput.

---

