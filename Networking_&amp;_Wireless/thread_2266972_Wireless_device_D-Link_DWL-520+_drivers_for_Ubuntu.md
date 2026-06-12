---
title: "Wireless device D-Link DWL-520+ drivers for Ubuntu 14.04"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by RaphaalBar on 2015-02-26
I have spent quite some hours now to get this working, but I am stuck. I use an old PC with 512 MB RAM and an Intel processor and the LXDE desktop, no performance problems there.

 If I lspci the card shows up:
```
02:08.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
```

ifconfig gives no trace of the device:
```
eth0      Link encap:Ethernet  HWaddr 00:07:e9:e3:50:12            inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fee3:5012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12605172 (12.6 MB)  TX bytes:2287923 (2.2 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186313 (186.3 KB)  TX bytes:186313 (186.3 KB)



```

On another machine, some time ago I got it going with ndiswrapper by just pointing it to the *.inf file of the windows driver as described  here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Now ndiswrapper only gives me an "Invalid driver", when I point it at GPLUS.inf (Got the driver from D-Link, unzipped it, unshielded the cab file and found several .inf files, apparently for different OSs. I chose the newest one - from the folder InfXP).

**If anyone could help me at this point I would be happy :-)**
[SIZE=1]If not here is what else I tried so far:

I also tried compiling the driver according to this old thread [http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303). But after the make command I do not get an acx.ko file, so I do not know how to proceed. Here is what happened:
```
[/SIZE]user335@user335:~$ cd WLAN-driver-files/acx/user335@user335:~/WLAN-driver-files/acx$ tar xjvf acx-20080210.tar.bz2
acx-20080210/
acx-20080210/wlan_hdr.h
acx-20080210/Makefile
acx-20080210/acx.h
acx-20080210/acx_func.h
acx-20080210/pci.c
acx-20080210/usb.c
acx-20080210/README
acx-20080210/acx_config.h
acx-20080210/wlan_compat.h
acx-20080210/Kconfig
acx-20080210/conv.c
acx-20080210/setrate.c
acx-20080210/common.c
acx-20080210/wlan_mgmt.h
acx-20080210/pktgen/
acx-20080210/pktgen/mk
acx-20080210/pktgen/README
acx-20080210/pktgen/sendpkt
acx-20080210/pktgen/sendpkt.c
acx-20080210/pktgen/printhex
acx-20080210/pktgen/printhex.c
acx-20080210/script/
acx-20080210/script/module_sizes.sh
acx-20080210/script/start_net.sh
acx-20080210/script/run_splint.sh
acx-20080210/script/crashme.sh
acx-20080210/script/inject_kernel_tree.sh
acx-20080210/script/count_ACX.sh
acx-20080210/script/firmware/
acx-20080210/script/firmware/Makefile
acx-20080210/script/firmware/extract.c
acx-20080210/script/iwc.sh
acx-20080210/script/acx100_indent.sh
acx-20080210/script/rename
acx-20080210/script/kernel_help
acx-20080210/script/fix_ws.sh
acx-20080210/script/find_ifs.sh
acx-20080210/script/crashme2.sh
acx-20080210/script/stop_net.sh
acx-20080210/script/fetch_firmware.sh
acx-20080210/acx_struct.h
acx-20080210/wlan.c
acx-20080210/Changelog
acx-20080210/ioctl.c
user335@user335:~/WLAN-driver-files/acx$ patch -p0 < acx_karmic.patch
patching file acx-20080210/ioctl.c
patching file acx-20080210/pci.c
patching file acx-20080210/usb.c
patching file acx-20080210/wlan_compat.h
user335@user335:~/WLAN-driver-files/acx$ cd acx-20080210/
user335@user335:~/WLAN-driver-files/acx/acx-20080210$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-3.13.0-46-generic'
  LD      /home/user335/WLAN-driver-files/acx/acx-20080210/built-in.o
  CC [M]  /home/user335/WLAN-driver-files/acx/acx-20080210/wlan.o
In file included from /home/user335/WLAN-driver-files/acx/acx-20080210/acx.h:6:0,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/wlan.c:49:
/home/user335/WLAN-driver-files/acx/acx-20080210/acx_func.h:109:0: warning: "printk_ratelimited" redefined [enabled by default]
 #define printk_ratelimited(args...) printk(args)
 ^
In file included from include/linux/kernel.h:13:0,
                 from include/linux/skbuff.h:17,
                 from include/linux/if_arp.h:26,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/wlan.c:45:
include/linux/printk.h:309:0: note: this is the location of the previous definition
 #define printk_ratelimited(fmt, ...)     \
 ^
  CC [M]  /home/user335/WLAN-driver-files/acx/acx-20080210/conv.o
In file included from /home/user335/WLAN-driver-files/acx/acx-20080210/acx.h:6:0,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/conv.c:43:
/home/user335/WLAN-driver-files/acx/acx-20080210/acx_func.h:109:0: warning: "printk_ratelimited" redefined [enabled by default]
 #define printk_ratelimited(args...) printk(args)
 ^
In file included from include/linux/kernel.h:13:0,
                 from include/linux/skbuff.h:17,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/conv.c:37:
include/linux/printk.h:309:0: note: this is the location of the previous definition
 #define printk_ratelimited(fmt, ...)     \
 ^
  CC [M]  /home/user335/WLAN-driver-files/acx/acx-20080210/ioctl.o
In file included from /home/user335/WLAN-driver-files/acx/acx-20080210/acx.h:6:0,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/ioctl.c:45:
/home/user335/WLAN-driver-files/acx/acx-20080210/acx_func.h:109:0: warning: "printk_ratelimited" redefined [enabled by default]
 #define printk_ratelimited(args...) printk(args)
 ^
In file included from include/linux/kernel.h:13:0,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/ioctl.c:37:
include/linux/printk.h:309:0: note: this is the location of the previous definition
 #define printk_ratelimited(fmt, ...)     \
 ^
  CC [M]  /home/user335/WLAN-driver-files/acx/acx-20080210/common.o
In file included from /home/user335/WLAN-driver-files/acx/acx-20080210/acx.h:6:0,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/common.c:53:
/home/user335/WLAN-driver-files/acx/acx-20080210/acx_func.h:109:0: warning: "printk_ratelimited" redefined [enabled by default]
 #define printk_ratelimited(args...) printk(args)
 ^
In file included from include/linux/kernel.h:13:0,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:4,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/user335/WLAN-driver-files/acx/acx-20080210/common.c:37:
include/linux/printk.h:309:0: note: this is the location of the previous definition
 #define printk_ratelimited(fmt, ...)     \
 ^
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1705:1: error: unknown type name &#8216;read_proc_t&#8217;
 static read_proc_t * const
 ^
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1707:2: warning: initialization from incompatible pointer type [enabled by default]
  acx_e_read_proc,
  ^
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1707:2: warning: (near initialization for &#8216;proc_funcs[0]&#8217;) [enabled by default]
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1708:2: warning: initialization from incompatible pointer type [enabled by default]
  acx_e_read_proc_diag,
  ^
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1708:2: warning: (near initialization for &#8216;proc_funcs[1]&#8217;) [enabled by default]
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1709:2: warning: initialization from incompatible pointer type [enabled by default]
  acx_e_read_proc_eeprom,
  ^
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1709:2: warning: (near initialization for &#8216;proc_funcs[2]&#8217;) [enabled by default]
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1711:1: warning: initialization from incompatible pointer type [enabled by default]
 };
 ^
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1711:1: warning: (near initialization for &#8216;proc_funcs[3]&#8217;) [enabled by default]
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c: In function &#8216;manage_proc_entries&#8217;:
/home/user335/WLAN-driver-files/acx/acx-20080210/common.c:1726:4: error: implicit declaration of function &#8216;create_proc_read_entry&#8217; [-Werror=implicit-function-declaration]
    if (!create_proc_read_entry(procbuf, 0, 0, proc_funcs[i], adev)) {
    ^
cc1: some warnings being treated as errors
make[1]: *** [/home/user335/WLAN-driver-files/acx/acx-20080210/common.o] Error 1
make: *** [_module_/home/user335/WLAN-driver-files/acx/acx-20080210] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-46-generic'
user335@user335:~/WLAN-driver-files/acx/acx-20080210$ 


[SIZE=1]
```


Another straw is that there is a TNET1130 driver from Texas instruments that can be loaded into ndiswrapper and makes work ACX110 Wireless cards. I confirmed that ndiswrapper accepts this, but as I have an ACX100 card I need the TNET1100 driver, which I cannot find.

Here is the wireless-info.txt from the wireless script, just in case more info is needed:
[/SIZE]```


########## wireless info START ##########


Report from: 28 Feb 2015 15:43 CET +0100


Booted last: 28 Feb 2015 15:37 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, video=LCDS-1:d, vt.handoff=7


##### desktop ###########################


LXDE


##### lspci #############################


02:08.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]
    Subsystem: D-Link System Inc DWL-520+ 22Mbps PCI Wireless Adapter [1186:3b01]


02:0c.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 10)
    Subsystem: Dell Device [1028:0145]
    Kernel driver in use: e100


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 192f:0916 Avago Technologies, Pte. 
Bus 006 Device 002: ID 045e:0768 Microsoft Corp. Sidewinder X4
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fee3:5012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:761668 (761.6 KB)  TX bytes:109767 (109.7 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             8.8.8.8


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
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp


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


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v0000104Cd00009066sv00003B04sd00001186bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv00003B05sd00001186bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv00009067sd0000104Cbc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv0000AB80sd000013D1bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv0000AB81sd000013D1bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv0000AB90sd000013D1bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv0000AB91sd000013D1bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv0000ABA0sd000013D1bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv0000ABA1sd000013D1bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000104Cd00009066sv*sd*bc*sc*i* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1229 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############

```

---

### Post by RaphaalBar on 2015-03-02
Bump.
Any help from an experienced user, pretty please ? :-)

---

### Post by RaphaalBar on 2015-03-02
I added my commands and output when trying to compile the driver.. I used instructions written for karmic ([http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520](http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520)), so maybe something can be improved there.

---

