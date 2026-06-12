---
title: "wireless problem after &quot;installing drivers&quot; button"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by notaki on 2014-10-10
hello everyone,

im new in ubuntu and i try to fix my wireless but i cant. I have read all the post and I am confused. 
system information: 
```
-Version-
Kernel        : Linux 3.2.0-69-generic-pae (i686)
Compiled        : #103-Ubuntu SMP Tue Sep 2 05:15:53 UTC 2014
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
Distribution        : Ubuntu 12.04.5 LTS
-Current Session-
Computer Name        : linuxlite-Lenovo
COMPUTER : LENOVO S10E NOTEBOOK

Ethernet controller        : Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
Network controller        : Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

i dont know what else to do.
after all camera not working.

please help

---

### Post by jeremy31 on 2014-10-10
Start by opening a terminal window and enter this ```
[COLOR=#000000][FONT=Ubuntu Mono]lspci -nn -d 14e4:
```
And post the terminal output[/FONT][/COLOR]

---

### Post by notaki on 2014-10-10
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)


```

---

### Post by westie457 on 2014-10-10
Try this ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge bcmwl-kernel-source
[/FONT][/COLOR]sudo apt-get remove --purge linux-firmware-nonfree

sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```
Ignore any moans and errors about things not being installed and files not found.

---

### Post by notaki on 2014-10-10
no luck . i copy paste the code, no errors was found and i rebooted. but still it shows that "wireless is disabled from the switch". fn+f5 doesnt work.
is there anything else i can try ?
i have done update, upgrade already

---

### Post by westie457 on 2014-10-10
If this does not work ```
rfkill unblock all
``` go to here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) to download and run a wireless script. Either post the text file here or post the output inside [code] tags please.

---

### Post by notaki on 2014-10-10
i did it i reboot but nothing. here is the wireless script.


```

########## wireless info START ##########

Report from: 10 Oct 2014 13:39 EEST +0300

Booted last: 10 Oct 2014 13:28 EEST +0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-70-generic-pae #105-Ubuntu SMP Wed Sep 24 20:08:22 UTC 2014 i686 i686 i386 GNU/Linux

Parameters: ro, splash, quiet, vt.handoff=7

##### desktop ###########################

Xfce

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
    Kernel driver in use: tg3

05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   342801  0 
ideapad_laptop         17890  0 
sparse_keymap          13658  1 ideapad_laptop
bcma                   25651  1 b43
brcmsmac              540923  0 
mac80211              436493  2 b43,brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178877  3 b43,brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12518  1 brcmsmac
ssb                    50691  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe40:cacf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540895 (540.8 KB)  TX bytes:242446 (242.4 KB)
          Interrupt:16 

pan1      Link encap:Ethernet  HWaddr <MAC 'pan1' [IF]>  
          inet addr:10.123.172.1  Bcast:10.123.172.255  Mask:255.255.255.0
          inet6 addr: fe80::3c43:faff:fe02:6bd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:19833 (19.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

pan1      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.123.172.0    0.0.0.0         255.255.255.0   U     0      0        0 pan1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

grep: /etc/resolv.conf: No such file or directory

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
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
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NOTAKI]] (600 root)
[connection] id=NOTAKI | type=802-11-wireless
[802-11-wireless] ssid=NOTAKI | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ThomsonC33D88]] (600 root)
[connection] id=ThomsonC33D88 | type=802-11-wireless
[802-11-wireless] ssid=ThomsonC33D88 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/stones]] (600 root)
[connection] id=stones | type=802-11-wireless
[802-11-wireless] ssid=stones | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Booking Rooms]] (600 root)
[connection] id=Booking Rooms | type=802-11-wireless
[802-11-wireless] ssid=Booking Rooms | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

pan1      no frequency information.

lo        no frequency information.

eth0      no frequency information.

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

##### iwlist scan #######################

pan1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     E053F8EBD0827A355C398D3
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

[bcma]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
depends:        
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 

[brcmsmac]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1944D882391CC5F32CA6325
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[brcmutil]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 

[cfg80211]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A289A224DC04F871A44431D
depends:        
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
depends:        
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 

##### module parameters #################

[b43]
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
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
lp
brcmsmac
b43

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
blacklist b43
blacklist wl

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[   25.632629] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2014-10-10
```
sudo apt-get install firmware-b43-lpphy-installer
```
```
sudo modprobe -r b43
```
```
sudo modprobe b43
```

---

### Post by notaki on 2014-10-10
the same again.
what is going on ? what can i do now ?
the wireless is disabled from the switch.

thanks anyway.

---

### Post by jeremy31 on 2014-10-10
```
sudo modprobe -r brcmsmac
``````
modprobe -r ideapad_laptop
``````
rfkill unblock all
```
See if rfkill still shows blocked

---

### Post by notaki on 2014-10-10
i am sorry but nothing happened again. i rebooted and shows the same message.
how can i see if rfkill still shows blocked ?

---

### Post by notaki on 2014-10-10
[CODE] $ sudo rfkill list
[sudo] password for linuxlite: 
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

[/CODE/ 

COULD THIS HELP ?

---

### Post by jeremy31 on 2014-10-10
Ok, according to the S10e user guide their is a button near the display, on the right side- pressing this should remove the hard block

FN+F5 should remove the soft block but since the FN functioning can be toggled in BIOS, you may just need to press F5

[http://download.lenovo.com/pccbbs/mobiles_pdf/45m2089.pdf](http://download.lenovo.com/pccbbs/mobiles_pdf/45m2089.pdf) is the guide the location of the first button is on page 1 and labelled 9

---

### Post by notaki on 2014-10-10
i cant believe it!!! 
a lot of thanks. 
I was trying fn+f5 but it was thewireless button. 
thanks very much.

---

### Post by notaki on 2014-10-10
ok i fix and bluetooth by the same way. thanks a lot. 
Goodnight!

---

### Post by jeremy31 on 2014-10-10
Great, I looked back through the posts and don't see anything that needs to be changed, please go to your original post, find "thread tools" and select mark as solved

If you have a problem locating it,  [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

