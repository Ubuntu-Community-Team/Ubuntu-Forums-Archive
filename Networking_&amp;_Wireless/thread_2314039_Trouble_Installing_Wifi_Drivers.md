---
title: "Trouble Installing Wifi Drivers"
date: 2016-02-18
forum: Networking &amp; Wireless
---

### Post by karl16 on 2016-02-18
Hey everyone! I'm a total n00b at Linux and I'm having a heck of a time installing this driver. The documentation just doesn't explain it well enough for me. I'm using Ubuntu 15.10. One thing I'm worried about is that on the TPLink website, it says the driver is for Linux Kernel version 2.6~3.16. I guess Ubuntu 15.10 uses Linux Kernel 4.2. Could that alone render the driver inoperable?

Anyway,


This driver is for a USB Wifi Device, the Archer T2U C600 from TPLink.


I downloaded the Driver from the TPLink website. Opened the PDF documentation.


Basically, I'm stuck on step 2:


Step 1: Access the directory of the driver
Step 2: Before compile, make sure the path in makefile.c is suitable for your compile environment of your Linux system.


Then it says all this random code that leaves me scratching my head:



```
ifeq ($(WIFI_MODE),)
RT28xx_MODE = STA
else
RT28xx_MODE = $(WIFI_MODE)
endif
ifeq ($(TARGET),)
TARGET = LINUX
endif


#PLATFORM: Target platform
PLATFORM = PC


ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE =
endif

```



I opened the file called "makefile" in the driver directory, and it doesn't look anything like that code:


```
-----
all:
    make -C UTIL/ osutil
    $(SHELL) cp_util.sh
    make -C MODULE/ build_tools
    make -C MODULE/ osdrv
    $(SHELL) cp_module.sh
    make -C NETIF/ osnet


clean:
    make -C UTIL/ clean
    make -C MODULE/ clean
    make -C NETIF/ clean


install:
    make -C UTIL/ install_util
    make -C MODULE/ install
    make -C NETIF/ install_netif


uninstall:
    make -C UTIL/ uninstall
    make -C MODULE/ uninstall
    make -C NETIF/ uninstall

```

-----


Step 3: Type "sudo make" to compile the driver file


That doesnt work: I get multiple errors. 


```
make -C UTIL/ osutil
make[1]: Entering directory '/lib/firmware/Archer_T2U_V1_150901/Driver/UTIL'
cp -f os/linux/Makefile.6.util /lib/firmware/Archer_T2U_V1_150901/Driver/UTIL/os/linux/Makefile
make -C /lib/modules/4.2.0-27-generic/build SUBDIRS=/lib/firmware/Archer_T2U_V1_150901/Driver/UTIL/os/linux modules
make[2]: Entering directory '/usr/src/linux-headers-4.2.0-27-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory '/usr/src/linux-headers-4.2.0-27-generic'
make[1]: Leaving directory '/lib/firmware/Archer_T2U_V1_150901/Driver/UTIL'
/bin/sh cp_util.sh


make -C MODULE/ build_tools
make[1]: Entering directory '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE'
make -C tools
make[2]: Entering directory '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/tools'
gcc -g bin2h.c -o bin2h
make[2]: Leaving directory '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/tools'
/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/tools/bin2h
chipset = mt7650u
chipset = mt7630u
chipset = mt7610u
make[1]: Leaving directory '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE'
make -C MODULE/ osdrv
make[1]: Entering directory '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE'
cp -f os/linux/Makefile.6 /lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/Makefile
make -C /lib/modules/4.2.0-27-generic/build SUBDIRS=/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux modules
make[2]: Entering directory '/usr/src/linux-headers-4.2.0-27-generic'
  CC [M]  /lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.o
/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlShow’:
/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.c:7053:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.c:7053:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 , size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                     ^
/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_private_get_statistics’:
/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.c:9737:17: warning: unused variable ‘fec_coding’ [-Wunused-variable]
    static char *fec_coding[2] = {"bcc", "ldpc"};
                 ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.o' failed
make[3]: *** [/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1398: recipe for target '_module_/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux' failed
make[2]: *** [_module_/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE/os/linux] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-4.2.0-27-generic'
Makefile:548: recipe for target 'osdrv' failed
make[1]: *** [osdrv] Error 2
make[1]: Leaving directory '/lib/firmware/Archer_T2U_V1_150901/Driver/MODULE'
Makefile:3: recipe for target 'all' failed
make: *** [all] Error 2

```

So I guess my question is, how do I compile that code so I can "sudo make" it and go from there?

Thanks in advance for any help!

---

### Post by Bucky Ball on 2016-02-18
*Thread moved to **Networking and Wireless**.*

Welcome. Even though you're new you'll have a MUCH better chance of a fix here, and people will take your 'newbness' into account (won't we people?). ;)

Please run the wireless info script in my signature and post it back here between code tags (NOT quote tags - just replace where it says >  with [code] in the start and end tags or use the # icon in 'Go Advanced' ... see instructions in my signature).

For starters, you could open a terminal and

[QUOTE]sudo lshw -C network

Post that back to get us going while you're getting the wireless info together. :)

Please do not compile, install or insert anything else til we can have a look at this. It has the potential to cause major breakage in which case we'll need to retrace your steps to remove changes and rectify just to get back to the beginning.

Note: The maker and model of the USB dongle is often fairly irrelevant. A manufacturer may make 2, 3, 4 versions of the same model, all with different wireless chip in them! You need to find out what wireless card the dongle has then work from there. You may be trying to compile/install a driver for your model, but a different version with a different card. Problematic at best. :|

---

### Post by karl16 on 2016-02-18
Thanks buckyball!


I guess I should tell you, I already did try to install/compile it one other way before hand. I copied it into the /firmware directory and then used some kind of install command on it... i think it half works, because it detects that the device exists and is WiFi, but says "device not ready"


I wish I knew exactly what I did... i'll try to find out. I do have the driver unzipped to the /firmware directory.


The manufacturer releases drivers, here is the place I got it from: [http://www.tp-link.com/en/download/Archer-T2U.html#Driver](http://www.tp-link.com/en/download/Archer-T2U.html#Driver). I believe thats the exact same model I'm using, so it would have the same card and chipset, right?


Also, I have a wireless card built into the computer. That wireless card is defective, but will occasionally work for an hour or two at a time. Do I need to blacklist that card?


Anyway, sorry if I'm not making any sense, I'm just a confused (and slightly scared) n00b.


Here are the outputs you asked for.






Output for sudo -lshw -C network


```

*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 10
       serial: b8:70:f4:f1:a1:48
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:d1830000-d183ffff memory:d1840000-d184ffff memory:9fb00000-9fb007ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA


[/quote]


And wireless-info.txt:


[quote]


########## wireless info START ##########


Report from: 18 Feb 2016 20:41 PHT +0800


Booted last: 18 Feb 2016 00:00 PHT +0800


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3


##### lsusb #############################


Bus 004 Device 006: ID 1b1c:1b12 Corsair 
Bus 004 Device 004: ID 148f:761a Ralink Technology, Corp. 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 064e:d20c Suyin Corp. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              548864  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
mxm_wmi                16384  1 nouveau
video                  36864  3 i915,acer_wmi,nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0f0  Link encap:Ethernet  HWaddr <MAC 'enp2s0f0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0f0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2649058 (2.6 MB)  TX bytes:340233 (340.2 KB)
          Interrupt:16 


ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp2s0f0  no wireless extensions.


lo        no wireless extensions.


ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f0


##### resolv.conf #######################


nameserver 127.0.1.1
search domain.name


##### network managers ##################


Installed:


    NetworkManager


Running:


root       723     1  0 13:31 ?        00:01:24 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetLink BCM57785 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'enp2s0f0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0f0
GENERAL.IP-IFACE:                       enp2s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       4180f7bb-1c7a-44fa-bdea-550d234f66f4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4180f7bb-1c7a-44fa-bdea-550d234f66f4 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          domain.name
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1455885460
DHCP4.OPTION[9]:                        domain_name = domain.name
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.5
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0f0' [IF]>/64
IP6.GATEWAY:                            fe80::213:33ff:fedc:acc6


GENERAL.DEVICE:                         ra0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MediaTek
GENERAL.PRODUCT:                        WiFi
GENERAL.DRIVER:                         usb
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'ra0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.2/net/ra0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   unknown
WIFI-PROPERTIES.5GHZ:                   unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


[[/etc/NetworkManager/system-connections/HUAWEI-E5330-4AAE]] (600 root)
[connection] id=HUAWEI-E5330-4AAE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HUAWEI-E5330-4AAE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PLDTHOMEDSLKarl 2]] (600 root)
[connection] id=PLDTHOMEDSLKarl 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'ra0' [IF]> | mac-address-blacklist= | ssid=PLDTHOMEDSLKarl
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PLDTHOMEDSLKarl]] (600 root)
[connection] id=PLDTHOMEDSLKarl | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PLDTHOMEDSLKarl
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PLDTHOMEDSLKarl 1]] (600 root)
[connection] id=PLDTHOMEDSLKarl 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PLDTHOMEDSLKarl
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Manila (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp2s0f0  no frequency information.


lo        no frequency information.


ra0       0 channels
          Current Frequency:2.412 GHz


##### iwlist scan #######################


enp2s0f0  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


ra0       No scan results


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[25865.599778] !!! rt28xx init fail !!! (repeated 3 times)


########## wireless info END ############

```


Anyway, I just installed Linux, and I have all my files backed up an external. If I messed something up with trying to install too many drivers, I can always just wipe and reinstall the whole OS!

Thanks mucho! :D

---

### Post by Bucky Ball on 2016-02-18
Thanks. Now perhaps the output of these two commands:

```
lsusb
lsmod
```

May need to kill off those drivers you've attempted to install and yes, perhaps blacklist the internal card, denpending what it is. Forget for the moment about the drivers provided by the manufacturer. There are quite possibly others that work better (and they may already be in the kernel but being blocked by another). 

And I'll reiterate: [noparse]```

```[/noparse] tags please, not [quote] tags. Thanks. Added to your last post.

---

### Post by karl16 on 2016-02-18
Got it! Sorry about the code/quote thing; in my defense, the area my ethernet cable can reach is nowhere near a power source, (filipino construction - one power outlet per room) so I was operating in the last seconds of battery power when I sent that last post. Felt kind of like a super hacker defusing the bomb just in time... except it was a forum post and I'm still a noob. I'm a mess, I know :-&

Anyway, here's output of lsusb 

```

Bus 004 Device 003: ID 148f:761a Ralink Technology, Corp. 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 064e:d20c Suyin Corp. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I believe ralink technology is the USB dongle.

And lsmod

```

Module                  Size  Used by
nls_utf8               16384  1
isofs                  40960  1
ctr                    16384  0
ccm                    20480  0
drbg                   32768  1
ansi_cprng             16384  0
dm_crypt               28672  1
mt7650u_sta           917504  0
arc4                   16384  2
iwldvm                233472  0
uvcvideo               90112  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    86016  1
mac80211              733184  1 iwldvm
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
videobuf2_vmalloc      16384  1 uvcvideo
snd_hda_intel          36864  3
videobuf2_memops       16384  1 videobuf2_vmalloc
intel_rapl             20480  0
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
x86_pkg_temp_thermal    16384  0
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
intel_powerclamp       16384  0
coretemp               16384  0
snd_hwdep              16384  1 snd_hda_codec
acer_wmi               20480  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm_intel             167936  0
sparse_keymap          16384  1 acer_wmi
media                  24576  2 uvcvideo,videodev
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
kvm                   512000  1 kvm_intel
joydev                 20480  0
iwlwifi               200704  1 iwldvm
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  619
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
input_leds             16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
cfg80211              548864  3 iwlwifi,mac80211,iwldvm
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
serio_raw              16384  0
ablk_helper            16384  1 aesni_intel
cryptd                 20480  311 aesni_intel,ablk_helper
soundcore              16384  1 snd
shpchp                 36864  0
mei_me                 32768  0
mei                    98304  1 mei_me
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
nouveau              1388544  1
i915                 1130496  5
ahci                   36864  3
psmouse               126976  0
libahci                32768  1 ahci
ttm                    94208  1 nouveau
i2c_algo_bit           16384  2 i915,nouveau
drm_kms_helper        126976  2 i915,nouveau
tg3                   163840  0
drm                   356352  9 ttm,i915,drm_kms_helper,nouveau
sdhci_pci              24576  0
ptp                    20480  1 tg3
sdhci                  45056  1 sdhci_pci
pps_core               20480  1 ptp
mxm_wmi                16384  1 nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  36864  3 i915,acer_wmi,nouveau

```

I also found one of the fixes I tried. It was this:

```

mkdir ~/src
cd ~/src
git clone https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916.git
cd mt7610u_wifi_sta_v3002_dpo_20130916
make clean
make
sudo make install

```
from [Askubuntu]("http://askubuntu.com/questions/499091/trying-to-install-tp-link-archer-t2u-on-ubuntu").  That is what I believe got ubuntu to be able to properly detect the usb device was in fact a wifi device.

---

### Post by gordintoronto on 2016-02-19
When I was new to Ubuntu, I assumed I needed to install a Wi-Fi driver. However, it was not true; the wireless "just worked." Are you sure that you are not in the same situation? There might be a networking icon near the top-right of your screen, and by clicking on it, or maybe right-clicking (sorry, I haven't used Ubuntu for a long time; my main system is Xubuntu) you can enter the SSID and passphrase.

---

### Post by chili555 on 2016-02-20
> it says the driver is for Linux Kernel version 2.6~3.16. I guess Ubuntu 15.10 uses Linux Kernel 4.2. Could that alone render the driver inoperable?Yes, exactly. Your running kernel, 4.2.0-xx, is too new for the antique driver on TP-Link website.

I suggest you try this highly experimental method:```
sudo apt-get update
sudo apt-get install git
git clone https://sanrath@bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit
cd mediatek_mt7610u_sta_driver_linux-64bit
make
sudo make install
```Insert the device and then hopefully connect.

The package 'makes' for me with many warnings but no errors. Whether this prevents correct operation, I do not know. I haven't the device.

We look forward to your report.

---

