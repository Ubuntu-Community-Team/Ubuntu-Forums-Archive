---
title: "Help, Lenovo laptop can't find wireless networks on 14.04, 15.04"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by ray25 on 2015-05-20
I installed the Ubuntu 14.04 on my Lenovo G50-80 laptop. Everything was fine, but I can't see any wireless networks for me to connect (see photo). 

[IMG]http://s23.postimg.org/uj21c2esn/image.jpg[/IMG]


I searched forums and have tried,


sudo apt-get update

sudo apt-get dist-upgrade

[FONT=Verdana]sudo modprobe -r ideapad-laptop
[/FONT]
[FONT=Verdana]Delet the bcmwl-kernel-source and re-install the new one
[/FONT]
[FONT=Verdana]Ungrade the system from 14.04 to 15.04, make the kernel to 3.19[/FONT]



But, none of these was working.


Please help, any input will be appreciated. See my wireless information below. Thanks.







[COLOR=#111111][FONT=Consolas]```


```[/FONT][/COLOR]```


########## wireless info START ##########


Report from: 20 May 2015 00:14 EDT -0400


Booted last: 19 May 2015 20:06 EDT -0400


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3821]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 004: ID 5986:0652 Acer, Inc 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 002: ID 17ef:602e Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


cfg80211              540672  0 
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 


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


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


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


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


########## wireless info END ############



```[COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-05-20
Unfortunately your wifi is very new to Linux and not yet supported.  There is a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)

---

### Post by Vladlenin5000 on 2015-05-20
> **jeremy31 said:**
> Unfortunately your wifi is very new to Linux and not yet supported.  There is a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)
^^^^
This. And trying a fix for Broadcom chips when you have an Atheros will only make things worse.

---

### Post by ray25 on 2015-05-20
Damn it. 
Not an expert, but I have been using Ubuntu for years. Don't want to go back to Win8.
Just dump my T60 and get this lenovo ideapad.
How long it may take to fix the bug? Should I wait?
Or I better return it and buy a Thinkpad (I assume Thinkpad is better supported?)

---

### Post by Vladlenin5000 on 2015-05-20
(wrong thread, sorry)

---

### Post by ray25 on 2015-05-20
Thank for replying.

I didn't get it. How I can know the it is 64 bit CPU with 32 bit UEFI?

In my laptop, it shows i5-5200U, which is called Broadwell, not Bay Trail

Thanks.

---

### Post by ray25 on 2015-05-20
Before I am buying a another laptop, what I can do to know it is already fully supported by Ubuntu. Thanks.

---

### Post by jeremy31 on 2015-05-20
I would contact Lenovo about a Realtek or Intel wifi card for your laptop

The maintenance manual [http://download.lenovo.com/consumer/mobiles_pub/lenovo_g_z_50_series_hmm.pdf](http://download.lenovo.com/consumer/mobiles_pub/lenovo_g_z_50_series_hmm.pdf) on page 80 lists a RTL8723BE and the Intel 3160

---

