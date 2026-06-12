---
title: "Asus. Wifi doesnt work. Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by javier35 on 2015-01-15
Hello. I have just bought an Asus X551C1-SX014 H 15.6/I3/4G/500HD/W8.1/A
In Windows, evevrything goes well, but in Ubuntu 14 I can't use Wifi.
The Wireless Network Adapter is:

Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)


I have tried to fix it following the steps that I have seen in others posts, but it doesn't work. I have even tried to install the Windows Drivers in Ubuntu using ndisgtk.

Thak you for your help!

---

### Post by slickymaster on 2015-01-15
Hello and welcome to the forums javier35

Please have a look at this ["sticky" thread]("http://ubuntuforums.org/showthread.php?t=370108"), in particular the instructions for downloading and running the wireless info script

Once you collect and post that info one of the networking experts will likely be able to get you up and running.

---

### Post by javier35 on 2015-01-15
Thanks. In the file wireless-info.txt I obtain the next useful information:



```
########## wireless info START ##########


Report from: 15 Jan 2015 12:42 CET +0100


Booted last: 15 Jan 2015 12:39 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: AzureWave Device [1a3b:2130]


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5286] (rev 01)


03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
------------------------------------------------------------------------------------
```

I think the rest of information is not important

---

### Post by slickymaster on 2015-01-15
javier35, I edited your last post, adding [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to it.

Please use code tags when posting code, because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand and. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by jeremy31 on 2015-01-15
For some reason the driver isn't loading ```
sudo modprobe -v ath9k
``` and post any errors

---

### Post by javier35 on 2015-01-15
Thank you! My Wifi is now working!!

---

### Post by jeremy31 on 2015-01-15
> **javier35 said:**
> Thank you! My Wifi is now working!!
posting the rest of the info should tell us why that module isn't loading on its own

---

### Post by javier35 on 2015-01-15
I only wrote:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v ath9k[/FONT][/COLOR]
```

and it worked.

Now the problem is that when I reboot my computer, I can't use the Wifi if I don't write the same code. 

It only load the driver when I write [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v ath9k , and when I reboot, it doesn't load the drivers automatically[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-01-15
I suspect you have blacklisted ath9k somehow and the full wireless-info.txt should show how it was blacklisted

---

### Post by javier35 on 2015-01-15
Thanks! I better copy the whole wireless-info.txt file, because I don't know how to fix it:

```


########## wireless info START ##########


Report from: 15 Jan 2015 12:42 CET +0100


Booted last: 15 Jan 2015 12:39 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: AzureWave Device [1a3b:2130]


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5286] (rev 01)


03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 13d3:3408 IMC Networks 
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


ndiswrapper           283985  0 
asus_wmi               24191  0 
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::7a24:afff:fee1:dbba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3669856 (3.6 MB)  TX bytes:471339 (471.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Conexión cableada 1] -----------------------------------------
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
    Address:         192.168.2.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


Region: Europe/Madrid (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/3.13.0-44-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=4


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v0000168Cd00000013sv00000017sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000017sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000017sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000025sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000025sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000025sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001731bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001731bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001731bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000036sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000036sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000036sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000406sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000406sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000406sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000407sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000407sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000407sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000408sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000408sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000408sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000417sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000417sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000417sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001012sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001012sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001012sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001203sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001203sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001203sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001204sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001204sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001204sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001234sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001234sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001234sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001235sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001235sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001235sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001236sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001236sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001236sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003070sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003070sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003070sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003202sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003202sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003202sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003203sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003203sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003203sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A07sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A07sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A07sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A12sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A12sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A12sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A13sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A13sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A13sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A14sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A14sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A14sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A17sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A17sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A17sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A18sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A18sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A18sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A63sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A63sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A63sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A73sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A73sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A73sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A74sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A74sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A74sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004610sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004610sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004610sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004F00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004F00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004F00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005A00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005A00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005A00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005E00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005E00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005E00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007064sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007064sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007064sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007065sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007065sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007065sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007084sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007084sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007084sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007088sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007088sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007088sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000A527sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000A527sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000A527sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E801sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E801sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E801sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E811sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E811sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E811sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E814sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E814sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E814sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E911sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E911sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E911sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E912sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E912sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E912sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000053sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000053sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000053sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000418sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000418sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000418sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000420sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000420sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000420sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000426sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000426sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000426sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003071sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003071sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003071sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A15sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A15sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A15sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A16sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A16sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A16sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A23sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A23sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A23sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A24sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A24sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A24sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000700Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000700Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000700Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000701Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000701Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000701Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007094sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007094sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007094sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007101sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007101sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007101sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007114sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007114sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007114sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007115sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007115sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007115sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000043sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000043sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000043sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000044sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000044sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000044sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001329sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001329sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001329sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000134Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000134Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000134Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001602sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001602sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001602sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001603sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001603sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001603sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A19sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A19sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A19sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A22sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A22sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A22sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005000sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005000sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005000sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005001sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005001sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005001sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005301sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005301sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005301sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005401sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005401sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005401sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00007092sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00007092sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00007092sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000034sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000034sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000034sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000035sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000035sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000035sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000100sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000100sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000100sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000112sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000112sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000112sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000200sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000200sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000200sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000202sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000202sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000202sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B0sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B0sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B0sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B1sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B1sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B1sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002D6sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002D6sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002D6sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000422sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000422sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000422sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000425sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000425sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000425sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000427sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000427sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000427sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000428sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000428sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000428sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000042Asd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000042Asd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000042Asd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001020sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001020sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001020sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001025sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001025sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001025sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001026sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001026sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001026sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001033sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001033sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001033sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001034sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001034sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001034sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001060sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001060sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001060sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001385sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001385sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001385sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001386sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001386sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001386sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000139Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000139Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000139Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000142Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000142Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000142Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001604sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001604sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001604sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002A97sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002A97sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002A97sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003064sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003064sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003064sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003067sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003067sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003067sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003164sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003164sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003164sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00004105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00004105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00004105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006303sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006303sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006303sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006313sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006313sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006313sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006323sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006323sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006323sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006333sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006333sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006333sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006353sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006353sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006353sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007096sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007096sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007096sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007106sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007106sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007106sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007108sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007108sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007108sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007111sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007111sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007111sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007112sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007112sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007112sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007116sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007116sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007116sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007128sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007128sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007128sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007130sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007130sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007130sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007131sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007131sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007131sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007519sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007519sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007519sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000A601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000A601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000A601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000C601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000C601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000C601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E000sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E000sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E000sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E002sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E002sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E002sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E008sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E008sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E008sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Bsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Bsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Bsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E913sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E913sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E913sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E917sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E917sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E917sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E918sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E918sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E918sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00001055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00001055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00001055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00002055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00002055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00002055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000720Bsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000720Bsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000720Bsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000B203sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000B203sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000B203sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000147Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000147Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000147Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A09sd000007D1bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A09sd000007D1bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A09sd000007D1bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A69sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A69sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A69sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A76sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A76sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A76sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008001sd000018CBbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008001sd000018CBbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008001sd000018CBbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008011sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008011sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008011sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000E914sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000E914sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000E914sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000032sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000032sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000032sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000033sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000033sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000033sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000384sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000384sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000384sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000429sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000429sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000429sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000430sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000430sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000430sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000502sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000502sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000502sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001022sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001022sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001022sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001024sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001024sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001024sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001026sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001026sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001026sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv000013C0sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv000013C0sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv000013C0sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002072sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002072sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002072sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002A5Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002A5Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002A5Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A6Fsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A6Fsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A6Fsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A70sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A70sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A70sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007122sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007122sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007122sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007125sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007125sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007125sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007132sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007132sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007132sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00009000sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00009000sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00009000sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E815sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E815sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E815sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E915sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E915sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E915sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E916sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E916sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E916sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A78sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A78sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A78sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A79sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A79sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A79sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00009223sd00001ACEbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00009223sd00001ACEbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00009223sd00001ACEbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv0000D05Bsd000010FCbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv0000D05Bsd000010FCbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv0000D05Bsd000010FCbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000034sd00001B0Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000034sd00001B0Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000034sd00001B0Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000036sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000036sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000036sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000008Fsd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000008Fsd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000008Fsd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000504sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000504sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000504sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001000sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001000sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001000sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001001sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001001sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001001sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001067sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001067sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001067sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001071sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001071sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001071sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001081sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001081sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001081sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001090sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001090sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001090sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001130sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001130sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001130sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001381sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001381sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001381sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001382sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001382sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001382sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Dsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Dsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Dsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001536sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001536sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001536sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001A67sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001A67sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001A67sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001C71sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001C71sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001C71sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00002000sd00001071bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00002000sd00001071bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00002000sd00001071bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003041sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003041sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003041sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003042sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003042sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003042sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003095sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003095sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003095sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003097sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003097sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003097sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Asd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Asd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Asd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv000030A3sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv000030A3sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv000030A3sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006502sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006502sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006502sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006512sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006512sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006512sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006522sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006522sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006522sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006532sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006532sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006532sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006542sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006542sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006542sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006552sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006552sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006552sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006600sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006600sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006600sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006610sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006610sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006610sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006620sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006620sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006620sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007136sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007136sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007136sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007137sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007137sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007137sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007138sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007138sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007138sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007139sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007139sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007139sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007140sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007140sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007140sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007141sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007141sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007141sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007154sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007154sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007154sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007156sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007156sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007156sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007157sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007157sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007157sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007158sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007158sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007158sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007161sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007161sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007161sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007163sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007163sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007163sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007168sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007168sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007168sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000A822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000A822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000A822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000B822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000B822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000B822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C823sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C823sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C823sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E004sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E004sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E004sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E006sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E006sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E006sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E007sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E007sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E007sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E009sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E009sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E009sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E00Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E00Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E00Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E010sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E010sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E010sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E012sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E012sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E012sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E013sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E013sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E013sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E015sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E015sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E015sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E019sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E019sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E019sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E01Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E01Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E01Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E919sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E919sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E919sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000F822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000F822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000F822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000023sd00001931bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000023sd00001931bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000023sd00001931bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000037sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000037sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000037sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000204sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000204sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000204sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000205sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000205sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000205sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000403sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000403sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000410sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000410sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000410sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000411sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000411sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000411sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000464sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000464sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000464sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C02sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C02sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C02sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C05sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C05sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C05sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C10sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C10sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C10sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C11sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C11sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C11sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001000sd00001B14bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001000sd00001B14bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001000sd00001B14bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001089sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001089sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001089sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001106sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001106sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001106sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001461sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001461sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001461sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001537sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001537sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001537sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001619sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001619sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001619sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001A89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001A89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001A89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001D89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001D89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001D89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002036sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002036sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002036sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002300sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002300sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002300sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002A37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002A37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002A37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002C37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002C37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002C37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A2sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A2sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A2sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ADsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ADsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ADsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030B2sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030B2sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030B2sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000031A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000031A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000031A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003B00sd00001106bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003B00sd00001106bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003B00sd00001106bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004101sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004101sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004101sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004102sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004102sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004102sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004103sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004103sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004103sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004104sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004104sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004104sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004114sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004114sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004114sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006623sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006623sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006623sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007159sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007159sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007159sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007164sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007164sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007164sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007167sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007167sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007167sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007173sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007173sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007173sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007178sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007178sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007178sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007182sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007182sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007182sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007183sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007183sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007183sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007187sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007187sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007187sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007194sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007194sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007194sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00008305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00008305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00008305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00009811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00009811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00009811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A011sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A011sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A011sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A500sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A500sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A500sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A501sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A501sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A501sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A502sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A502sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A502sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A831sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A831sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A831sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000BA91sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000BA91sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000BA91sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000D811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000D811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000D811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E014sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E014sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E014sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E016sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E016sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E016sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E017sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E017sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E017sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E01Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E01Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E01Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E022sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E022sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E022sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E023sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E023sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E023sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E025sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E025sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E025sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E031sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E031sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E031sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E032sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E032sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E032sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E033sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E033sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E033sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E035sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E035sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E035sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E036sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E036sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E036sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E037sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E037sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E037sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E03Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E03Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E03Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E048sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E048sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E048sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E049sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E049sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E049sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E070sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E070sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E070sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000EE32sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000EE32sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000EE32sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000F611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000F611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000F611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001112sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001112sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001112sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001A12sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001A12sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001A12sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv000030A7sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv000030A7sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv000030A7sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv0000E029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv0000E029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv0000E029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000300sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000300sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000300sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000301sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000301sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000301sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00002099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00002099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00002099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001121sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001121sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001121sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001462sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001462sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001462sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000158Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000158Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000158Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001626sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001626sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001626sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001A21sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001A21sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001A21sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00002309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00002309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00002309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B0sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B0sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B0sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B3sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B3sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B3sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B4sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B4sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B4sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000031A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000031A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000031A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00004309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00004309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00004309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00007189sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00007189sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00007189sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E030sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E030sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E030sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E034sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E034sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E034sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000009Asd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000009Asd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000009Asd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00000508sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00000508sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00000508sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001173sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001173sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001173sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001627sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001627sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001627sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001628sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001628sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001628sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv000016A8sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv000016A8sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv000016A8sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002000sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002000sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002000sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002001sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002001sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002001sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003112sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003112sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003112sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003113sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003113sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003113sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003114sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003114sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003114sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003116sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003116sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003116sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003A7Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003A7Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003A7Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003ABEsd00001948bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003ABEsd00001948bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003ABEsd00001948bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004107sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004107sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004107sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004108sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004108sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004108sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004109sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004109sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004109sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006503sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006503sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006503sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006513sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006513sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006513sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006523sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006523sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006523sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00007188sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00007188sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00007188sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000E04Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000E04Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000E04Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001186sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001186sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001186sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000118Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000118Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000118Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001237sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001237sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001237sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000126Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000126Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000126Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001785sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001785sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001785sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000179Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000179Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000179Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001838sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001838sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001838sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000191Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000191Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000191Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F86sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F86sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F86sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002000sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002000sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002000sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002001sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002001sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002001sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002086sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002086sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002086sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002097sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002097sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002097sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000209Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000209Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000209Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002126sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002126sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002126sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002152sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002152sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002152sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002187sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002187sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002187sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002B87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002B87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002B87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002C97sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002C97sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002C97sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002F87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002F87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002F87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003122sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003122sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003122sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000312Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000312Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000312Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003218sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003218sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003218sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003219sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003219sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003219sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004001sd00001C56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004001sd00001C56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004001sd00001C56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004105sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004105sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004105sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004106sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004106sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004106sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004115sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004115sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004115sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004116sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004116sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004116sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004117sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004117sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004117sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004318sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004318sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004318sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006608sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006608sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006608sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006627sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006627sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006627sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006628sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006628sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006628sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006647sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006647sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006647sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006657sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006657sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006657sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007192sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007192sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007192sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007193sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007193sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007193sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007197sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007197sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007197sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000850Dsd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000850Dsd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000850Dsd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000A118sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000A118sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000A118sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C680sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C680sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C680sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C706sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C706sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C706sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C708sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C708sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C708sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E044sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E044sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E044sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E047sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E047sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E047sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E051sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E051sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E051sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E062sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E062sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E062sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E063sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E063sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E063sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E075sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E075sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E075sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E080sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E080sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E080sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000F842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000F842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000F842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000033sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000033sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000033sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000063sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000063sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000063sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000064sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000064sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000064sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000081sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000081sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000081sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000088sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000088sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000088sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000091sd00001969bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000091sd00001969bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000091sd00001969bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000802sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000802sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000802sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000812sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000812sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000812sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000822sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000822sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000822sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000862sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000862sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000862sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001783sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001783sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001783sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000180Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000180Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000180Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001864sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001864sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001864sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv000018CDsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv000018CDsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002003sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002003sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002003sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002110sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002110sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002110sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002116sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002116sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002116sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Dsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Esd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Esd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Esd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002185sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002185sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002185sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002208sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002208sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002F85sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002F85sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002F85sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003114sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003114sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003114sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000104Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000104Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000104Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003214sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003214sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003214sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004110sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004110sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004110sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004111sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004111sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004111sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004112sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004112sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004112sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004113sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004113sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004113sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000411Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000411Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000411Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004120sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004120sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004120sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00007055sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00007055sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00007055sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000802Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000802Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000802Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000812Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000812Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000812Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000850Esd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000850Esd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000850Esd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E6sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E6sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E6sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E8sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E8sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E8sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0F9sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0F9sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0F9sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E052sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E052sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E052sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E058sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E058sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E058sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E059sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E059sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E059sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E064sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E064sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E064sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E07Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E07Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E07Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E085sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E085sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E085sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E086sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E086sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E086sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E087sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E087sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E087sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E08Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E08Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E08Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000652sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000652sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000652sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000662sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000662sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000662sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000672sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000672sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000672sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000682sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000682sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000682sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000692sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000692sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000692sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006A2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006A2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006A2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006B2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006B2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006B2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000803sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000813sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000018E3sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000018E3sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000018E3sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002005sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002005sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002005sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002130sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002130sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002130sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002176sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002176sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002176sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000217Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000217Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000217Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002182sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002182sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002182sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002810sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002810sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002810sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002811sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002811sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002811sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002812sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002812sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002812sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002813sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002813sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A1sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A1sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A1sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A2sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A2sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A2sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A3sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A3sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A3sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A4sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A4sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A4sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F82sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F82sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F82sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F8Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F8Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F8Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004129sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004129sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000412Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000412Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00007202sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00007202sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00007202sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000085F2sd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000085F2sd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000085F2sd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A120sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A120sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A120sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E068sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E068sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E068sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E069sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E069sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E069sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E07Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E07Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E07Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E081sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E08Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E091sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000057Esd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000057Esd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000057Esd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv00000589sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv00000589sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv00000589sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000058Asd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000058Asd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000058Asd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv00000000sd00000000bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv00000000sd00000000bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv00000000sd00000000bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FE30sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FE30sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FE30sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FF19sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FF19sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FF19sv*sd*bc*sc*i* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   17.886535] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   17.887516] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-01-15
Looks like ndiswrapper is the problem```
ndiswrapper -l
``` and paste the output

---

### Post by javier35 on 2015-01-15
Thanks. I don't obtain anything when I write [COLOR=#000000][FONT=Ubuntu Mono]ndiswrapper -l in the console.

When I write ndiswrapper only, I obtain the help:

```
[/FONT][/COLOR]javier@javier-X551CA:~$ ndiswrapper -ljavier@javier-X551CA:~$ sudo su
[sudo] password for javier: 
root@javier-X551CA:/home/javier# ndiswrapper -l
root@javier-X551CA:/home/javier# ndiswrapper
install/manage Windows drivers for ndiswrapper


usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card


[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-01-15
Did you use terminal to load ndiswrapper or did you use windows wireless or whatever the graphical program is called now?

---

### Post by javier35 on 2015-01-15
I am using the terminal in Ubuntu 14, I am not using Windows.

---

### Post by jeremy31 on 2015-01-15
Lets see ```
history | grep ndiswrapper
```

---

### Post by javier35 on 2015-01-15
I obtain:

```
javier@javier-X551CA:~$ history | grep ndiswrapper   89  ndiswrapper -l
   90  ndiswrapper
   91  ndiswrapper -l
   92  ndiswrapper-l
   93  ndiswrapper -l
   95  ndiswrapper -l
   97  ndiswrapper -l
   98  ndiswrapper
   99  ndiswrapper -l
  100  history | grep ndiswrapper



```

---

