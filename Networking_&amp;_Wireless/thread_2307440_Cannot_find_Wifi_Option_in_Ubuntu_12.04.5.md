---
title: "Cannot find Wifi Option in Ubuntu 12.04.5"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by write2diba on 2015-12-25
Hello,
     I have recently installed Ubuntu 12.04.5 in my Laptop. But I can connect to wired network only. In Windows I can connect to the Wifi but in Ubuntu no option to connect with the Wifi is being shown. Please help me out. I don't know what to do.


Thanks

---

### Post by weatherman2 on 2015-12-25
Try re-posting in the "Networking & Wireless" forum.  Before posting there, find the "sticky" post at the top of that forum that includes a wireless script you will eventually be asked to run, anyway, so that people will have specific information about your laptop to be able to offer help.  If possible, plug the laptop temporarily into an ethernet connection with a cable to get a temporarily internet connection so you can download the wireless script; unplug the cable, run the script, then re-connect it and post the results on your new thread.

If you cannot connect with an ethernet cable, download the wireless script with Windows first (maybe onto a flash drive) then re-boot Ubuntu, run the script, save the output to the flash drive, then re-boot Windows again and post the results.

---

### Post by Bucky Ball on 2015-12-25
*Thread moved to **Networking and Wireless**.*

> **weatherman2 said:**
> Try re-posting in the "Networking & Wireless" forum.

Please *_**do not**_* post duplicate threads about the same support issue. If you want a thread moved, report it and ask staff to move it for you. Thanks.

Supply the output of this command, please:

```
sudo lshw -C network
```

---

### Post by write2diba on 2015-12-25
> **weatherman2 said:**
> Try re-posting in the "Networking & Wireless" forum.  Before posting there, find the "sticky" post at the top of that forum that includes a wireless script you will eventually be asked to run, anyway, so that people will have specific information about your laptop to be able to offer help.  If possible, plug the laptop temporarily into an ethernet connection with a cable to get a temporarily internet connection so you can download the wireless script; unplug the cable, run the script, then re-connect it and post the results on your new thread.

If you cannot connect with an ethernet cable, download the wireless script with Windows first (maybe onto a flash drive) then re-boot Ubuntu, run the script, save the output to the flash drive, then re-boot Windows again and post the results.


Sorry.. I missed the thread actually... I will keep in mind before posting in forums...

thank you for replying.. As you told me to run the script I did and I got the following result




```
########## wireless info START ##########

Report from: 26 Dec 2015 21:14 IST +0530

Booted last: 26 Dec 2015 21:12 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: loop=/ubuntu/disks/root.disk, ro, quiet, splash, acpi_osi=Linux, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 0a)
    Subsystem: Lenovo Device [17aa:3830]
    Kernel driver in use: r8169

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
    Subsystem: XAVi Technologies Corp. Device [1b9a:2485]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 006: ID 0000:0538  
Bus 002 Device 005: ID 17ef:7924 Lenovo 
Bus 002 Device 002: ID 174f:1169 Syntek 
Bus 002 Device 003: ID 04f2:b49f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              91457  0 
rtl8723_common         23427  1 rtl8723be
rtl_pci                27310  1 rtl8723be
rtlwifi                64281  2 rtl8723be,rtl_pci
mac80211              658171  3 rtl8723be,rtl_pci,rtlwifi
cfg80211              502970  2 rtlwifi,mac80211
btcoexist              55886  1 rtl8723be
ideapad_laptop         18462  0 
sparse_keymap          13890  1 ideapad_laptop
wmi                    19363  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.59  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:290300 (290.3 KB)  TX bytes:106869 (106.8 KB)

##### iwconfig ##########################

usb0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.0.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       965     1  0 21:12 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.59
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

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
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

usb0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

usb0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

##### rc.local ##########################

echo 0 > /sys/class/backlight/ideapad/brightness

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[   14.289662] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   14.414485] rtl8723be 0000:04:00.0: Direct firmware load failed with error -2
[   14.414487] rtl8723be 0000:04:00.0: Falling back to user helper
[   14.438635] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available
[   18.607278] r8169 0000:03:00.0 eth1: link down
[   18.607842] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   69.619153] rndis_host 2-2:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-2, RNDIS device, <MAC 'usb0' [IF]>

########## wireless info END ############

```

---

### Post by write2diba on 2015-12-25
> **Bucky Ball said:**
> *Thread moved to **Networking and Wireless**.*



Please *_**do not**_* post duplicate threads about the same support issue. If you want a thread moved, report it and ask staff to move it for you. Thanks.

Supply the output of this command, please:

```
sudo lshw -C network
```


As you told me to run the command I did and got the following result 





```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 0a
       serial: f0:76:1c:de:09:0f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:108 ioport:2000(size=256) memory:90504000-90504fff memory:90500000-90503fff
  *-network
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rtl8723be latency=0
       resources: irq:19 ioport:1000(size=256) memory:90400000-90403fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 36:68:4f:16:b0:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.59 link=yes multicast=yes

```

---

### Post by Bucky Ball on 2015-12-25
Please replace your [quote] tags with [code] tags. Code tags for terminal output, thanks. See post #4 for an example and see last link in my signature for further instructions. :)

---

### Post by write2diba on 2015-12-25
> **Bucky Ball said:**
> Please replace your [quote] tags with [code] tags. Code tags for terminal output, thanks. See post #4 for an example and see last link in my signature for further instructions. :)



Yes... Did as you told me.. 

But what about the code... Did it help you to know anything about the problem...???

---

### Post by weatherman2 on 2015-12-26
This looks like your problem:

```



##### dmesg #############################


[   14.289662] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   14.414485] rtl8723be 0000:04:00.0: Direct firmware load failed with error -2

```

You have a Realtek wireless card, but the firmware could not be loaded.  This is not an uncommon problem, but I don't have much experience myself with Realtek wireless cards.  Someone here is likely to pop up with a simple solution eventually, but in the meantime you can do a web search for this problem and look for a solution.

But it may be that you simply need to obtain missing firmware files - as described in this similar problem:

[https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg21679.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg21679.html)

---

### Post by praseodym on 2015-12-26
PLease install this new firmware package by double-click and reboot afterwards:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb)

---

### Post by write2diba on 2015-12-26
> **praseodym said:**
> PLease install this new firmware package by double-click and reboot afterwards:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb)



Thank you very much.. It worked like a charm.... Wireless connection is now possible... :)

---

