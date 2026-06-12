---
title: "BCM94352 No Networks Found"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by sniderjc on 2015-08-26
Hi all,

After a considerable amount of searching I have thrown up the white flag and would appreciate a little help.

Early on TL;DR: I'm running Ubuntu 15.04 x64 Desktop, UEFI. I have a BCM94352Z WLAN card in my laptop. Specifically the Dell DW1560, the same card found in XPS 13 9343 machines. ([Pic]("http://i.ebayimg.com/00/s/MTIwMFgxNjAw/z/FoIAAOSwstxVNGwq/$_1.JPG?set_id=880000500F")) Using the Broadcom STA drivers the wireless card is detected, but no networks are ever detected. I am experiencing the same exact behavior with b43 and even ndiswrapper. (I reinstalled Ubuntu cleanly before trying each of those.) No obvious errors were shown in dmesg.

What I've Done:
1. Tried Broadcom STA drivers, b43 and ndiswrapper - clean installs in between each trial.
2. Checked rfkill list. -- No hard or soft blocks.
3. Toggled the Airplane mode button on the keyboard repeatedly.
4. Disabled BIOS Secure Boot
5. A lot more but I am so brain dead right now from working on this I can't think. :P

As of now,I am back to a clean slate, 15.04. It has internet access through an ethernet cable. Can anyone tell me the proper way to proceed and why even when the card is properly detected I may not be finding local networks? I am ready to follow whatever directions you give to debug this :D


Full Disclosure:
I am having the exact same problem in Windows. The driver will properly install but will find no networks. The device DOES work in THIS machine, however. Under an osx installation the card works beautifully. -- I am only mentioning that because the difference in how each OS communicates with the card may highlight the exact problem.  One final note is that this is a X1 Carbon (3rd gen), not a Dell PC. I don't foresee this being relevant considering the card does work on this device (no bios whitelist or anything) but it is also worth mentioning.

---

### Post by Bucky Ball on 2015-08-26
Welcome. Please provide the output of the wirelessinfo script in my signature.

---

### Post by sniderjc on 2015-08-26
Hi Bucky.

At my current clean installation state, here is what your script output returns.
```

########## wireless info START ##########

Report from: 26 Aug 2015 14:00 EDT -0400

Booted last: 26 Aug 2015 09:54 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-LM [8086:15a2] (rev 03)
    Subsystem: Lenovo Device [17aa:2227]
    Kernel driver in use: e1000e

04:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]

##### lsusb #############################

Bus 001 Device 005: ID 04ca:7049 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 003: ID 138a:0017 Validity Sensors, Inc. 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              540672  0 
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.38.51.222  Bcast:10.38.51.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45993426 (45.9 MB)  TX bytes:1954571 (1.9 MB)
          Interrupt:20 Memory:e1300000-e1320000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.38.48.1      0.0.0.0         UG    1024   0        0 eth0
10.38.48.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.28.121.50   10.38.48.1      255.255.255.255 UGH   1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search dorms.nku.edu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       653     1  0 13:54 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.3.2-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       74ca7c58-a48f-4cae-8af9-1274037b1a39
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   74ca7c58-a48f-4cae-8af9-1274037b1a39 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 10.38.51.222/22, gw = 10.38.48.1
IP4.ROUTE[1]:                           dst = 172.28.121.50/32, nh = 10.38.48.1, mt = 1
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.122.237.203
IP4.DNS[2]:                             192.122.237.204
IP4.DOMAIN[1]:                          dorms.nku.edu
DHCP4.OPTION[1]:                        network_number = 10.38.48.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1440640451
DHCP4.OPTION[9]:                        domain_name = dorms.nku.edu
DHCP4.OPTION[10]:                       next_server = 172.28.121.50
DHCP4.OPTION[11]:                       broadcast_address = 10.38.51.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.38.48.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 28800
DHCP4.OPTION[16]:                       ip_address = 10.38.51.222
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.122.237.203 192.122.237.204
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.252.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.28.121.50
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::

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

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a2 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    1.748631] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    1.748634] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[    5.556928] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############


```

That is WITHOUT any drivers installed. If I take the next step, and use my wireless card info and follow [this guide by chili]("http://ubuntuforums.org/showthread.php?t=2214110") (apt-get update and then install bcmwl-kernel-source) then I get more detailed output, but I can never locate wireless access points.

Wireless Info Script output after bcmwl-kernel-source installation and restart.
```

########## wireless info START ##########

Report from: 26 Aug 2015 14:08 EDT -0400

Booted last: 26 Aug 2015 10:07 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-LM [8086:15a2] (rev 03)
    Subsystem: Lenovo Device [17aa:2227]
    Kernel driver in use: e1000e

04:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 005: ID 04ca:7049 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 003: ID 138a:0017 Validity Sensors, Inc. 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6369280  0 
cfg80211              540672  1 wl
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.38.51.222  Bcast:10.38.51.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3234980 (3.2 MB)  TX bytes:278528 (278.5 KB)
          Interrupt:20 Memory:e1300000-e1320000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.38.48.1      0.0.0.0         UG    1024   0        0 eth0
10.38.48.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.28.121.50   10.38.48.1      255.255.255.255 UGH   1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search dorms.nku.edu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       703     1  0 14:07 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.3.2-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a9426bbd-75af-46fc-8f2c-927123fdeef6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a9426bbd-75af-46fc-8f2c-927123fdeef6 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 10.38.51.222/22, gw = 10.38.48.1
IP4.ROUTE[1]:                           dst = 172.28.121.50/32, nh = 10.38.48.1, mt = 1
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.122.237.203
IP4.DNS[2]:                             192.122.237.204
IP4.DOMAIN[1]:                          dorms.nku.edu
DHCP4.OPTION[1]:                        network_number = 10.38.48.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1440641239
DHCP4.OPTION[9]:                        domain_name = dorms.nku.edu
DHCP4.OPTION[10]:                       next_server = 172.28.121.50
DHCP4.OPTION[11]:                       broadcast_address = 10.38.51.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.38.48.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 28800
DHCP4.OPTION[16]:                       ip_address = 10.38.51.222
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.122.237.203 192.122.237.204
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.252.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.28.121.50
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4352 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes

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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-15-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a2 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    1.462318] wl: module license 'MIXED/Proprietary' taints kernel.
[    1.464398] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    1.655832] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    1.896170] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    1.896172] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[    5.527205] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   83.266831] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

Thanks for your time and effort looking into this.

---

### Post by chili555 on 2015-08-27
This is my favorite kind of problem. Everything looks just perfect; except it doesn't work!

Please confirm that you have the latest bcmwl-kernel-source:```
sudo dpkg -s bcmwl-kernel-source
```We hope you see:```
Version: 6.30.223.248+bdcom-0ubuntu2
```Please confirm that your home router is not locked to either 2.4 or 5 Ghz. I suggest Auto.

Does the card scan and see networks in any location at all? Work, library, coffee shop?? 

Finally, I see that the ethernet is connected and has an IP address. Please detach the ethernet, restart NM and try again:```
sudo service network-manager restart
sudo iwlist wlan0 scan
```Any change?

---

### Post by sniderjc on 2015-08-27
Thanks so much for looking into this Chili, I really appreciate it!!

Soo... a little extra background;
I am living in dorms on a college campus so there are wifi networks all around me. (Both 5Ghz and 2.4Ghz)
The only router that is actually in my possession that I can modify settings for runs in 2.4Ghz (it is fairly old).

To answer your second question. The card does not see any networks at all in Ubuntu. ([SIZE=1]But it works annoying well in OSX 20+ hotspots, both bands)
[/SIZE]
The output of 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg -s bcmwl-kernel-source[/FONT][/COLOR]
```

was 

```
Package: bcmwl-kernel-sourceStatus: install ok installed
Priority: optional
Section: admin
Installed-Size: 7850
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
```

So the version number was correct.

After disconnecting ethernet and running the following commands:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo service network-manager restart
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo iwlist wlan0 scan[/FONT][/COLOR]
```

Terminal returned:
```
wlan0   No scan results
```

No change thus far. What's on deck? :P

---

### Post by chili555 on 2015-08-27
Let's look at a few other things:```
dmesg | grep 04:00
```04:00 is the bus number the card sits on. I wonder if there is any ACPI or other difficulty there.

Also:```
cat /var/log/syslog | grep  wl | tail -n20 
```wl will give us both wl the driver and wlan0 the interface.

If the output is sparse, it indicates that the log was recently archived and restarted. In that case, make it syslog.1, the most recent archive.

I suggest you post the result here and give me the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by sniderjc on 2015-08-27
Output of ```
dmesg | grep 04:00
``` is
```
[    0.393940] pci 0000:04:00.0: [14e4:43b1] type 00 class 0x028000
[    0.393982] pci 0000:04:00.0: reg 0x10: [mem 0xe1200000-0xe1207fff 64bit]
[    0.394012] pci 0000:04:00.0: reg 0x18: [mem 0xe1000000-0xe11fffff 64bit]
[    0.394258] pci 0000:04:00.0: supports D1 D2
[    0.394263] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold

```

Output of 
```
cat /var/log/syslog | grep  wl | tail -n20
``` can be found [here.]("http://paste.ubuntu.com/12206841/")

Thanks again for the support. I hope this sheds some light on the issue.

---

### Post by Bucky Ball on 2015-08-27
> **chili555 said:**
> This is my favorite kind of problem. Everything looks just perfect; except it doesn't work!

+1. Exactly. I'm no expert but that's what I thought before I collapsed in bed and slept last night.

---

### Post by sniderjc on 2015-08-27
I want to add in a couple of thoughts or ideas. Feel free to ignore these as I have no knowledge in these matters. (Only a strong CS background, mainly in Java/C# and web development)

1st. Is there any way that OSX can be ****ing with me, as in placing some lock or handle on the WLAN card so that it needs to be 'reset' or something to work in Windows? No idea how this would work or if that is even remotely possible.

2nd. Does the country/region code apply in Linux? Any way to make sure it is set to US? I bought the card directly from Dell so I don't see how it could be any different. Could this contribute to the behavior I am seeing?


One more note that I forgot to add. When I originally started debugging this last week, I noticed that on Windows & Linux I could create an adhoc network that would successfully broadcast to other devices. (My iPhone could see it.) With that said, I could never connect.

Again, thanks for the continued input. I will standby for input :D

---

### Post by chili555 on 2015-08-28
Sorry for the delay in my reply. I have nearly scratched my head bald trying to figure out this one!> 1st. Is there any way that OSX can be ****ing with me, as in placing some lock or handle on the WLAN card so that it needs to be 'reset' or something to work in Windows? No idea how this would work or if that is even remotely possible.It's somewhat doubtful. I have seen a few cases where Windows essentially turns off the wireless and Linux can't turn it back on. The tell-tale is in* rfkill *where we see 'hard blocked:yes.' That is not the case here.

I have also seen a few cases where wake-on-lan was turned off in Windows and the ethernet card was unable to be turned on in Linux. I have never seen the same for a wireless card where, AFAIK, wake-on-lan is not available. In any event, it is certainly worth looking around in OSX. While you are at it, include the BIOS in your investigations.> 2nd. Does the country/region code apply in Linux? Any way to make sure it is set to US? I bought the card directly from Dell so I don't see how it could be any different. Could this contribute to the behavior I am seeing?I think it is a very slight possibility. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor. Reboot. Any change?>  I noticed that on Windows & Linux I could create an adhoc network that would successfully broadcast to other devices. (My iPhone could see it.) Including this Broadcom device??

---

### Post by sniderjc on 2015-08-28
Hi Chili,

I will check the region settings tonight when I get home and follow up.

But yes! With this device I can setup an adhoc network and it will broadcast on Windows & Linux. Not sure what that means except for the radio is technically on. Still not finding access points or anything. Does this mean anything to you?

Will follow up after I try the region modifications.

Thanks,
JC

---

### Post by chili555 on 2015-08-28
Is Network Manager set to AdHoc? Try setting it to Infrastructure and see if the device scans.

[ATTACH=CONFIG]264095[/ATTACH]

---

### Post by sniderjc on 2015-08-28
No, at this time no networks are setup at all. I am just trying to get it to scan for some. Just wanted to add in the fact that adhoc networks would broadcast, not that I could ever connect.


The region was 00, set it to US. No change.

---

