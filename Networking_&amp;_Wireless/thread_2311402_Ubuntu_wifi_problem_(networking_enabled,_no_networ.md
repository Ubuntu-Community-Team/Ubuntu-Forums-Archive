---
title: "Ubuntu wifi problem (networking enabled, no networks showing)"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by Pictraz on 2016-01-26
I have a Dell Inspiron 15 7559.

I've installed Ubuntu on a partition on an external HDD, and boot from that.

When I click on available networks, none show up despite Enable Networking being checked. On Windows 10 on my main partition it works fine. Connecting using an ethernet cable works too.

I'm a bit of a noob when it comes to hardware problems like this, so please be gentle :)

---

### Post by papibe on 2016-01-26
Hi Pictraz. Welcome to the forum ):P

Start [here]("http://ubuntuforums.org/showthread.php?t=370108").

Let us know if you need more directions on how to follow those instructions.
Regards.

---

### Post by Pictraz on 2016-01-27
After running sudo apt-get update, it still didnt work.

This is the contents of wireless-info.txt:

```




########## wireless info START ##########

Report from: 27 Jan 2016 13:09 GMT +0000

Booted last: 27 Jan 2016 13:06 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Dell Device [1028:0706]
    Kernel driver in use: r8169

05:00.0 Network controller [0280]: Intel Corporation Device [8086:3165] (rev 79)
    Subsystem: Intel Corporation Device [8086:4410]

06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:522a] (rev 01)

##### lsusb #############################

Bus 002 Device 002: ID 174c:5106 ASMedia Technology Inc. Transcend StoreJet 25M3
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 1bcf:2b8a Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlwifi               188416  0 
mxm_wmi                16384  1 nouveau
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
cfg80211              524288  1 iwlwifi
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.101.129.141  Bcast:10.101.143.255  Mask:255.255.240.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:717624 (717.6 KB)  TX bytes:81609 (81.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.101.128.1    0.0.0.0         UG    0      0        0 eth0
10.101.128.0    0.0.0.0         255.255.240.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search customer.courtrooms.knightsbridge.lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       787     1  0 13:06 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.101.129.141
    Prefix:          20 (255.255.240.0)
    Gateway:         10.101.128.1

    DNS:             10.101.128.1

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

Region: Europe/London (based on set time zone)

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

[iwlwifi]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     B470AF663F8CCFC606AA966
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   12.229351] nouveau 0000:02:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[   12.229355] nouveau 0000:02:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[   19.093818] r8169 0000:04:00.0 eth0: link down
[   19.093851] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.385206] nouveau 0000:02:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[   25.385211] nouveau 0000:02:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[  111.740308] r8169 0000:04:00.0 eth0: link up
[  111.740316] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############




```

---

### Post by chili555 on 2016-01-27
> Network controller [0280]: Intel Corporation Device [[COLOR="#FF0000"]8086:3165[/COLOR]] (rev 79)
    Subsystem: Intel Corporation Device [8086:4410]There has been a lot of discussion about this tricky device. You probably *CAN'T* get the device working before kernel version 4.2 and newer. You have:> 3.19.0-47-genericIf it were me, I'd install Ubuntu 15.10 and be happy.

If, on the other hand, you'd like to compile stuff, edit files, post back to ask old Chili for help twenty times, grow a grey beard, etc., we can get started. It is your choice. 

I will be more than happy to help in either case.

---

### Post by Pictraz on 2016-01-27
Ah okay.

So if I get 15.10 it will work?

How much work will it take to get it working on this?

Is there much difference between 14.04 and 15.10?

I'll mainly be doing programming on this. C, Java, Python, Haskell, etc etc (uni stuff). For all intents and purposes, are the two versions the same?

I really appreciate old Chili for helping me btw :D

---

### Post by chili555 on 2016-01-27
It should only be a matter of renaming a couple of files.> Now we need the latest firmware. First, verify that you have these two files; iwlwifi-7265D-13.ucode and iwlwifi-7265-13.ucode:

```
ls /lib/firmware | grep 7265
```

If so, we are going to make copies but rename them:

```
cd /lib/firmware
sudo cp iwlwifi-7265D-13.ucode  iwlwifi-3165-9.ucode
sudo cp iwlwifi-7265-13.ucode  iwlwifi-3165-13.ucode

```
Reboot. Your wireless should be working....from here: [http://askubuntu.com/questions/713742/wireless-card-firmware-intel-3165-iwlwifi-only-available-for-kernel-4-1-any/713749#713749](http://askubuntu.com/questions/713742/wireless-card-firmware-intel-3165-iwlwifi-only-available-for-kernel-4-1-any/713749#713749) As you can see, the process for earlier (e.g. 3.19-xx) kernel versions is a bit complex.

To me, and I'm not a programmer, the versions are about the same except things work better in later versions, as is usually the case with newer versions of Ubuntu.

---

