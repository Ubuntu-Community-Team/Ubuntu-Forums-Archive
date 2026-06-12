---
title: "Broadcom wireless card disabled N wifi &amp; 5G, broken after graphics update"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by exothermic2 on 2015-12-29
I'm on a Macbook Pro 5,5 with Ubuntu 14.04 trusty and a Broadcom BCM4322 14e4:432b wireless card.

I recently upgraded from 12.04 where everything was working and I was able to connect to 5G wifi networks using .11N. After the upgrade, everything still worked. Wifi, 5G networks, N speeds. Not sure what driver was automatically loaded, but it worked. What was not working was the Nvidia graphics driver. 

So, I went Settings > Additional Drivers > and enabled the graphics driver I wanted. While doing that I noticed that the Broadcom Airport Extreme device was listed as "not working" and "do not use this device" was selected, but this was as I was currently connected to a wifi network and everything was ok. But I didn't touch the wifi device and just updated the graphics driver. Upon restart I had no wifi at all but graphics were fine. I tried everything in every help blog and forum post and cannot get back to what I had working before. 

1. The Broadcom STA driver does not work at all, I tried installing via Additional Drivers, Command line, and Ubuntu Software center. Purged everything before trying each. After a reboot there is no WiFi as an option.
2. I can get wifi working via the b43 drivers installed through the Software Center, but I only have b/g and 2.4G. I cannot use N wifi, or 5G networks, even though the 5G network on my router is still saved in my networks history.
3. Tried to enable N via iwconfig, but not sure if I am doing that right.

I have no idea where to go from here. Been trying to figure this out for 2 days now! 

```


########## wireless info START ##########


Report from: 28 Dec 2015 21:14 PST -0800


Booted last: 28 Dec 2015 20:36 PST -0800


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu Studio


##### lspci #############################


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: forcedeth


03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: b43-pci-bridge


##### lsusb #############################


Bus 002 Device 004: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 004: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


b43                   387371  0 
bcma                   52096  1 b43
mac80211              630728  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106494 (106.4 KB)  TX bytes:76572 (76.5 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:880884 (880.8 KB)  TX bytes:321653 (321.6 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"CenturyLink5184"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'CenturyLink5184' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:17  Invalid misc:142   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search domain


##### network managers ##################


Installed:


    NetworkManager


Running:


root       700     1  0 20:36 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0  [CenturyLink5184] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
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
    Darwin's Jowl - 2.4: Infra, <MAC 'Darwin's Jowl - 2.4' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    2gigaken:        Infra, <MAC '2gigaken' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *CenturyLink5184:Infra, <MAC 'CenturyLink5184' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WPA2
    CenturyLink4612: Infra, <MAC 'CenturyLink4612' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             205.171.3.25
    DNS:             205.171.2.25


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/AmtrakConnect]] (600 root)
[connection] id=AmtrakConnect | type=802-11-wireless
[802-11-wireless] ssid=AmtrakConnect | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CremaWire 5G]] (600 root)
[connection] id=CremaWire 5G | type=802-11-wireless
[802-11-wireless] ssid=CremaWire 5G | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Joels Phone]] (600 root)
[connection] id=Joels Phone | type=802-11-wireless
[802-11-wireless] ssid=Joels Phone | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/freshpot3]] (600 root)
[connection] id=freshpot3 | type=802-11-wireless
[802-11-wireless] ssid=freshpot3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Three Sisters Inn]] (600 root)
[connection] id=Three Sisters Inn | type=802-11-wireless
[802-11-wireless] ssid=Three Sisters Inn | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TownePlace_GUEST]] (600 root)
[connection] id=TownePlace_GUEST | type=802-11-wireless
[802-11-wireless] ssid=TownePlace_GUEST | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Bridges Cafe]] (600 root)
[connection] id=Bridges Cafe | type=802-11-wireless
[802-11-wireless] ssid=Bridges Cafe | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Riverside Market]] (600 root)
[connection] id=Riverside Market | type=802-11-wireless
[802-11-wireless] ssid=Riverside Market | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/myqwest8399]] (600 root)
[connection] id=myqwest8399 | type=802-11-wireless
[802-11-wireless] ssid=myqwest8399 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Quadtaxon]] (600 root)
[connection] id=Quadtaxon | type=802-11-wireless
[802-11-wireless] ssid=Quadtaxon | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ford Food + Drink]] (600 root)
[connection] id=Ford Food + Drink | type=802-11-wireless
[802-11-wireless] ssid=Ford Food + Drink | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Crows Feet Commons]] (600 root)
[connection] id=Crows Feet Commons | type=802-11-wireless
[802-11-wireless] ssid=Crows Feet Commons | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GreyhoundWiFi_6576]] (600 root)
[connection] id=GreyhoundWiFi_6576 | type=802-11-wireless
[802-11-wireless] ssid=GreyhoundWiFi_6576 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Foodie]] (600 root)
[connection] id=Foodie | type=802-11-wireless
[802-11-wireless] ssid=Foodie | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PublicDomain]] (600 root)
[connection] id=PublicDomain | type=802-11-wireless
[802-11-wireless] ssid=PublicDomain | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/www.personaltelco.net]] (600 root)
[connection] id=www.personaltelco.net | type=802-11-wireless
[802-11-wireless] ssid=www.personaltelco.net | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/-Knights Inn-]] (600 root)
[connection] id=-Knights Inn- | type=802-11-wireless
[802-11-wireless] ssid=-Knights Inn- | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/-Sister's-]] (600 root)
[connection] id=-Sister's- | type=802-11-wireless
[802-11-wireless] ssid=-Sister's- | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AceHotel]] (600 root)
[connection] id=AceHotel | type=802-11-wireless
[802-11-wireless] ssid=AceHotel | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DirectorsParkFreeWifi]] (600 root)
[connection] id=DirectorsParkFreeWifi | type=802-11-wireless
[802-11-wireless] ssid=DirectorsParkFreeWifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CenturyLink5184]] (600 root)
[connection] id=CenturyLink5184 | type=802-11-wireless
[802-11-wireless] ssid=CenturyLink5184 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McMenamins]] (600 root)
[connection] id=McMenamins | type=802-11-wireless
[802-11-wireless] ssid=McMenamins | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CenturyLink5184-5G]] (600 root)
[connection] id=CenturyLink5184-5G | type=802-11-wireless
[802-11-wireless] ssid=CenturyLink5184-5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PSU Guest]] (600 root)
[connection] id=PSU Guest | type=802-11-wireless
[802-11-wireless] ssid=PSU Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/prettyflyforawifi]] (600 root)
[connection] id=prettyflyforawifi | type=802-11-wireless
[802-11-wireless] ssid=prettyflyforawifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'CenturyLink5184' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink5184"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000077246a832e
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '2gigaken' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"2gigaken"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006ce37c560
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Darwin's Jowl - 2.4' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Darwin's Jowl - 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000068bf993913
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[b43]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[bcma]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C8432FAB97804E8F7A8FB0F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


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


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:0a.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


##### dmesg #############################


[    5.445380] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[    5.554878] forcedeth 0000:00:0a.0 eth0: link up
[    5.648241] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[    5.896961] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.896995] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    5.897730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.331475] wlan0: authenticate with <MAC 'CenturyLink5184' [AC1]>
[    7.380457] wlan0: send auth to <MAC 'CenturyLink5184' [AC1]> (try 1/3)
[    7.387648] wlan0: authenticated
[    7.388033] wlan0: associate with <MAC 'CenturyLink5184' [AC1]> (try 1/3)
[    7.390483] wlan0: RX AssocResp from <MAC 'CenturyLink5184' [AC1]> (capab=0x411 status=0 aid=3)
[    7.390915] wlan0: associated
[    7.390936] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  136.982388] forcedeth 0000:00:0a.0 eth0: link down
[  140.410328] wlan0: deauthenticating from <MAC 'CenturyLink5184' [AC1]> by local choice (reason=3)
[  234.030226] wlan0: authenticate with <MAC 'CenturyLink5184' [AC1]>
[  234.030591] wlan0: send auth to <MAC 'CenturyLink5184' [AC1]> (try 1/3)
[  234.032133] wlan0: authenticated
[  234.036083] wlan0: associate with <MAC 'CenturyLink5184' [AC1]> (try 1/3)
[  234.038986] wlan0: RX AssocResp from <MAC 'CenturyLink5184' [AC1]> (capab=0x411 status=0 aid=3)
[  234.039321] wlan0: associated
[  338.454517] wlan0: deauthenticating from <MAC 'CenturyLink5184' [AC1]> by local choice (reason=3)
[ 1662.081559] wlan0: authenticate with <MAC 'CenturyLink5184' [AC1]>
[ 1662.108718] wlan0: send auth to <MAC 'CenturyLink5184' [AC1]> (try 1/3)
[ 1662.111090] wlan0: authenticated
[ 1662.112229] wlan0: associate with <MAC 'CenturyLink5184' [AC1]> (try 1/3)
[ 1662.114663] wlan0: RX AssocResp from <MAC 'CenturyLink5184' [AC1]> (capab=0x411 status=0 aid=3)
[ 1662.115285] wlan0: associated


########## wireless info END ############

```

---

### Post by Vladlenin5000 on 2015-12-29
Hi and welcome.

Installing b43 was not a good idea...

According to [this]("http://ubuntuforums.org/showthread.php?t=2214110") I suggest you uninstall it and, for good measure blacklist it and ssb:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```

Then:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```


Reboot & test.

---

### Post by exothermic2 on 2015-12-29
Did that.
 
```

$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-62 linux-headers-3.13.0-62-generic
  linux-image-3.13.0-62-generic linux-image-extra-3.13.0-62-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/1,512 kB of archives.
After this operation, 8,038 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 363886 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.13.0-74-generic
Building for architecture x86_64
Building initial module for 3.13.0-74-generic
Done.


wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-74-generic/updates/dkms/


depmod.....


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-74-lowlatency

```


And I rebooted. And now I have no wifi whatsoever again.

```



########## wireless info START ##########


Report from: 29 Dec 2015 14:29 PST -0800


Booted last: 29 Dec 2015 14:27 PST -0800


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu Studio


##### lspci #############################


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
	Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
	Kernel driver in use: forcedeth


03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
	Subsystem: Apple Inc. AirPort Extreme [106b:008d]
	Kernel driver in use: b43-pci-bridge


##### lsusb #############################


Bus 002 Device 003: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 003 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6367819  0 
cfg80211              484040  1 wl
ssb                    62379  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40326 (40.3 KB)  TX bytes:22718 (22.7 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search domain


##### network managers ##################


Installed:


	NetworkManager


Running:


root       665     1  0 14:27 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             205.171.3.25
    DNS:             205.171.2.25


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


[[/etc/NetworkManager/system-connections/AmtrakConnect]] (600 root)
[connection] id=AmtrakConnect | type=802-11-wireless
[802-11-wireless] ssid=AmtrakConnect | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CremaWire 5G]] (600 root)
[connection] id=CremaWire 5G | type=802-11-wireless
[802-11-wireless] ssid=CremaWire 5G | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Joels Phone]] (600 root)
[connection] id=Joels Phone | type=802-11-wireless
[802-11-wireless] ssid=Joels Phone | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/freshpot3]] (600 root)
[connection] id=freshpot3 | type=802-11-wireless
[802-11-wireless] ssid=freshpot3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Three Sisters Inn]] (600 root)
[connection] id=Three Sisters Inn | type=802-11-wireless
[802-11-wireless] ssid=Three Sisters Inn | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TownePlace_GUEST]] (600 root)
[connection] id=TownePlace_GUEST | type=802-11-wireless
[802-11-wireless] ssid=TownePlace_GUEST | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Bridges Cafe]] (600 root)
[connection] id=Bridges Cafe | type=802-11-wireless
[802-11-wireless] ssid=Bridges Cafe | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Riverside Market]] (600 root)
[connection] id=Riverside Market | type=802-11-wireless
[802-11-wireless] ssid=Riverside Market | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/myqwest8399]] (600 root)
[connection] id=myqwest8399 | type=802-11-wireless
[802-11-wireless] ssid=myqwest8399 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Quadtaxon]] (600 root)
[connection] id=Quadtaxon | type=802-11-wireless
[802-11-wireless] ssid=Quadtaxon | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ford Food + Drink]] (600 root)
[connection] id=Ford Food + Drink | type=802-11-wireless
[802-11-wireless] ssid=Ford Food + Drink | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Crows Feet Commons]] (600 root)
[connection] id=Crows Feet Commons | type=802-11-wireless
[802-11-wireless] ssid=Crows Feet Commons | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GreyhoundWiFi_6576]] (600 root)
[connection] id=GreyhoundWiFi_6576 | type=802-11-wireless
[802-11-wireless] ssid=GreyhoundWiFi_6576 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Foodie]] (600 root)
[connection] id=Foodie | type=802-11-wireless
[802-11-wireless] ssid=Foodie | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PublicDomain]] (600 root)
[connection] id=PublicDomain | type=802-11-wireless
[802-11-wireless] ssid=PublicDomain | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/www.personaltelco.net]] (600 root)
[connection] id=www.personaltelco.net | type=802-11-wireless
[802-11-wireless] ssid=www.personaltelco.net | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/-Knights Inn-]] (600 root)
[connection] id=-Knights Inn- | type=802-11-wireless
[802-11-wireless] ssid=-Knights Inn- | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/-Sister's-]] (600 root)
[connection] id=-Sister's- | type=802-11-wireless
[802-11-wireless] ssid=-Sister's- | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AceHotel]] (600 root)
[connection] id=AceHotel | type=802-11-wireless
[802-11-wireless] ssid=AceHotel | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DirectorsParkFreeWifi]] (600 root)
[connection] id=DirectorsParkFreeWifi | type=802-11-wireless
[802-11-wireless] ssid=DirectorsParkFreeWifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CenturyLink5184]] (600 root)
[connection] id=CenturyLink5184 | type=802-11-wireless
[802-11-wireless] ssid=CenturyLink5184 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McMenamins]] (600 root)
[connection] id=McMenamins | type=802-11-wireless
[802-11-wireless] ssid=McMenamins | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CenturyLink5184-5G]] (600 root)
[connection] id=CenturyLink5184-5G | type=802-11-wireless
[802-11-wireless] ssid=CenturyLink5184-5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PSU Guest]] (600 root)
[connection] id=PSU Guest | type=802-11-wireless
[802-11-wireless] ssid=PSU Guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/prettyflyforawifi]] (600 root)
[connection] id=prettyflyforawifi | type=802-11-wireless
[802-11-wireless] ssid=prettyflyforawifi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/3.13.0-74-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512


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
blacklist b43
blacklist ssb


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


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:0a.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


##### dmesg #############################


[    5.573896] forcedeth 0000:00:0a.0 eth0: MSI enabled
[    5.574119] forcedeth 0000:00:0a.0 eth0: no link during initialization
[    5.574564] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   71.962473] forcedeth 0000:00:0a.0 eth0: link up
[   71.963352] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############



```


The bit that says "Kernel driver in use: b43-pci-bridge" doesn't make sense. I just blacklisted it.

---

### Post by exothermic2 on 2016-01-01
I'm starting to think that the only way I will be able to get this working is to reinstall the entire OS. Since I have no idea what the original functional driver was.

---

### Post by exothermic2 on 2016-01-30
I had to reinstall, not only reinstall but erase everything and install Ubuntu Trusty fresh. Spent a whole day on it again.

The issue was originally created when I changed the graphics drivers using the additional drivers gui. To update both the wifi and Nvidia drivers I used the command line instead.

With a fresh install, I got the wifi working with the bcmwl-kernel-source driver, as shown above. 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall bcmwl-kernel-source[/FONT][/COLOR]
```

I found out how to set the graphics drivers via command line from this page:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

In my case with the MacbookPro 5,5 with Nvidia graphics I did this:

```
sudo ubuntu-drivers devices
sudo apt-get install nvidia-340-updates

```

Now both my wifi and graphics card is working as it should. Next I get to restore all my files, programs, and settings. fun fun.

I wish erasing and reinstalling the OS was not the only way to solve this, but it was a mystery why it was originally borked in the first place.

---

