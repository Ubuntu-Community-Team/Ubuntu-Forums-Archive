---
title: "Wireless Internet Adapter goose chase"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by tws2 on 2015-04-26
Greetings Ubuntu Nation, 

[U]Intro:
[/U]I am TWS, and I'm a brand new Noob to Ubuntu/Linux Universe. I've successfully installed Ubuntu 14.04 LTS Trusty Tahr, (dual) alongside Windows 7. I've used a hardwire to update/upgrade to the latest. 

_Problem:_
I bought an Asus USB-AD51 wireless adapter, Dual Band, Wireless-AC600. It supports both Linux and Windows 7. I put in the install disc and it pops up, but it doesn't install anything. The disc comes with a file called "Quick Start DPO.txt," when I open it, the top line reads "MT7610u Linux Driver quick start".

This file begins with:

Check tools: *Before install driver, please check already install compile tool and kernel source code. 

1> Install compile tool
     $yum install gcc-c++

2> Check kernel source code exists /usr/src/kernels/ "kernel name"

      Download your kernel source code
      *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/)
                or
      $yum install kernel-devel

It then has a section called "Build Instructions", looks like a code script to install the driver or something. 

I tried step 1 and 2 but it didn't work right. Thinking there was an easier answer, I turned to Google-ing...

_The Goose Chase:_
My fellow Ubuntu-nians, I will humbly admit, I'm not an expert at any of this, but I do Google everything and make an honest effort to figure everything out. It works 99% of the time; now it's not. I've spent the last few days and hours and hours searching and trying new things. Nothing is working. I tried the wireless script that diagnoses my system, but I can't get that to work right, either. 

I'm extremely frustrated and ready to break something or someone, I've been patient, now I'm not.

Please help, 
Sincerely, 
TWS

---

### Post by ian-weisser on 2015-04-26
'Linux support' could mean one of two things:
1) It works out-of-the-box. The manufacturer has *already* added the driver to the Linux kernel. **This is what you want.**
2) You compile your own kernel with the driver they provide. The manufacturer hasn't bothered to add the driver to the Linux kernel, or the kernel admins rejected it for poor quality. **This is that you seem to have**.

Manufacturers of the second kind were tolerated 15 years ago when most  Linux users knew how to compile their own kernel. 
However, there is no excuse for it  today. The Linux community fully expects reputable manufacturers to be the first kind. Shame on Asus.

If the dongle doesn't work out-of-the-box (try it!), then **return it**. Exchange it for one that will work out-of-the box.
Complain directly to Asus for lying about Linux compatibility.
Feel free to badmouth them in every online forum you are a member of.

If you decide you want to learn how to recompile your Ubuntu kernel to include the dongle driver, see [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
It's worth learning, but it's **not** a task for beginners. It's not obvious nor easy nor fast the first time you do it.

---

### Post by tws2 on 2015-04-26
Thanx for replying; I think I'm just doing something wrong.

---

### Post by wildmanne39 on 2015-04-26
Those directions are not for ubuntu, and the drivers supplied on disc rarely work to install because of kernel differences, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by tws2 on 2015-04-26
```

########## wireless info START ##########

Report from: 26 Apr 2015 19:53 PDT -0700

Booted last: 26 Apr 2015 15:58 PDT -0700

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:2a78]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 006: ID 154b:007a PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd HP Multimedia Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              494362  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2605:e000:ac08:3e00:187b:d818:44c4:1e0a/64 Scope:Global
          inet6 addr: 2605:e000:ac08:3e00:4261:86ff:fe0f:e2ed/64 Scope:Global
          inet6 addr: fe80::4261:86ff:fe0f:e2ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4530882 (4.5 MB)  TX bytes:378121 (378.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

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
    Address:         192.168.0.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62

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

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2015-04-26
The device did not show up, did you have it plugged in when you ran the script? if not just post the results of:
```
lsusb
```
Thanks

---

### Post by tws2 on 2015-04-26
No, I didn't. I'll do it now.

---

### Post by tws2 on 2015-04-26
```
Bus 001 Device 007: ID 0b05:17d1 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd HP Multimedia Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by tws2 on 2015-04-26
Wireless Script Run with device plugged in.

```

########## wireless info START ##########

Report from: 26 Apr 2015 20:09 PDT -0700

Booted last: 26 Apr 2015 15:58 PDT -0700

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:2a78]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 007: ID 0b05:17d1 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd HP Multimedia Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              494362  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2605:e000:ac08:3e00:187b:d818:44c4:1e0a/64 Scope:Global
          inet6 addr: 2605:e000:ac08:3e00:4261:86ff:fe0f:e2ed/64 Scope:Global
          inet6 addr: fe80::4261:86ff:fe0f:e2ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7436450 (7.4 MB)  TX bytes:1082884 (1.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

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
    Address:         192.168.0.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62

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

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2015-04-26
I am researching that device so I need a few minutes.

---

### Post by tws2 on 2015-04-26
Ok, thanx.

---

### Post by tws2 on 2015-04-26
This is what came on the install disc:

---

### Post by tws2 on 2015-04-26
It opens as:

```
MT7610U Linux Driver quick start         
 
==================== 
Check tools:   

==================== 
*Before install driver, please check already install compile tool and  kernel source code 
 
1>Install compile tool 
    $yum install gcc-c++ 
 
2>check kernel source code exists /usr/src/kernels/ "kernel name" 
 
    Download your kernel source code 
    *http://www.kernel.org/pub/linux/kernel/          
    or 
    $yum install kernel-devel 
 
 
 
==================== 
Build Instructions:   

==================== 
1> $tar -xvf mt7610u_wifi_sta_vxxxx_dpo_xxxxxxxx.tar.bz2 
     go to "mt7610u_wifi_sta_vxxxx_dpo_xxxxxxxx" directory. 
     
 

2> In Makefile
      
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
      
     define the linux kernel source include file path LINUX_SRC
      
     modify to meet your need.
 
 
3> In os/linux/config.mk 
     
     define the GCC and LD of the target machine
     
     define the compiler flags CFLAGS
     
     modify to meet your need. 
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
        
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
               
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d 
     ** Build for being controlled by WpaSupplicant with Ralink Driver
        
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
        
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d 
 
4> $make            
     
     # compile driver source code, need administrator.
     
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c 
 
5> $make install 
     #install driver 
     #copy RT2870STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat 
 
6>$vi /etc/rc.d/rc.local 
     #input "ifconfig ra0 up" 
 
     ** Ubuntu 13.04 don't have this file. 
    $reboot 
 
7> unload driver    
     
     $ifconfig ra0 down 

     $make uninstall 
     $reboot 
 
 
Note: If you want to change os/linux/config.mk setting, please remove driver and  reinstall.
```

---

### Post by wildmanne39 on 2015-04-26
I have not found anyone with that device that got it to work. 
the device id is 0b05:17d1 and that is how you find the driver you need. The only driver I found said it works on kernel 3.11 so it is to old, you could try ndiswrapper but someone else will have to help with that, or you could return it and get one that is supported. I do not have any suggestions for the best one to get.
I am sorry I do not have better news.
[http://mediatek.com/en/downloads/mt7610u-usb/](http://mediatek.com/en/downloads/mt7610u-usb/)

---

### Post by tws2 on 2015-04-27
Understood. Thanx for trying.

---

