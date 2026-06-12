---
title: "rt2500 ralink card on ubuntu 14.04"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by pdk-knight on 2014-06-03
RT2500 ralink wireless card.

Since ubuntu 8.10 I have always had to use ndiswrapper.
  (solved the way the intermittent network failure (even though the iwconfig said
 all was working) by 
ping -i 30   adsl  )
RT2500 ralink wireless card.

I have now installed 14.04 with  updates. Cannot compile a driver for ndis wrapper as I get incomplete or missing header. I downloaded the latest headers.
I would like to run without ndiswrapper.

The Install always finds the card, but 
iwlist scanning 
gives No Scan Results.

The results from a script shown below.
Any help would be appreciated
Peter Knight


```
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux peter 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

05:00.0 Ethernet controller [0200]: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) [8086:1096] (rev 01)
    Subsystem: Intel Corporation Device [8086:3484]
    Kernel driver in use: e1000e
05:00.1 Ethernet controller [0200]: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) [8086:1096] (rev 01)
    Subsystem: Intel Corporation Device [8086:3484]
    Kernel driver in use: e1000e
06:02.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Subsystem: Surecom Technology Device [10bd:13f3]
    Kernel driver in use: rt2500pci

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# The primary network interface
#auto wlan0
#iface wlan0 inet static
#    # wireless-* options are implemented by the wireless-tools package
#    wireless-mode Ad-Hoc
#    wireless-essid ruthandpeter@phuzamoya
#address 10.0.0.7
#netmask 255.255.255.0
#network 10.0.0.0
#gateway 10.0.0.2

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.2

    DNS:             10.0.0.2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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

##### lsmod #####

rt2500pci              27381  0 
rt2x00pci              13287  1 rt2500pci
rt2x00mmio             13603  1 rt2500pci
rt2x00lib              55307  3 rt2x00pci,rt2500pci,rt2x00mmio
mac80211              626511  2 rt2x00lib,rt2x00pci
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2500pci

##### modinfo #####

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     449B4A407454BAC53926F19
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x8086:0x1096 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x1096 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    0.814522] GHES: APEI firmware first mode is enabled by WHEA _OSC.
[    1.480864] e1000e 0000:05:00.1 eth1: (PCI Express:2.5GT/s:Width x4) <MAC address removed>
[    1.480867] e1000e 0000:05:00.1 eth1: Intel(R) PRO/1000 Network Connection
[    1.480945] e1000e 0000:05:00.1 eth1: MAC: 5, PHY: 5, PBA No: 400000-000
[   16.971132] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.303092] intel_rng: don't want to disable this in firmware setup, and if
[   18.397296] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
[   25.597729] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.598279] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.612562] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.612920] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
```

---

### Post by varunendra on 2014-06-04
Hello Peter, please try this in a terminal -
```
sudo iwconfig wlan0 power off
```
..and see if it works. If not, please run a new, experimental version of the  wireless_script mentioned here, and post its fresh report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the report, please use 'Code' tags. See the 'Use Code Tags' link in my signature below to see a quick guide with screenshots.

---

### Post by pdk-knight on 2014-06-05
[CODE]
Thanks Varun,
will follow your suggestion.
Have been trying over the last 2 days to get it running.
wrote script....
iwconfig wlan0 essid "ruthandpeter@phuzamoya" mode Ad-Hoc channel auto
and took of #'s from interfaces.
Then rutilt worked and ifconfig picked up the static address.
Put comments back and rebooted. 

Back to square one with the error 
can't get frequency channel 2
error code 22
Ran upwireles scipt , got message. No action.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

Take off comments in interfaces and reboot
Back to rutilt working but no signal.
NB all this time networkmanager was set to false 
so the interfaces file should not have made any difference ???


Set networkmanager.conf to managed=true
The hardware address was not the mac address (I thought it should be)
 
Changed it in the 70-persistent-net.rules file .
Rebooted.. That caused every interface to disappear.
The system simply generated a new interface wlan1 and resulted in no interfaces.
Set rules back to original and rebooted.
Now the networkmanager is working correctly and ignoring the interfaces file.
Before the IP address was getting set from the interfaces file.
I saved the proof in wireless-info-1.txt (more than enoug info already).
Ran script below and recieved message nerwork connected. However no signal in rtutilt
nm-tool showed signal 100 and noise -256.
but rtutilt showed no link
#!/bin/bash
iwconfig wlan0 essid "ruthandpeter@phuzamoya" mode Managed channel 1 ap 00:04:ed:5d:39:70 

Sytem gave segmentation error while copying text and starting vi
Next boot... Back to square one no scan results. no wlan0 ip address.
Peter
[\CODE]

---

### Post by pdk-knight on 2014-06-05
```

Thanks for the help
Peter

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

peter 3.13.0-27-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz
Memory : 5963 MB
Uptime : 18:35:01 up 29 min,  2 users,  load average: 0,05, 0,07, 0,06


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:00.0 Ethernet controller [0200]: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) [8086:1096] (rev 01)
    Subsystem: Intel Corporation Device [8086:3484]
    Kernel driver in use: e1000e
05:00.1 Ethernet controller [0200]: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) [8086:1096] (rev 01)
    Subsystem: Intel Corporation Device [8086:3484]
    Kernel driver in use: e1000e
06:02.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Subsystem: Surecom Technology Device [10bd:13f3]
    Kernel driver in use: rt2500pci


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2500pci              27381  0 
rt2x00pci              13287  1 rt2500pci
rt2x00mmio             13603  1 rt2500pci
rt2x00lib              55307  3 rt2x00pci,rt2500pci,rt2x00mmio
mac80211              626511  2 rt2x00lib,rt2x00pci
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2500pci


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID                | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
===============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                         | 802.11 WiFi | rt2500pci | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-------------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth1                          | Wired       | e1000e    | unavailable  | no      |           |              | <MAC eth1>
-------------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Ethernet connection 1] | Wired       | e1000e    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         10.0.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.2
    DNS:             10.0.0.2
-------------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

ruthandpeter@phuzamoya : ssid=ruthandpeter@phuzamoya | mac-address=<MAC wlan0> | ipv6=ignore | ipv4=manual 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# The primary network interface
auto wlan0
iface wlan0 inet static
    # wireless-* options are implemented by the wireless-tools package
wireless-mode Ad-Hoc
    wireless-essid ruthandpeter@phuzamoya
address 10.0.0.7
netmask 255.255.255.0
broadcast 255.255.255.0
network 10.0.0.0
gateway 10.0.0.2

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 10.0.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.783/0.882/0.981/0.099 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.010/0.017/0.025/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_ZA.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2500pci]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
version:        2.3.0
srcversion:     449B4A407454BAC53926F19
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6

[rt2x00pci]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211

[rt2x00mmio]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib

[rt2x00lib]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B09A94F74DCA60EBD06A6B6
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[eeprom_93cx6]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x1096 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x1096 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"



Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=8bf796ea-fc17-46f8-81a4-f9579616665a ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.667953] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.668402] audit: initializing netlink socket (disabled)
[    0.810480] GHES: APEI firmware first mode is enabled by WHEA _OSC.
[    1.443097] e1000e 0000:05:00.1 eth1: (PCI Express:2.5GT/s:Width x4) <MAC eth1>
[    1.443101] e1000e 0000:05:00.1 eth1: Intel(R) PRO/1000 Network Connection
[    1.443179] e1000e 0000:05:00.1 eth1: MAC: 5, PHY: 5, PBA No: 400000-000
[   16.677688] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.015735] intel_rng: don't want to disable this in firmware setup, and if
[   18.353838] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
[   18.724617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.724637] wlan0: Trigger new scan to find an IBSS to join
[   21.820024] wlan0: Trigger new scan to find an IBSS to join
[   22.504375] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.780025] wlan0: Trigger new scan to find an IBSS to join
[   25.401732] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.402287] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.404680] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.524694] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by varunendra on 2014-06-06
Please correct the 'Code' tags - it should be a forward slash (/) in the closing tag, not a backslash (\) that you have used. :)

For the wireless, please try -
```
sudo iwconfig wlan0 power off
```
..and if you are using Network Manager to manage the wifi (recommended), remove all entries pertaining to the wireless interface from the /etc/network/interfaces file. That file and 'Network Manager' are two different managers to do the same job. Currently, you are using both to manage the same interface (wlan0) which may cause mutual conflicts of configuration resulting in no connection.

The "managed=false" entry in NetworkManager.conf file ensures that NM will ignore any interface that is being managed by the 'interfaces' file, thus avoiding possible conflicts. By changing it to "true", you just told it to NOT ignore any interfaces regardless of whether they are also managed by the 'interfaces' file or not. It is recommended to use either the 'interfaces' file ***OR*** Network Manager, not both at the same time.

---

### Post by pdk-knight on 2014-06-07
```

Set NetworkManager back to managed - false 
(interfaces controlling wlan0 i.e. comments removed)
Network manager tool shows the wlan0 set as manual as was set in interfaces.
root@peter:/home/pdk# iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Invalid argument
Below is the dmesg when booting after the changes.
[   17..568328] [drm] Initialized radeon 2.36.0 20080528 for 0000:09:0c.0 on minor 0
[   18.218103] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
[   18.320957] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.444414] cfg80211: World regulatory domain updated:
[   18.444420] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.444423] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.444425] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.444428] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.444430] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.444432] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.780030] wlan0: Trigger new scan to find an IBSS to join
[   28.496758] wlan0: Creating new IBSS network, BSSID 8e:06:96:6f:77:d4
[   60.892019] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[   61.052009] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   61.212012] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  121.820021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  121.980009] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  122.140011] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  182.876019] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  183.036016] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  183.196008] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Looked in /var/log/upstart
The last log 
 cat network-interface-wlan0.log.1
Ignoring unknown interface wlan0=wlan0.

network-manager -log gives a whole lot of errors the last being
(NetworkManager:755): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Key file does not have group 'connectivity'
Finally, something I don't understand
ifconfig shows wlan0 hardware address as a typical mac address
In network manager gui, the field specifically says mac address. 
This is not the mac address of the wlan0 card.
Re-read instructions on networkmanager managed=false
commented out all wireless settings.
iwconfig wlan0 power off 
no message
rutilt giving error channel 2 as before.
Peter

```

---

### Post by praseodym on 2014-06-07
You need to blacklist the wrong driver:
```

echo "blacklist rt2500pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv rt2500pci
sudo modprobe -v ndiswrapper
```

---

### Post by pdk-knight on 2014-06-08
I'm not using ndis wrapper.
Peter

---

### Post by pdk-knight on 2014-08-09
2 months later I have abandoned Ubuntu 14.04
I'll stay with ndiswrapper and 12.04
Peter

---

