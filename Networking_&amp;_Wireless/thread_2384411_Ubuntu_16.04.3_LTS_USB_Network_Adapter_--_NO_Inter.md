---
title: "Ubuntu 16.04.3 LTS USB Network Adapter -- NO Internet Access"
date: 2018-02-06
forum: Networking &amp; Wireless
---

### Post by papazig on 2018-02-06
Hello all,

I am new to Unbutu. I just wiped my entire Windows 7 system and installed Unbutu 16.04.3. I really enjoy it and I'm comfortable using a terminal for I am required to use one in my c++ programming class(based on UNIX). The only thing that is causing me to pull my hair out is that I am unable to get the Wifi working. I have no other means of connecting to the internet besides through my USB wireless adapter (DYNEX Wirless N: DX-NUSB -- its old but works on other systems). I have the driver for this device but it is an .exe used with Windows, so to my understanding, it will not work with Ubuntu. I have read countless forums and through everything I tried, nothing has worked. 

When I enter ```
lsusb
``` the line pertaining to my device is:
```
Bus 002 Device 003: ID 050d:d321 Belkin Components Dynex DX-NUSB 802.11bgn Wirless Adapter [Broadcom BCM43231]
```

Here is the result of running the Wireless Info Program:
```


########## wireless info START ##########


Report from: 06 Feb 2018 18:38 EST -0500


Booted last: 06 Feb 2018 00:00 EST -0500


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:8505]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 050d:d321 Belkin Components Dynex DX-NUSB 802.11bgn Wireless Adapter [Broadcom BCM43231]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 1908:1320 GEMBIRD PhotoFrame PF-15-1
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 0781:556b SanDisk Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 194f:0301 PreSonus Audio Electronics, Inc. AudioBox
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  1 nouveau
video                  40960  3 asus_wmi,nouveau,i915
wmi                    16384  3 asus_wmi,mxm_wmi,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:383328 (383.3 KB)  TX bytes:383328 (383.3 KB)


##### iwconfig ##########################


enp3s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1050     1  0 18:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (P8 series motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WIFI]] (600 root)
[connection] id=WIFI | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=ZIGNET
[ipv4] method=shared
[ipv6] method=ignore


##### Netplan config ####################


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp3s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp3s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


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


##### dmesg #############################


[   31.540490] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   32.513400] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   32.619007] r8169 0000:03:00.0 enp3s0: link down
[   32.619053] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready


########## wireless info END ############

```

I hope we can get this to work because I really dont want to move to windows 10.

Cheers.

---

### Post by vasa1 on 2018-02-06
Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) thoroughly and provide the required information. Thanks!

---

### Post by chili555 on 2018-02-12
> Bus 002 Device 003: ID [COLOR="#FF0000"]050d:d321[/COLOR] Belkin Components Dynex DX-NUSB 802.11bgn Wirless Adapter [Broadcom BCM43231]I am afraid that I haven't any good news. When I search for the usb.id, I see exactly two relevant hits; this exact thread and this: [https://wikidevi.com/wiki/Dynex_DX-NUSB](https://wikidevi.com/wiki/Dynex_DX-NUSB)> Probable Linux driver
*none*, will not be supported by brcmfmac
USB ID not yet observed in any mainline kernel / Now we could try ndiswrapper but Windows XP .inf and .sys files are required. Do you have them or can you find them? Windows 7, 8, 8 1/2, 8.342286 or Windows 10 files will not work.

I haven't seen ndiswrapper work successfully in any recent Linux kernel and certainly not in the last couple of years.

---

### Post by jeremy31 on 2018-02-12
Could you buy a TP Link WN722N, 150 Mbps?  There are a couple versions, version 1 is plug and play in Ubuntu and version 2 might need a bit of help depending on the kernel used

---

