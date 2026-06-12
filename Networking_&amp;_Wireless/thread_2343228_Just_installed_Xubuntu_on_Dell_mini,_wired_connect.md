---
title: "Just installed Xubuntu on Dell mini, wired connection works, but wireless not working"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by davecardnell on 2016-11-14
I've just installed Xubuntu on an old Dell Inspiron Mini, which I'm trying to breathe some life into, replacing Windows XP.

I'm new to Unix, I've looked at various posts but unsure what to do, so I'd be very grateful for some help.
I can get a wired connection to work, but not the wireless connection, even with the wired connection removed.

In the network manager "Enable Networking" is checked as is "Enable Mobile Broadband"
However just above these entries under "Mobile Broadband" it says "not registered"
Under "Edit Connections" I added my Wi-Fi router details, but only filled in the SSID, not sure if I was meant to fill in anything else.

This is the result of the [wireless info script]("https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info") that I found on another post



```
########## wireless info START ##########


Report from: 14 Nov 2016 16:40 GMT +0000


Booted last: 14 Nov 2016 00:00 GMT +0000


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:02f4]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 004: ID 413c:8147 Dell Computer Corp. F3507g Mobile Broadband Module
Bus 001 Device 002: ID 064e:a129 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_laptop            24576  0
b43                   401408  0
bcma                   49152  1 b43
dcdbas                 16384  1 dell_laptop
mac80211              659456  1 b43
cfg80211              499712  2 b43,mac80211
ssb                    57344  1 b43
video                  36864  3 i915,compal_laptop,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::cd62:3626:e70:8f38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:252291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:372489036 (372.4 MB)  TX bytes:8050397 (8.0 MB)


wwx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wwx<IF from MAC [IF2]>' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


wwx<IF from MAC [IF2]>  no wireless extensions.


lo        no wireless extensions.


enp4s0    no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       571     1  0 15:08 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0fe49ac4-340d-48b4-be71-c249d440c449
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0fe49ac4-340d-48b4-be71-c249d440c449 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.18/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             194.168.4.100
IP4.DNS[2]:                             194.168.8.100
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1479144451
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.18
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 194.168.4.100 194.168.8.100
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         fe80::cd62:3626:e70:8f38/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         ttyACM0
GENERAL.TYPE:                           gsm
GENERAL.NM-TYPE:                        NMDeviceModem
GENERAL.VENDOR:                         Dell
GENERAL.PRODUCT:                        Dell Wireless 5530 HSPA Mobile Broadband Minicard Device
GENERAL.DRIVER:                         cdc_acm, cdc_ether, cdc_wdm
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /org/freedesktop/ModemManager1/Modem/0
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
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


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=virginmedia1569312
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


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


wwx<IF from MAC [IF2]>  no frequency information.


lo        no frequency information.


enp4s0    no frequency information.


##### iwlist scan #######################


wwx<IF from MAC [IF2]>  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


##### module infos ######################


[b43]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa? Mi?ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 
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
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 


[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   16.577977] cdc_ether 1-5:1.7 wwan0: register 'cdc_ether' at usb-0000:00:1d.7-5, Mobile Broadband Network Device, <MAC 'wwx<IF from MAC [IF2]>' [IF2]>
[   17.253570] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   17.298567] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   17.298594] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2062, Revision 2, Version 0
[   17.463465] cdc_ether 1-5:1.7 wwx<IF from MAC [IF2]>: renamed from wwan0
[   17.566574] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2 (repeated 2 times)
[   17.566816] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2 (repeated 2 times)
[   17.570920] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   17.570928] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   17.570936] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   32.451737] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   32.461465] r8169 0000:04:00.0 enp4s0: link down (repeated 2 times)
[   32.461687] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   34.064723] r8169 0000:04:00.0 enp4s0: link up
[   34.064765] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready


########## wireless info END ############



```

---

### Post by stan26 on 2016-11-14
**How to install DELL Wireless 1397 WLAN Mini Card**
[COLOR=#000000]             Hook up an ethernet cable, then check out System->Admin->Aditional-Drivers.

[/COLOR]**Re: How to install DELL Wireless 1397 WLAN Mini Card**
[COLOR=#000000][INDENT]I believe that card is a BCM4312 Broadcom card. If so, follow the steps already mentioned (make sure you have wired access for it to work). It uses the STA driver (also called the "wl", which is WL in lowercase) normally for best performance, but if necessary it can use the b43. However, b43 performance sometimes doesn't work at all and others have complained of it being slow and disconnecting often. I have a BCM4312 and with the b43 I could not get over about 4.2Mbps but with the STA got to my max of 6.82Mbps (the speed of my service).
Your mileage may vary, but I recommend the STA driver first if it offers both.[/INDENT]
[/COLOR]
**Re: How to install DELL Wireless 1397 WLAN Mini Card**
[COLOR=#000000][INDENT]Problem solved![/INDENT]
[/COLOR]

---

### Post by Hadaka on 2016-11-14
Hi , your wireless report shows this error.
 ```
 ERROR -b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2
```
From a working wired connection,Please open a terminal ctrl/alt/t
Please Copy and paste the following commands one at a time

*Ignore any errors or file not found for commands 2 or 3

```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
Then Copy and paste to the terminal..
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
 *Remove the wired connection *BOOT and test wireless
Thanks.

---

### Post by davecardnell on 2016-11-14
Problem solved, by installing a new driver.
Thanks for the very quick replies - magic.

---

### Post by Hadaka on 2016-11-14
@stan26.. 
  Hi..  Please see..[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) for instruction on how
to correctly determine a Broadcom driver.
This number can be *anything ..Broadcom Corporation BCM4312 .. It is the CARD number not the driver number.
This is the correct number to determine the DRIVER...[14e4:4315]...  PCI-ID#  14e4=vendor  4315=driver
PCI-ID [14e4:4315] performs best with the B43 driver not the WL 
Thanks.

---

