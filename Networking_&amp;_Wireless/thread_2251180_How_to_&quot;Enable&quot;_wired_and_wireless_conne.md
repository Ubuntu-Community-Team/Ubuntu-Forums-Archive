---
title: "How to &quot;Enable&quot; wired and wireless connections that are &quot;disabled&quot;"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by Sudeten on 2014-11-02
I have read and tried everything I could -- but I am stumped.  Nothing seems to change the fact the my Ubuntu 14.04, which had both wired and wireless working previously, has now mysteriously stopped working and there seems to be no way to "turn them back on" (there is a systems folder with "networking" but once the wired and wireless became "disabled" they no longer show).  Here is what ifconfig -a shows:

~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:ae:7f:8b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth2      Link encap:Ethernet  HWaddr 00:05:1b:a2:23:5f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13395426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13395426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1713320234 (1.7 GB)  TX bytes:1713320234 (1.7 GB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:73:4c:35  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and iwconfig -a shows:
iwconfig
eth0      no wireless extensions.

eth2      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on

Any ideas?

---

### Post by jeremy31 on 2014-11-02
You could read this thread [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385) on how to use the wireless script without an internet connection, running the script and posting the wireless-info file should save some time

---

### Post by Sudeten on 2014-11-02
jeremy31;  is there a similar script for the wired?

---

### Post by Sudeten on 2014-11-02
Ok, here is the WIRELESS info, thanks jeremy31 for the link:

```



########## wireless info START ##########

Report from: 02 Nov 2014 22:03 EST -0500

Booted last: 02 Nov 2014 00:00 EDT -0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
    Subsystem: Hewlett-Packard Company Device [103c:2ae0]
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0570]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 005: ID 0781:5530 SanDisk Corp. Cruzer
Bus 008 Device 004: ID 192f:0916 Avago Technologies, Pte. 
Bus 008 Device 003: ID 04ca:003a Lite-On Technology Corp. 
Bus 008 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0b95:1790 ASIX Electronics Corp. 
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              630653  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 50.static
netmask 255.255.255.240
gateway 50.gateway
dns-nameservers 75.75.75.75 78.78.76.76

auto eth1
iface eth1 inet static
address 50.static
netmask 255.255.255.240
gateway 50.gateway
dns-nameservers 75.75.75.75 78.78.76.76

auto wlan0
oface wlan0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

eth2      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

** (process:9268): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

** (process:9268): WARNING **: error: could not connect to NetworkManager

NetworkManager Tool

State: unknown

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

no-auto-default=<MAC address>,<MAC 'eth0' [IF]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/BlackBerry Mobile Hotspot 2504]] (600 root)
[connection] id=BlackBerry Mobile Hotspot 2504 | type=802-11-wireless
[802-11-wireless] ssid=BlackBerry Mobile Hotspot 2504 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wireless4ghz]] (600 root)
[connection] id=wireless4ghz | type=802-11-wireless
[802-11-wireless] ssid=wireless4ghz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

eth2      no frequency information.

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

eth2      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x4357 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

##### dmesg #############################

########## wireless info END ############



```

---

### Post by Sudeten on 2014-11-02
What information is needed for the WIRED connection?

---

### Post by Sudeten on 2014-11-02
Thanks in advance for your help!

---

### Post by jeremy31 on 2014-11-03
I would ```
sudo gedit /etc/NetworkManager/NetworkManager.conf
``` and add a # in front of every line after ```
iface lo inet loopback
``` Reboot and see if it works

---

### Post by Sudeten on 2014-11-03
The only thing in NetworkManager.conf is the following:

```


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=8C:AE:4C:FD:14:04,78:E3:B5:AE:7F:8B,

[ifupdown]
managed=true


```

---

### Post by grahammechanical on 2014-11-03
At a guess I would say that both network adapters (ethernet and Wifi) and not getting power or not switched on. This is what iwconfig -a shows on my machine

> eth0      Link encap:Ethernet  HWaddr 00:1a:92:82:d4:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


eth1      Link encap:Ethernet  HWaddr 00:1a:92:82:db:59  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe82:db59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34336615 (34.3 MB)  TX bytes:3373375 (3.3 MB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:218190 (218.1 KB)  TX bytes:218190 (218.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
          inet6 addr: fe80::215:afff:fe0e:9be0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:727852 (727.8 KB)  TX bytes:13049 (13.0 KB)


I have two ethernet (wired) adapters. One of which is connected. This is the one that is eth1 (the faster adapter). Do you notice, it says

> UP BROADCAST RUNNING MULTICAST

Whereas, eth0 says

> UP BROADCAST MULTICAST

I also have a WiFi adapter (wlan0). Which I have disabled by un-ticking the Enabled WiFi option in the Network icon menu. That also is 

> UP BROADCAST MULTICAST

So, RUNNING indicates a connected adapter and UP indicates a working adapter. Your three adapters only say

> BROADCAST MULTICAST

Your adapters are not UP. They are not powered, is my guess. Perhaps they have been disabled in the computer BIOS.

Regards.

---

### Post by Hadaka on 2014-11-03
Hi, let's do a little house cleaning and see what we can find.
please open a terminal then COPY and paste one line at a time
```
sudo sed -i 's/true/false/' /etc/NetworkManager/NetworkManager.conf
sudo rm /etc/udev/rules.d/70-persistent-net.rules
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a  /etc/modprobe.d/blacklist.conf 
```
BOOT
then do and post..
```
cat /etc/network/interfaces
rfkill list all
sudo modprobe -rf alx
sudo modprobe alx
```
BOOT
Got wired connection??

---

### Post by Sudeten on 2014-11-04
Hadaka, thanks for your help -- unfortunately it did  not work.

---

### Post by jeremy31 on 2014-11-04
Hadaka wants you to post the results from
```
cat /etc/network/interfaces
rfkill list all
sudo modprobe -rf alx
sudo modprobe alx
```

---

### Post by Sudeten on 2014-11-04
Thanks for your help, Hadaka, but this did not work.  Still the same problem.

---

### Post by Hadaka on 2014-11-04
Hi , Telling me "this did not work" gives me no real data
to work with. I asked you to please post the output of some
commands. So, again, post those outputs and hopefully
it will show reasons this is not working.
thanks.

---

### Post by jeremy31 on 2014-11-04
Sudeten, running the wireless script again should give Hadaka the info needed ```
./wireless_script
``` and paste the new wireless-info.txt

The ```
cat /etc/network/interfaces
``` was the file I meant to have you change but post what you see in terminal from that at least

The first wireless-info showed this
```
[COLOR=#000000][FONT=Ubuntu Mono]auto lo 
[/FONT][/COLOR]iface lo inet loopback

auto eth0
iface eth0 inet static
address 50.static
netmask 255.255.255.240
gateway 50.gateway
dns-nameservers 75.75.75.75 78.78.76.76

auto eth1
iface eth1 inet static
address 50.static
netmask 255.255.255.240
gateway 50.gateway
dns-nameservers 75.75.75.75 78.78.76.76

auto wlan0
oface wlan0 inet dhcp
```

---

### Post by Sudeten on 2014-11-19
Sorry for the delay - I have been out of town,  This is what i have:

```


cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 50.static
netmask 255.255.255.240
gateway 50.gateway
dns-nameservers 75.75.75.75 78.78.76.76

auto eth1
iface eth1 inet static
address 50.static
netmask 255.255.255.240
gateway 50.gateway
dns-nameservers 75.75.75.75 78.78.76.76

auto wlan0
oface wlan0 inet dhcp

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by Sudeten on 2014-11-19
BTW, the name of the adapter is:  AR8161 Gigabit Ethernet by Qualcomm Atheros.  Apparently there has been a problem with this before.  
[http://askubuntu.com/questions/288744/cant-connect-to-ethernet-with-atheros-ar8161-on-ubuntu-12-04-2](http://askubuntu.com/questions/288744/cant-connect-to-ethernet-with-atheros-ar8161-on-ubuntu-12-04-2)
[http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12](http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12)
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

However, all of these posts are more than a year old -- and before 14.04 that I am running.  Does anyone have an update on this?

---

### Post by Sudeten on 2014-11-19
I just looked at the "network" in the system manager again.  The only thing that shows is Network proxy (which is not in use).  However, a message popped up saying:  "The system network services are not compatible with this version."  What is that talking about?

---

### Post by Sudeten on 2014-11-19
I just ran the system test.  The report says the following:
WIRELESS:  Fontconfig warning: ignoring C.UTF8: not a valid language tag

WIRED: test gave these results:
```

Warning: Exception while talking to Network Manager over dbus. Skipping the remainder of this test. If this is a server, this is expected. 
The Error Generated was: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files ---------------------------[ Devices found by udev ]---------------------------- 
Category: NETWORK Interface: eth0 Product: AR8161 Gigabit Ethernet Vendor: Qualcomm Atheros Driver: alx (ver: 3.13.0-37-generic) Path: /devices/pci0000:00/0000:00:07.0/0000:01:00.0 
Category: NETWORK Interface: eth1 Product: AX88179 Vendor: ASIX Electronics Corp. Driver: ax88179_178a (ver: 3.13.0-37-generic) Path: /devices/pci0000:00/0000:00:10.0/usb7/7-1/7-1:1.0 
Category: WIRELESS Interface: wlan0 Product: BCM43225 802.11b/g/n Vendor: Broadcom Corporation Driver: brcmsmac (ver: 3.13.0-37-generic) Path: /devices/pci0000:00/0000:00:15.3/0000:04:00.0/bcma0:0 x

THE REPORT ALSO INCLUDED THIS INFO:

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
    Subsystem: Hewlett-Packard Company Device [103c:2ae0]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at e000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0570]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fe900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge



```

---

### Post by Sudeten on 2014-11-19
Here is some more from the system test:

```


    *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fea00000-feafffff
           *-network DISABLED
                description: Ethernet interface
                product: AR8161 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 08
                serial: 78:e3:b5:ae:7f:8b
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
                resources: irq:19 memory:fea00000-fea3ffff ioport:e000(size=128)
                
 *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:05:1b:a2:23:5f
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=ax88179_178a driverversion=22-Aug-2005 duplex=half firmware=ASIX AX88179 USB 3.0 Gigabit Et link=no multicast=yes port=MII speed=10Mbit/s
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 44:6d:57:73:4c:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-37-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
   

```

---

### Post by Sudeten on 2014-11-19
ok, my problem is resolved  for now.  I discovered that the network manager service was not running.
```

sudo service network-manager restart

```

got the wireless going again.

I then had to go change the wired to "true" for "managed" rather than the "false" which meant it was unmanaged.

```

sudo nano /etc/NetworkManager/NetworkManager.conf

```
change the line *managed=false* to *managed=true*
  Save, stop and start network manager:


```

sudo service network-manager restart

```

Thank you everyone for your help on this!

---

