---
title: "Disabled wireless ubuntu 14.04 HP Pavilion RALINK 539a"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by smichaele on 2015-12-04
I've been using Ubuntu 14.04 now for about 6 months after finally getting tired of all of the issues I had with software development under Win 7. I'm really pleased with my new OS and setup except for one thing - I haven't been able to get my wireless working. I've followed so many threads and tried so many different solutions that it seems like I'll never get it to work. I started out at the Ubuntu Wireless Troubleshooting Guide so I've posted some output from there below. The wireless indicator on my keyboard constantly shows that it's off no matter what I do - it worked fine under Win 7 though. If anyone can help I'd certainly appreciate it. Thanks in advance for any help you can offer.

Steve

```

HP-Pavilion-dv7-Notebook-PC:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        08:ED:B9:1A:B3:4A


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        08:2E:5F:72:C7:F0


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             167.206.245.135
    DNS:             167.206.245.136
    DNS:             192.168.1.1


  IPv6 Settings:
    Address:         2002:4357:2ff7:0:78f4:f54:a53e:9b95
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe5b:ab4


    Address:         2002:4357:2ff7:0:a2e:5fff:fe72:c7f0
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe5b:ab4


    Address:         fe80::a2e:5fff:fe72:c7f0
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe5b:ab4


HP-Pavilion-dv7-Notebook-PC:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 08:ed:b9:1a:b3:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.19.0-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:c2500000-c250ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: 08:2e:5f:72:c7:f0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:2000(size=256) memory:c2404000-c2404fff memory:c2400000-c2403fff

```

---

### Post by SlidingHorn on 2015-12-04
What happens when you input: 

```
sudo ifconfig wlan0 up
```

---

### Post by deadflowr on 2015-12-04
Moved to the Networking and Wireless subforum

---

### Post by Geoffrey_Arndt on 2015-12-05
Rather than spend more time trying to fix your wireless using the existing chipset . . . I recommend purchasing an inexpensive - tested - compatible usb wireless adaptor.   I have a collection of over two dozen various adaptors, all of which work in Ubuntu, but I've done a lot of research up front from multiple sources, including talking to the techs at the distributor in California.  

So, "Panda provides" several of these, and they work very well (just plug & play) . . . no driver installs or compiles to mess with:

Prices vary from about $5.99 (used) to $19.99.    Well worth the small expense in my view - - plus, you're then supporting hardware manufacturers and/or distributors that provide out-of-the-box linux compatibility.   Something that these forums could improve on (imho).

[http://www.amazon.com/s/ref=nb_sb_ss_c_0_14?url=search-alias%3Dcomputers&field-keywords=panda+wireless&sprefix=panda+wireless%2Caps%2C152](http://www.amazon.com/s/ref=nb_sb_ss_c_0_14?url=search-alias%3Dcomputers&field-keywords=panda+wireless&sprefix=panda+wireless%2Caps%2C152)

---

### Post by Hadaka on 2015-12-05
Hi, your wireless is indeed..not working
```
HP-Pavilion-dv7-Notebook-PC:~$ sudo lshw -C network
  *-network DISABLED
```
please do..
```
sudo modprobe -rf rt2800pci
sudo modprobe -v rt2800pci
sudo rfkill unblock all
```
next disconnect the wired connection and then click the wifi icon
inspect to see if enable Wireless is checked.
if you still dont have wireless go here..
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
follow directions and post the wireless-info.txt file
thanks.

---

### Post by dellboy56 on 2015-12-05
What wifi adapter you got Intel Broadcom?

---

### Post by smichaele on 2015-12-09
> **SlidingHorn said:**
> What happens when you input: 

```
sudo ifconfig wlan0 up
```

I get: SIOCSIFFLAGS: Operation not possible due to RF-kill

---

### Post by smichaele on 2015-12-09
> **Hadaka said:**
> Hi, your wireless is indeed..not working
```
HP-Pavilion-dv7-Notebook-PC:~$ sudo lshw -C network
  *-network DISABLED
```
please do..
```
sudo modprobe -rf rt2800pci
sudo modprobe -v rt2800pci
sudo rfkill unblock all
```
next disconnect the wired connection and then click the wifi icon
inspect to see if enable Wireless is checked.
if you still dont have wireless go here..
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
follow directions and post the wireless-info.txt file
thanks.

Ran the script. I know it says that the wireless is hard blocked and the indicator on my keyboard tells me the same thing but I apparently have no way to turn it on. There is nothing in the BIOS that allows for that and key combinations to try to change it are useless. The output is below. Any help would be greatly appreciated. Thanks.

```



########## wireless info START ##########


Report from: 09 Dec 2015 22:34 EST -0500


Booted last: 09 Dec 2015 22:24 EST -0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:00:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]
	Subsystem: Hewlett-Packard Company Device [103c:1839]
	Kernel driver in use: rt2800pci


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:1818]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 064e:c334 Suyin Corp. 
Bus 003 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 0461:4d75 Primax Electronics, Ltd Rocketfish RF-FLBTAD Bluetooth Adapter
Bus 001 Device 008: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 007: ID 03f0:6b11 Hewlett-Packard Photosmart C4500 series
Bus 001 Device 011: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 009: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c527 Logitech, Inc. 
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### lsmod #############################


hp_wmi                 16384  0 
rt2800pci              16384  0 
sparse_keymap          16384  1 hp_wmi
rt2800mmio             24576  1 rt2800pci
rt2800lib              90112  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              708608  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              524288  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4357:2ff7:0:4978:575c:947b:408b/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2002:4357:2ff7:0:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1960984 (1.9 MB)  TX bytes:782270 (782.2 KB)


virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


virbr0    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       959     1  0 22:24 ?        00:00:00 NetworkManager


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
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             167.206.245.135
    DNS:             167.206.245.136
    DNS:             192.168.1.1


  IPv6 Settings:
    Address:         2002:4357:2ff7:0:4978:575c:947b:408b
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe5b:ab4


    Address:         2002:4357:2ff7:0:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe5b:ab4


    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe5b:ab4


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


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


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


virbr0    no frequency information.


lo        no frequency information.


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


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


virbr0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C7768FC9D600016BB9062C
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EA7A45E50305BDF0A76BD50
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512


[rt2x00pci]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512


[rt2x00mmio]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci  nohwcrypt=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x539a (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   15.657452] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   15.661717] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   26.049958] r8169 0000:05:00.0 eth0: link down (repeated 2 times)
[   26.050019] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.065349] r8169 0000:05:00.0 eth0: link up
[   44.065359] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############

```

---

### Post by smichaele on 2015-12-09
Thanks for the advice Geoffrey_Arndt but I haven't given up yet (I may get there though)!

---

### Post by Hadaka on 2015-12-10
Hi, this....
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```
Is a key combo or a physical switch..usually
what is the exact model and make of your computer??
mean time,power off, remove the battery an let it sit
for a couple minutes,replace the battery and try the key
combo. also try,,{FUNCTION/F12}  {F12}  {ALT/F12}
```
sudo modprobe -r hp-wmi
sudo modprobe hp-wmi
rfkill unblock all
```
then to see if cleared'
```
rfkill list all
```

---

### Post by smichaele on 2015-12-28
Thanks for your help Hadaka but no luck. Mine is an HP dv7-7025dx. The F12 key should toggle the wireless but it doesn't and neither does any other key combination. The wireless LAN still shows as hard blocked. Unless there's another driver for the Ralink that I can use I think I'm out of luck. Have a great New Year!

Steve

---

