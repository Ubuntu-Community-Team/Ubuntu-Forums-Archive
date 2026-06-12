---
title: "No wireless connection with bcm4331 (linux-firmware-nonfree)"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by baabsaget on 2014-12-01
Hello,

My wifi connection suddenly became flaky with ubuntu a couple of months ago, and I found you broadcom wireless table which instructed me to install linux-firmware-nonfree. I removed firmware-b43-installer and installed linux-firmware-nonfree and rebooted but there is no wireless connection. Any way to get it to work? Also, I found that when I attempted to use a wired connection while the firmware-b43-installer driver was active, the wired connection would freeze up after about 10 minutes of usage. After removing the wifi driver, the wired connection now seems to work properly.

---

### Post by Hadaka on 2014-12-01
hi, please post the output of..
```
uname -r
cat /etc/issue
lspci -nn | egrep '0200|0280'
lsmod | egrep 'wl|b43'
rfkill list all
```
thanks.

---

### Post by baabsaget on 2014-12-01
uname -r
3.13.0-37-generic

cat /etc/issue
Ubuntu 14.04.1 LTS \n \l


lspci -nn | egrep '0200|0280'
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

lsmod | egrep 'wl|b43'
b43                   387371  0 
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
bcma                   52096  1 b43

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by Hadaka on 2014-12-01
Hi, let's see if we can get the offline method to
get it working. please do..
```
sudo apt-get remove --purge firmware-b43-installer
```
then go here..
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
post #7, copy the zip file first
then do..
```
sudo modprobe -rf b43
sudo modprobe b43
```
once online..do..
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

---

### Post by baabsaget on 2014-12-01
still no wifi connection after following your instructions. I have an ethernet cable so I can use online methods.

---

### Post by Hadaka on 2014-12-01
hi, please post the wireless script.
copy and paste this into a terminal it will create a wireless-info.txt
file in your home diretory,paste that file here.
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
thanks.

---

### Post by baabsaget on 2014-12-01
```

########## wireless info START ##########


Report from: 01 Dec 2014 14:48 EST -0500


Booted last: 01 Dec 2014 12:32 EST -0500


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


\boot\vmlinuz-3.13.0-37-generic.efi.signed, ro, initrd=boot\initrd.img-3.13.0-37-generic


##### desktop ###########################


GNOME Flashback (Compiz)


##### lspci #############################


01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
	Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
	Kernel driver in use: tg3


02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
	Subsystem: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]
	Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 002 Device 006: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13ba:0018 PCPlay Barcode PCP-BCG4209
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


b43                   387371  0 
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
bcma                   52096  1 b43


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aa20:66ff:fe05:4364/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:655994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:962945168 (962.9 MB)  TX bytes:22865780 (22.8 MB)
          Interrupt:16 


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
search home


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
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


[[/etc/NetworkManager/system-connections/25XF4]] (600 root)
[connection] id=25XF4 | type=802-11-wireless
[802-11-wireless] ssid=25XF4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SCS-StChris]] (600 root)
[connection] id=SCS-StChris | type=802-11-wireless
[802-11-wireless] ssid=SCS-StChris | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/STCVA]] (600 root)
[ipv6] method=auto
[connection] id=STCVA | type=802-11-wireless
[802-11-wireless] ssid=STCVA | mac-address=<MAC address>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/martins]] (600 root)
[connection] id=martins | type=802-11-wireless
[802-11-wireless] ssid=martins | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Thomas's iPhone]] (600 root)
[connection] id=Thomas's iPhone | type=802-11-wireless
[802-11-wireless] ssid=Thomas's iPhone | mac-address=<MAC address>
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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


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


coretemp


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


echo 5 > /sys/class/backlight/acpi_video0/brightness


echo 0 | tee /sys/class/leds/smc::kbd_backlight/brightness


chmod 777 /sys/power/state


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="wl"


[/etc/pm/config.d/defaults] (644 root)
SLEEP_MODULE="uswsusp"


[/etc/pm/config.d/module] (644 root)
SLEEP_MODULE=uswsusp


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############

```

---

### Post by Hadaka on 2014-12-01
Hi your wireless driver says 
```
Kernel driver in use: bcma-pci-bridge
```
and it should say..
```
Kernel driver in use: b43-pci-bridge
```
please do..
```
sudo modprobe -rf bcma
```
then repeat the last commands and load the driver
offline..
report back a wireless script when done.
thanks

---

### Post by baabsaget on 2014-12-01
```

thomas@thomas-swagbook-pro:~$ sudo modprobe -rf bcma
[sudo] password for thomas: 
modprobe: FATAL: Module bcma is in use.

```

lsmod says that bcma is in use by b43. If I unload b43 and bcma, lspci reports no driver in use by the wifi card. If I load b43 again, lspci goes back to saying that bcma-pci-bridge is in use.

---

### Post by Hadaka on 2014-12-01
ok...it should not be saying "In Use"
disable the network or whatever you have to do,
delete b43 driver. disconnect the cable...LOAD
the driver and SHOW the results of doing so...offline
just follow the instructions in post 7 that i sent you. I know
you have a working cable connection, but, this works better
sometimes.

---

### Post by baabsaget on 2014-12-02
I followed your instructions in post 7 while offline with no ethernet or anything and ran the script again like you said.

```

########## wireless info START ##########

Report from: 02 Dec 2014 09:35 EST -0500

Booted last: 02 Dec 2014 09:34 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

\boot\vmlinuz-3.13.0-37-generic.efi.signed, ro, initrd=boot\initrd.img-3.13.0-37-generic

##### desktop ###########################

GNOME Flashback (Compiz)

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00f5]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 006: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   387371  0 
bcma                   52096  1 b43
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43

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
          Interrupt:16 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/25XF4]] (600 root)
[connection] id=25XF4 | type=802-11-wireless
[802-11-wireless] ssid=25XF4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SCS-StChris]] (600 root)
[connection] id=SCS-StChris | type=802-11-wireless
[802-11-wireless] ssid=SCS-StChris | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/STCVA]] (600 root)
[ipv6] method=auto
[connection] id=STCVA | type=802-11-wireless
[802-11-wireless] ssid=STCVA | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/martins]] (600 root)
[connection] id=martins | type=802-11-wireless
[802-11-wireless] ssid=martins | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Thomas's iPhone]] (600 root)
[connection] id=Thomas's iPhone | type=802-11-wireless
[802-11-wireless] ssid=Thomas's iPhone | mac-address=<MAC address>
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

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

coretemp

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

echo 5 > /sys/class/backlight/acpi_video0/brightness

echo 0 | tee /sys/class/leds/smc::kbd_backlight/brightness

chmod 777 /sys/power/state

exit 0

##### pm-utils ##########################

[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="wl"

[/etc/pm/config.d/defaults] (644 root)
SLEEP_MODULE="uswsusp"

[/etc/pm/config.d/module] (644 root)
SLEEP_MODULE=uswsusp

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[    5.688607] b43 bcma0:0: Direct firmware load failed with error -2
[    5.688608] b43 bcma0:0: Falling back to user helper
[    5.690251] b43 bcma0:0: Direct firmware load failed with error -2
[    5.690253] b43 bcma0:0: Falling back to user helper
[    5.690989] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[    5.690990] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[    5.690991] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   54.809031] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
[   54.809062] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   54.809085] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   54.809134] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   54.860067] bcma: bus0: Bus registered
[   54.864630] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   54.865073] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   54.865608] b43 bcma0:0: Direct firmware load failed with error -2
[   54.865610] b43 bcma0:0: Falling back to user helper
[   54.866386] b43 bcma0:0: Direct firmware load failed with error -2
[   54.866389] b43 bcma0:0: Falling back to user helper
[   54.867289] b43 bcma0:0: Direct firmware load failed with error -2
[   54.867292] b43 bcma0:0: Falling back to user helper
[   54.867708] b43 bcma0:0: Direct firmware load failed with error -2
[   54.867711] b43 bcma0:0: Falling back to user helper
[   54.868532] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[   54.868535] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[   54.868538] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############



```

---

### Post by Hadaka on 2014-12-02
ok,  please connect to the internet via cable and do,,
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
now it is working?

---

### Post by slickymaster on 2014-12-02
> **Hadaka said:**
> ok,  please connect to the internet via cable and do,,
```
sudo apt-get update
sudo apt-get upgrae
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
now it is working?

Sorry for stepping in Hadaka, but it's just to alert the OP that there's a typo in your second command, you forget the 'd'.

@baabsaget:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```

---

### Post by baabsaget on 2014-12-03
yes, the internet works with firmware-b43-installer installed, but it is flaky. I thought from your chart that getting linux-firmware-nonfree might alleviate this problem. Sometimes when I resume from suspend the wifi will just try to connect forever, and sometimes when I am continuously pushing data through the card it sometimes becomes extremely slow for 10 seconds or so and then come back as normal. if the drivers are just bad then that's what it is but I thought that linux-firmware-nonfree was a more correct driver than firmware-b43-installer from your chart and was wondering if it would be better.

---

### Post by Hadaka on 2014-12-03
Linux-firmware-nonfree is no longer available.
It was on "loan" from the broadcomm bunch and they
decided not to share with the linux crowd anylonger.
so it went away a couple months ago.That leaves only the b43
for the 4311 card.please mark this thread solved
thanks.

---

### Post by jeremy31 on 2014-12-03
> **baabsaget said:**
> yes, the internet works with firmware-b43-installer installed, but it is flaky. I thought from your chart that getting linux-firmware-nonfree might alleviate this problem. Sometimes when I resume from suspend the wifi will just try to connect forever, and sometimes when I am continuously pushing data through the card it sometimes becomes extremely slow for 10 seconds or so and then come back as normal. if the drivers are just bad then that's what it is but I thought that linux-firmware-nonfree was a more correct driver than firmware-b43-installer from your chart and was wondering if it would be better.

What chart are you referring to?  It was back in September when the Broadcom firmware was removed from linux-firmware-nonfree but the firmware should be the same using firmware_b43_installer
It seems the old version of linux-firmware-nonfree is still available to download;--http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download

---

### Post by baabsaget on 2014-12-03
jeremy31,

your old version of linux-firmware-nonfree worked when I installed it in place of firmware-b43-installer. it connects to networks faster and resumes from suspend correctly. thanks so much!

---

