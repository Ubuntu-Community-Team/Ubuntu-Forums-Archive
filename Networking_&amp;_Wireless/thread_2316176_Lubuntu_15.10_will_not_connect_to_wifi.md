---
title: "Lubuntu 15.10 will not connect to wifi"
date: 2016-03-05
forum: Networking &amp; Wireless
---

### Post by Bunny Boy on 2016-03-05
Running Lubuntu 15.10 on a Dell Latitude D610.  Network card worked fine in earlier Kubuntu but will not autoconnect now in Lubuntu.

03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64
Interrupt: pin A routed to IRQ 17
Region 0: Memory at dfcfe000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge

I can't find any kind of control in Lubuntu that manually connects the wifi.  Also, Fn+F2 does nothing (the wifi light does not come on)

Any ideas?

---

### Post by chili555 on 2016-03-05
Please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Bunny Boy on 2016-03-05
> **chili555 said:**
> Please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

Well, I'm not sure why it would be a driver issue.  I followed the directions in that link and reinstalled the driver, but my "Network Connections" applet still doesn't present any means of actually connecting.  (it just has the options to add, edit, or delete connections)

So how do I tell this OS to actually connect via wifi?

BTW Fn+F2 still does nothing.  Is this a hardware problem?

---

### Post by jeremy31 on 2016-03-05
Might as well run the wireless script
```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]chmod +x wireless-info && ./wireless-info
```

And paste the contents of the wireless-info.txt file using code tags[/FONT][/COLOR]

---

### Post by Bunny Boy on 2016-03-05
> **jeremy31 said:**
> Might as well run the wireless script
```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]chmod +x wireless-info && ./wireless-info
```

And paste the contents of the wireless-info.txt file using code tags[/FONT][/COLOR]

```


########## wireless info START ##########

Report from: 05 Mar 2016 19:13 CST -0600

Booted last: 05 Mar 2016 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:57:19 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Latitude D610 [1028:0182]
	Kernel driver in use: tg3

03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
	Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

##### lsmod #############################

b43                   401408  0
dell_laptop            24576  0
bcma                   49152  1 b43
mac80211              659456  1 b43
dcdbas                 16384  1 dell_laptop
cfg80211              483328  2 b43,mac80211
ssb                    57344  1 b43
video                  24576  2 i915,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5816246 (5.8 MB)  TX bytes:1225510 (1.2 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       578     1  0 18:24 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5751 Gigabit Ethernet PCI Express (Latitude D610)
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5751-v3.29a
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       399ecf53-afc7-4e73-a096-fb70fb7da4eb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{37}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   399ecf53-afc7-4e73-a096-fb70fb7da4eb | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.106/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1457312385
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.106
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF]>/64
IP6.GATEWAY:                            

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
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/OzCAD]] (600 root)
[connection] id=OzCAD | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=OZBB_Ambulance
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     EBCFBB62711AEC753D1C919
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        25:03:26:C1:B5:8C:49:2C:31:50:BE:A3:71:10:4E:E0:C4:A8:87:C2
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        25:03:26:C1:B5:8C:49:2C:31:50:BE:A3:71:10:4E:E0:C4:A8:87:C2
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        25:03:26:C1:B5:8C:49:2C:31:50:BE:A3:71:10:4E:E0:C4:A8:87:C2
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        25:03:26:C1:B5:8C:49:2C:31:50:BE:A3:71:10:4E:E0:C4:A8:87:C2
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     B9B638C64CE9AC05F1A1903
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        25:03:26:C1:B5:8C:49:2C:31:50:BE:A3:71:10:4E:E0:C4:A8:87:C2
sig_hashalgo:   sha512

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   19.390241] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.420574] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   19.420595] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 8, Version 0
[   19.933986] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   19.934046] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   19.934067] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   19.934071] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   19.934074] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   49.781647] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[ 2164.320461] tg3 0000:02:00.0 eth0: Link is up at 100 Mbps, full duplex
[ 2164.320487] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
[ 2164.322200] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by Bunny Boy on 2016-03-05
Thanks, jeremy31, that fixed it!  (I realized after I pasted in the wireless-info.txt that it contained the answer near the bottom!)

---

### Post by chili555 on 2016-03-05
> [   19.933986] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   19.934046] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   19.934067] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   19.934071] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not foundEvidently you haven't completed the steps in my link. Please open a terminal and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Detach the ethernet, reboot and give us your report.

---

### Post by Hadaka on 2016-03-05
Hi, your wireless report shows your country code is unset you can correct with..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
The report also shows you are managing your network with NetworkManager not manually, you can correct with,..
```
sudo sed -i 's/true/false/' /etc/NetworkManager/NetworkManager.conf
```
Then please mark your thread as solved by clicking Thread Tools then choose solved.
thanks.

---

