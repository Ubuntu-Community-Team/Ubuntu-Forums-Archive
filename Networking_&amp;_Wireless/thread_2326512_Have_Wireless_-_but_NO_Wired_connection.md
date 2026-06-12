---
title: "Have Wireless - but NO Wired connection?"
date: 2016-06-01
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2016-06-01
Need to know how to troubleshoot this internet connection problem. Wireless works, but Wired does not! 
Here is the output of Wireless Script. Does this help? I don't see anything wrong?
Running LTS Xubuntu v14.04 on my wifes Laptop HP500.

```



########## wireless info START ##########

Report from: 01 Jun 2016 16:43 EDT -0400

Booted last: 01 Jun 2016 00:00 EDT -0400

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-44-generic #59~14.04.1-Ubuntu SMP Tue Jul 7 15:07:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Xfce

##### lspci #############################

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
b43                   396480  0 
bcma                   52320  1 b43
mac80211              652777  1 b43
cfg80211              498458  2 b43,mac80211
ssb_hcd                12884  0 
wmi                    19193  1 hp_wmi
ssb                    62352  2 b43,ssb_hcd

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11906 (11.9 KB)  TX bytes:10435 (10.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.20.55  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:735375 (735.3 KB)  TX bytes:96540 (96.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"FBIvan7"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'FBIvan7' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:8   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         XXX.XXX.XX.XX    0.0.0.0         UG    0      0        0 wlan0
xxx.xxx.xxx.xx    0.0.0.0       255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver < wiped >
search     < wiped >

##### network managers ##################

Installed:

    NetworkManager

Running:

root       867     1  0 13:10 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [FBIvan7] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE402:        Infra, <MAC '2WIRE402' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    ATT954j687:      Infra, <MAC 'ATT954j687' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Ross:            Infra, <MAC 'Ross' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Hometam1:        Infra, <MAC 'Hometam1' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    2WIRE229:        Infra, <MAC '2WIRE229' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Sabbath-Network: Infra, <MAC 'Sabbath-Network' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    HOME-9565:       Infra, <MAC 'HOME-9565' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    *FBIvan7:        Infra, <MAC 'FBIvan7' [AC1]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 83 WPA WPA2

  IPv4 Settings:
    Address:         192.168.XX.XX
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.XX.XX

    DNS:             75.75.76.76
    DNS:             81.218.119.11
    DNS:             208.67.220.220

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

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=FBIvan7 | type=802-11-wireless
[802-11-wireless] ssid=FBIvan7
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/ATT064]] (600 root)
[connection] id=ATT064 | type=802-11-wireless
[802-11-wireless] ssid=ATT064 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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
          Current Frequency:2.432 GHz (Channel 5)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      6   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FBIvan7' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"FBIvan7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000009517808
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030bbdaca2e
                    Extra: Last beacon: 1380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'xfinitywifi' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030bbdb2530
                    Extra: Last beacon: 12ms ago

##### module infos ######################

[b43]
filename:       /lib/modules/3.16.0-44-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:6D:E3:1C:01:85:E4:5A:0C:0D:73:CA:36:F8:FA:02:ED:C6:25:3A
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
filename:       /lib/modules/3.16.0-44-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:6D:E3:1C:01:85:E4:5A:0C:0D:73:CA:36:F8:FA:02:ED:C6:25:3A
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:6D:E3:1C:01:85:E4:5A:0C:0D:73:CA:36:F8:FA:02:ED:C6:25:3A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D48679749A6B8B822E391CA
depends:        
intree:         Y
vermagic:       3.16.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:6D:E3:1C:01:85:E4:5A:0C:0D:73:CA:36:F8:FA:02:ED:C6:25:3A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/3.16.0-44-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb
intree:         Y
vermagic:       3.16.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:6D:E3:1C:01:85:E4:5A:0C:0D:73:CA:36:F8:FA:02:ED:C6:25:3A
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/3.16.0-44-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     2055C3093DA2EE9DEB5572C
depends:        
intree:         Y
vermagic:       3.16.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:6D:E3:1C:01:85:E4:5A:0C:0D:73:CA:36:F8:FA:02:ED:C6:25:3A
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4311 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   25.941584] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   26.048090] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12476.943273] forcedeth 0000:00:14.0 eth0: link down
[12705.273626] wlan0: authenticate with <MAC 'FBIvan7' [AC1]>
[12705.284229] wlan0: send auth to <MAC 'FBIvan7' [AC1]> (try 1/3)
[12705.285904] wlan0: authenticated
[12705.286136] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[12705.286140] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[12705.288222] wlan0: associate with <MAC 'FBIvan7' [AC1]> (try 1/3)
[12705.290309] wlan0: RX AssocResp from <MAC 'FBIvan7' [AC1]> (capab=0x411 status=0 aid=1)
[12705.290732] wlan0: associated

########## wireless info END ############


```

Any Suggestions?
Thanks!

---

### Post by QDR06VV9 on 2016-06-01
What dose this show
```
gedit /etc/network/interfaces
```

---

### Post by Rick St. George on 2016-06-01
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by QDR06VV9 on 2016-06-01
> **Rick St. George said:**
> ```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
Ok Good.
Run this in terminal....but I like to have the Ethernet cord plugged in when running the below.
```
sudo lshw -C network
```

---

### Post by Rick St. George on 2016-06-02
Results:

```


  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:21 memory:b8000000-b8003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:49:48:b7
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=b43 driverversion=3.16.0-44-generic  firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg


```

Only thing I see is NO logical name on the Wired section!?!
Its weird ... clicking network icon / information - it shows an IP Address, but nothing can connect!?!?!
Any suggestions?

---

### Post by Rick St. George on 2016-06-02
Also wanted to Post this ...

 in Software Updates / Additional Drivers it shows Broadcom BCM4311 802.11b/g Wireless LAN Controller
"Using Broadcom 802.11 Linux STA wireless driver from bcmwl-kernel-source (proprietary)", 
"This device is not working"

And ... 
DO NOT USE THE DEVICE (is checked)
Can Not check - when I do, it defaults back to "DO NOT USE THE DEVICE", because it is apparently detecting the device not working. 

Apparently - according to other posts, it has to do with the Broadcom proprietary drivers and the new kernel updates!!!
So how can we insure this problem gets fixed, other than replacing the NIC ? ? ?

---

### Post by Rick St. George on 2016-06-02
Just found this out .... Looked up the Manual and it shows that the NIC is a RealTek 8201CL
See here [http://h10032.www1.hp.com/ctg/Manual/c01095493.pdf](http://h10032.www1.hp.com/ctg/Manual/c01095493.pdf)

Is it possible that Xubuntu configured a Driver for the wrong NIC?  How can I find out???

---

### Post by QDR06VV9 on 2016-06-02
Just to check, install inxi...and post back the results
```
sudo apt-get install inxi
```
And paste back the return of this
```
inxi -N
```

---

### Post by Rick St. George on 2016-06-02
```

E: unable to locate package inxi
You can install it by typing 
sudo apt-get install inxi
You will have to enable the component called 'universe'.

```

DID THAT AND RECEIVED

```

sudo apt-get install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gawk hddtemp libsigsegv2 lm-sensors mesa-utils
Suggested packages:
  gawk-doc ksensors fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed:
  gawk hddtemp inxi libsigsegv2 lm-sensors mesa-utils
0 upgraded, 6 newly installed, 0 to remove and 8 not upgraded.
Need to get 1,069 kB of archives.
After this operation, 3,259 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty/universe hddtemp amd64 0.3-beta15-52 [52.8 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty/universe inxi all 1.9.17-1 [101 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe lm-sensors amd64 1:3.3.4-2ubuntu1 [84.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty/universe mesa-utils amd64 8.1.0-2 [34.4 kB]
Fetched 1,069 kB in 2s (408 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 172717 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Selecting previously unselected package gawk.
(Reading database ... 172725 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package hddtemp.
Preparing to unpack .../hddtemp_0.3-beta15-52_amd64.deb ...
Unpacking hddtemp (0.3-beta15-52) ...
Selecting previously unselected package inxi.
Preparing to unpack .../archives/inxi_1.9.17-1_all.deb ...
Unpacking inxi (1.9.17-1) ...
Selecting previously unselected package lm-sensors.
Preparing to unpack .../lm-sensors_1%3a3.3.4-2ubuntu1_amd64.deb ...
Unpacking lm-sensors (1:3.3.4-2ubuntu1) ...
Selecting previously unselected package mesa-utils.
Preparing to unpack .../mesa-utils_8.1.0-2_amd64.deb ...
Unpacking mesa-utils (8.1.0-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up hddtemp (0.3-beta15-52) ...
Setting up inxi (1.9.17-1) ...
Setting up lm-sensors (1:3.3.4-2ubuntu1) ...
Setting up mesa-utils (8.1.0-2) ...
Processing triggers for ureadahead (0.100.0-16) ...
regina@regina-HPF500-ABA:~$ inxi -N
Network:   Card-1: Broadcom BCM4311 802.11b/g WLAN driver: b43-pci-bridge 
           Card-2: NVIDIA MCP51 Ethernet Controller driver: forcedeth 

```

Rebooted ...

Shows IP Address, but Incoming 0 - Outgoing 0
Have Net Access with WiFi and was able to accomplish above, can't figure out whats going on with the Wired Access!?!?!

---

### Post by Bashing-om on 2016-06-02
Rick St. George; Hello'

Broadcom. yes proprietary software. With broadcom wireless and the wired connection go hand in hand.
See if this guide is of assistance here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

To install - reinstall - the proper driver.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by jeremy31 on 2016-06-02
Edit the /etc/NetworkManager/NetworkManager.conf file to remove the line with
```
no-auto-default=
```


Reboot and see if it works

---

### Post by Rick St. George on 2016-06-02
Checked that out thoroughly. From there Ran this to Verify;

```

uname -r
3.16.0-71-generic
regina@regina-HPF500-ABA:~$ dpkg --get-selections | grep headers
linux-headers-3.16.0-30                install
linux-headers-3.16.0-30-generic            install
linux-headers-3.16.0-44                install
linux-headers-3.16.0-44-generic            install
linux-headers-3.16.0-71                install
linux-headers-3.16.0-71-generic            install
linux-headers-generic-lts-utopic        install 

```

THEN DOWNLOADED - 
bcmwl (6.30.223.248+bdcom-0ubuntu0.2) trusty-proposed
From here: [https://launchpad.net/ubuntu/+source/bcmwl](https://launchpad.net/ubuntu/+source/bcmwl)
THEN RAN THIS ... 

```

sudo dpkg -i bcmwl-kernel-source*
[sudo] password for regina: 
(Reading database ... 202393 files and directories currently installed.)
Preparing to unpack bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) over (6.30.223.248+bdcom-0ubuntu0.2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.16.0-71-generic
Building for architecture x86_64
Building initial module for 3.16.0-71-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-71-generic/updates/dkms/

depmod.....

DKMS: install completed.

```


BUT NO PROMPT. So, did it finish? Did a Shut Down, but systems seems to be hung up!
Did I mess up !?!?!?
Edit: Sorry Jeremy31 - didn't see your message till after I posted this. When it comes back up I can try it.

---

### Post by Rick St. George on 2016-06-02
Now I beleive it was the WRONG Driver Source. According to the Sticky, it should be the b43-firmware for the 4311 Broadcom.

When I go to Software & Updates / Additional Drivers ... it does not show Broadcom at all .. No Ethernet. However, my Wired Connection (icon at top) shows an IP Address ! ! ! Wireless light not on, so it must be wired-connection it is detecting, but still don't have right driver installed. I must be doing it wrong.

I'm going to try the instructions under "B43 - No Net Access" at;
[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx

[/URL]

---

### Post by jeremy31 on 2016-06-02
Not sure what is going on with the wired.  But to get wireless going again use ```
sudo apt-get remove bcmwl-kernel-source
``` and reboot

---

### Post by Rick St. George on 2016-06-02
Ok - I have used the "b43-fwcutter" to extract the drivers to "/lib/firmware", but not sure it is using it. And in "Software & Updates / Additional Updates" it still shows "device not working" and shows the following with DO NOT USE THIS DEVICE selected;
Broadcom 802.11 Linxu STA wireless driver source from bcmwl-kernel-source (proprietary)

Prior to Re-boot, I removed "bcmwl-kernel-source", and got the Wireless back-up but still Wired Connection does not connect.

Running this ;

```

sudo lshw -C network

```

Shows the same as post 5.

Any suggestions?

---

### Post by QDR06VV9 on 2016-06-03
Have you tried this yet?
Edit the /etc/NetworkManager/NetworkManager.conf file to remove the line with
   
   ```
 no-auto-default=
```
EDIT: I have seen where NM applet has to show all users are allowed to connect to this network.
To be sure right click on the network icon in the panel and select edit <it may show something like enp4s6 or eth0>

---

### Post by Rick St. George on 2016-06-03
YES I did, and also checked NM and YES "all users are allowed to use this network".
I am noticing it is taking forever to download BitDefender updates at only 14 kb/s.
Something seriously wrong here ... and I'm beginning to think its hardware issue.
Except that it all started when everyone else was having problems recently after an update and backporting their "network upgrades".

---

### Post by Rick St. George on 2016-06-07
Note we have IPV 6 disabled. Could this be part of the problem everyone  is experiencing when the coders are attempting to force it to work???   Just curious! And profoundly perplexed ! ! !

---

### Post by jeremy31 on 2016-06-07
I found this in a wiki
```

sudo modprobe -r forcedeth
sudo modprobe forcedeth msi=0 msix=0
```
See if it works

---

### Post by Rick St. George on 2016-06-07
Thanks Jeremy31, but still No Wired access after reboot. But shows IP address even after disabling WiFi and enabling Wired!?!?
Also, note the 1st paragraph in Post #15 above. Why does NO Driver show up here and under Network Manager / Information / Wired Conn.?

Note the 2nd Part of Post #15 above, shows Driver is B43 (for BroadCom 4311).

An Error shows unmet depedancies. Installed Synaptics Pkg Mgr. and shows no unmet dependancies. Quick Search in Pkg. Mgr. for LibNL
shows: libnl-3-200 v3.2.27.1, and is greyed out (only option is to remove). 

Still at a loss as to whats going on???

EDIT:  NOTE recent update on my UbuntuStudio v14.04 LTS shows;

> 
Changes for libnl-route-3-200 versions:
Installed version: 3.2.21-1ubuntu1.1
Available version: 3.2.21-1ubuntu3


So how can I get these to install on my wifes Xubuntu Laptop running v14.04 LTS ???

---

### Post by QDR06VV9 on 2016-06-07
You can go to this site: [http://packages.ubuntu.com/trusty/libs/libnl-route-3-200](http://packages.ubuntu.com/trusty/libs/libnl-route-3-200)
Download and install it on her's
I like to use [Gdebi]("http://packages.ubuntu.com/trusty/admin/gdebi") to install .debs

---

### Post by Rick St. George on 2016-06-07
After using Synaptic Pkg. Mgr. opted to "force version" to downgrade from libnl v3.2.27.1 to v3.2.21.1, then Rebooted. 
Apparently the Pkg. Mgr. removed some Headers used as now the computer won't boot and the screen reads ...

> 
Gave up waiting for root device.
- Boot args (cat /proc/cmdline)
- Missing modules (cat /proc/modules; ls /dev)
dropping to a shell


Perhaps now all I can do is Install v16.04 (if it is ready).
Thanks Runrikus, I have those download on a flash drive, but before Reboot it would not read the flash drive.
Any suggestions as to how to get this HP F500 back up and running? Then I will try to install libnl v3.2.21.1 
Is that the corrected version?

Thanks!

---

### Post by jeremy31 on 2016-06-07
Can you use the Grub menu at boot to go to Advanced Options to boot to an older kernel?  You may have to press Shift at boot to see the Grub menu

I didn't ask you to reboot after my recommendation in post #19 as the parameter change doesn't survive a reboot

---

### Post by Rick St. George on 2016-06-08
Sorry Jeremy for the Reboot, and Yes I did also try booting to an earlier kernel, but that boot also failed.

Since I can't get it to boot, I tried the Xubuntu mini.iso to a USB Flash Drive (extracted the ISO to the F-Drive), but it would not boot off the Flash Drive. All I got was a black screen with flashing cursor. At this point, I believe I will have to boot from a Xubuntu v14.04 Live Disk and perhaps it can use the Net Connection to download and install newer files / kernels, and maybe to v16.04 LTS. Have all files backed up!

---

### Post by Rick St. George on 2016-06-08
Re-installed Xubuntu v14.04 LTS, System using B43 driver for BroadCom 4311 (PCI & Chip ID) but No Wireless now. Wired connection works.

Upon boot-up, it briefly refers to a Bad Page [https://wireless.wiki.kernel.org/en/users/Drivers/b43](https://wireless.wiki.kernel.org/en/users/Drivers/b43) and the page reads - 
"For relicensing, the content of this page was removed.".  A link on that page [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/)  seems to have same info as here [http://linuxwireless.org/en/users/Drivers/b43/](http://linuxwireless.org/en/users/Drivers/b43/) , both of which show that the Broadcom 4311 is supported by the B43 driver. Instructions to install that driver is a follows;
```

sudo apt-get install firmware-b43-installer
```
Since the computer already shows that driver is intalled, I am not going there, as upon installation the kernel should've and must have installed it.

Seems like we will just have to give up on this one folks. Don't know what broke it, because it use to work fine.
Any last suggestions? 
Thanks!

---

### Post by X-RED_Tech on 2016-06-08
Troubleshoot for Boadcom is here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
And no, the kernels "shouldn't" because it's a proprietary driver/firmware.

---

### Post by Rick St. George on 2016-06-09
Upon attempting the command in Post #25, I get the following;
> 
E: unable to locate package firmware-b43-installer


Must be permission somewhere, or perhaps I need to add something to "authentication" under Software & Updates?
One more chance please!

---

### Post by X-RED_Tech on 2016-06-09
You need some internet connection to download and install from the repositories. We usually just connect an Ethernet cable to do that. Also make sure you do **sudo apt-get update **before anything else. If you find errors please post them. This error may or may not prevent the installation of the required drivers/firmware and should be dealt with before other troubleshooting.

---

### Post by Rick St. George on 2016-06-09
FINALLY - OK, Here is what worked ... After Complete Re-Install of Xubuntu v14.04 (from Live-CD).
NOTE: my system shows I have the BroadCom 4311 (pci & chip ID)

In Software Updates / Ubuntu Software (tab) - Enabled/checked 
  "Proprietary drivers for devices" and 
  "Software restricted by Copyright or legal issues (multiverse)"
Under /Other Software (tab) - Enabled/checked
  "Independent (source code)"

Then executed the following in terminal;
```

sudo apt-get install firmware-b43-installer
sudo modprobe -r b43 bcma
sudo modprobe -r brcmsmac bcma
sudo modprobe -r wl

sudo modprobe b43
sudo rfkill unblock all

```
Rebooted. Both WiFi and Wired connections are recognized and work (for time being).
NOTE: several pages were referenced on this matter. The one I found most helpful, informative and timely was here;
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

Thanks everyone for your help on this matter.
My wife is happy now ... and I'm a genious / hero ! ! !
Hooray!

;-)

---

### Post by QDR06VV9 on 2016-06-09
Hey Hey...That's Good News!
And it always good to be the knight in shinning armour albeit short lived at times.  :lol:
And a big thanks for sharing how you solved it.
Kind Regards

---

