---
title: "Wi-fi randomly disconnects and can't reconnect, PS3 Red Ribbon (Debian)"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by loicnguyen on 2015-11-23
Hi,

First of all, I'm fairly new to linux so I'm not very experienced.

I'm currently using Red Ribbon (debian based linux distro) on my Playstation 3. The problem is, the wifi keeps disconnecting after a few minutes and can't reconnect unless I reboot. As for the ethernet connexion, the last time I tried, it couldn't connect at all. (Note: Right now, I only have access to wifi)

Even if it's on a ps3, I hope that it doesn't change that much from a computer.


Here the output of the script (the wifi was already disconnected when I ran the script):

```

########## wireless info START ##########

last: /var/log/wtmp: No such file or directory
Perhaps this file was removed by the operator to prevent logging last info.
Report from: 22 Nov 2015 23:44 UTC +0000

Booted last: 22 Nov 2015 00:00 UTC +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

./wireless-info2: line 155: lsb_release: command not found

##### kernel ############################

Linux 3.12.6-red-ribbon-powerpc64-ps3 #7 SMP Tue Jan 7 17:09:59 CET 2014 ppc64 unknown unknown GNU/Linux

, video=ps3fb:mode:0, ps3fb=8M, quiet, nomodeset, splash, 

##### desktop ###########################

LXDE

##### lspci #############################

pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0267 Sony Corp. Tachikoma Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 24ae:2000  
Bus 001 Device 002: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info2: line 192: rfkill: command not found

##### lsmod #############################

cfg80211              213921  0 

##### interfaces ########################

auto lo
iface lo inet loopback
allow-hotplug eth0
auto eth0
auto wlan0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2044906 (1.9 MiB)  TX bytes:81666 (79.7 KiB)

##### iwconfig ##########################

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"FMEL"  Nickname:"gelic_wl"
          Mode:Managed  Access Point: <MAC 'FMEL' [AC2]>   
          Link Signal level=100/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2595     1  0 23:24 ?        00:00:01 /usr/sbin/NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ps3_gelic_driver
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    J0e:             Infra, <MAC 'J0e' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    FMEL:            Infra, <MAC 'FMEL' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52
    FMEL:            Infra, <MAC 'FMEL' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 52
    FMEL:            Infra, <MAC 'FMEL' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    FMEL:            Infra, <MAC 'FMEL' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    FMEL:            Infra, <MAC 'FMEL' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12
    FMEL:            Infra, <MAC 'FMEL' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ps3_gelic_driver
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/FMEL]] (600 root)
[connection] id=FMEL | type=802-11-wireless
[802-11-wireless] ssid=FMEL | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

./wireless-info2: line 293: iwlist: command not found

##### iwlist scan #######################

lo        Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC '' [AC1]>
                    ESSID:""
                    Channel:10
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Encryption key:on
                    Mode:Master
                    Signal level=100/100  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FMEL' [AC2]>
                    ESSID:"FMEL"
                    Channel:4
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Encryption key:off
                    Mode:Master
                    Signal level=75/100  
          Cell 03 - Address: <MAC 'FMEL' [AC3]>
                    ESSID:"FMEL"
                    Channel:11
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Encryption key:off
                    Mode:Master
                    Signal level=60/100  
          Cell 04 - Address: <MAC 'FMEL' [AC4]>
                    ESSID:"FMEL"
                    Channel:1
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Encryption key:off
                    Mode:Master
                    Signal level=52/100  
          Cell 05 - Address: <MAC 'FMEL' [AC5]>
                    ESSID:"FMEL"
                    Channel:9
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Encryption key:off
                    Mode:Master
                    Signal level=50/100  
          Cell 06 - Address: <MAC 'FMEL' [AC6]>
                    ESSID:"FMEL"
                    Channel:11
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Encryption key:off
                    Mode:Master
                    Signal level=30/100  
          Cell 07 - Address: <MAC 'FMEL' [AC7]>
                    ESSID:"FMEL"
                    Channel:1
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Encryption key:off
                    Mode:Master
                    Signal level=12/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.12.6-red-ribbon-powerpc64-ps3/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        
intree:         Y
vermagic:       3.12.6-red-ribbon-powerpc64-ps3 SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

ps3lv1call

##### modprobe options ##################

[/etc/modprobe.d/snd_usb_audio.conf]
options snd_usb_audio enable=yes
options snd_usb_audio ignore_ctl_error=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   26.868309] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.479371] gelic_wl_assoc_worker: scan prerequisite failed
[   59.192253] gelic_wl_associate_bss: connected

########## wireless info END ############


```




Best regards,
Loic

---

