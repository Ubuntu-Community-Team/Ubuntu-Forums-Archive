---
title: "No wireless networks found while using ndiswrapper with Broadcom card"
date: 2017-01-18
forum: Networking &amp; Wireless
---

### Post by mike1122 on 2017-01-18
Hi, I originally set out to use a Broadcom 4306 (Rev 02) card with the b43legacy firmware as described in the Broadcom guide, but was never able to succeed in connecting to my wireless network.  I also tried many suggestions found in other threads.  The furthest I got was the ability to see wireless networks in range but received a "bad password" response from Wicd. I tried Network Manager as well, but it also would not connect.  Also tried these configurations with no security settings/encryption (instead of WPA2).  

I eventually came upon a [thread]("http://ubuntuforums.org/showthread.php?t=2095736") (from 2012) suggesting ndiswrapper and the bcmwl5a.inf driver for this particular card.  Under this configuration I can no longer see any wireless networks but I'm hoping the problem may be easier to resolve than that with the b43 drivers.  Here are two of the symptoms that stood out to me, but the whole Wireless info script report follows.  

I'm happy to revert to the b43 drivers if you'd prefer to work that angle instead.  Thank you in advance!

```
michael@michael-Inspiron-1100:~$ sudo iwlist scan
[sudo] password for michael: 
wlan0     No scan results

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

```
michael@michael-Inspiron-1100:~$ rfkill list all
michael@michael-Inspiron-1100:~$ 
```

```
########## wireless info START ##########

Report from: 18 Jan 2017 13:04 EST -0500

Booted last: 18 Jan 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:36:54 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Lubuntu

##### lspci #############################

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Device [4401:1028]
    Kernel driver in use: b44

03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
    Subsystem: Linksys WPC54G v1 / WPC54GS v1 802.11g Wireless-G Notebook Adapter [1737:4320]
    Kernel driver in use: ndiswrapper

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

ssb                    57344  1 b44
ndiswrapper           200704  0
cfg80211              499712  0
dell_laptop            24576  0
dcdbas                 16384  1 dell_laptop
video                  36864  2 i915,dell_laptop

##### interfaces ########################

sed: can't read /etc/network/interfaces: Permission denied

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.190  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34813 (34.8 KB)  TX bytes:10753 (10.7 KB)
          Interrupt:7 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:48000000-48002000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    206    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     206    0        0 eth0

##### resolv.conf #######################

nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 127.0.1.1
search hsd1.nj.comcast.net

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       701     1  0 12:55 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401 100Base-T
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       d83fb175-0fa8-44fa-b014-21fae5fc0766
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d83fb175-0fa8-44fa-b014-21fae5fc0766 | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.0.190/24
IP4.ADDRESS[2]:                         192.168.0.192/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
IP4.DOMAIN[1]:                          hsd1.nj.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1484849068
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.190
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = hsd1.nj.comcast.net.
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       routers = 192.168.0.1
DHCP4.OPTION[23]:                       domain_name_servers = 208.67.222.222 208.67.220.220
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4306 802.11b/g Wireless LAN Controller (WPC54G v1 / WPC54GS v1 802.11g Wireless-G Notebook Adapter)
GENERAL.DRIVER:                         ndiswrapper
GENERAL.DRIVER-VERSION:                 1.59+Broadcom,11/27/2004, 3.100.
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0/net/wlan0
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Michael1
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[ssb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 686 

[ndiswrapper]
filename:       /lib/modules/4.4.0-59-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     F04579DDA0189592485AA87
depends:        
vermagic:       4.4.0-59-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
ndiswrapper

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
blacklist b43
blacklist ssb
blacklist b43legacy
blacklist b43 ssb
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

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x4401 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4320 (b43legacy)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   71.752278] CPU: 0 PID: 1215 Comm: iwlist Tainted: P        W  OE   4.4.0-59-generic #80-Ubuntu
[   71.752278]  [<f8d4a488>] NdisAllocateBuffer+0x38/0x150 [ndiswrapper]
[   71.752278]  [<f8d4a78a>] ? ndis_isr+0x4a/0xc0 [ndiswrapper]
[   71.752278]  [<f8d5423b>] ? io_irq_isr+0x2b/0xe0 [ndiswrapper]
[   71.752278]  [<f8d4a9e6>] ? NdisMSynchronizeWithInterrupt+0x26/0x30 [ndiswrapper]
[   71.752278]  [<f8d5a2f0>] ? mp_request+0x140/0x3b0 [ndiswrapper]
[   71.752278]  [<f8d44b20>] ? iw_set_bitrate+0x140/0x140 [ndiswrapper]
[   71.752278]  [<f8d44b62>] ? iw_set_scan+0x42/0x80 [ndiswrapper]
[   71.752278]  [<f8d44b20>] ? iw_set_bitrate+0x140/0x140 [ndiswrapper] (repeated 2 times)
[   72.472348] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  347.000138] b44 ssb0:0 eth0: Link is down
[  347.482603] b44 ssb0:0 eth0: powering down PHY
[  356.239830] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  358.278610] b44 ssb0:0 eth0: powering down PHY
[  368.100369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  423.278191] b44 ssb0:0 eth0: powering down PHY
[  444.816424] ndiswrapper: device wlan0 removed
[  444.887513] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  444.971940] ndiswrapper: driver bcmwl5a (Broadcom,11/27/2004, 3.100.35.0) loaded
[  449.550346] ndiswrapper: using IRQ 11
[  449.980858] wlan0: ethernet device <MAC 'wlan0' [IF2]> using NDIS driver: bcmwl5a, version: 0x3642300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[  449.980930] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  450.251461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  556.435779] b44: unknown parameter 'ssb' ignored
[  556.476133] ssb: Found chip with id 0x4401, rev 0x01 and package 0x00
[  556.476150] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[  556.476159] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[  556.476168] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[  556.516363] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[  556.537266] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC 'eth0' [IF1]>
[  556.775457] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  560.000227] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[  560.000240] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[  560.000356] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by Hadaka on 2017-01-19
Hi , please open a terminal ..ctrl/alt/t..
 First...You must decide to run wicd or network manager
both are currently loaded and conflicting...so choose one only.,
****wicd networkmgr ****

then from a WORKING wired connection..COPY
and paste one line at a time...ignore any error
or file not found...Do every line...one at a time.

```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```

```
sudo sed -i '/blacklist b43/ d' /etc/modprobe.d/blacklist.conf
sudo sed -i '/blacklist ssb/ d' /etc/modprobe.d/blacklist.conf
```

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

Remove the wired connection,any and ALL USB devices, BOOT and test wireless
Thanks.

---

### Post by mike1122 on 2017-01-19
Many thanks for the instructions!  I can now see the networks but no success in connecting.  dmesg is showing authentication timeouts and "link is not ready" messages.  Please see detailed script results attached.  Thank you.

[ATTACH]273254[/ATTACH]

---

### Post by praseodym on 2017-01-19
```
sed: can't read /etc/network/interfaces: Permission denied
```
Are you the sudo-user? If yes, the permissions are wrong of that file
```

sudo chmod 644 /etc/network/interfaces
```
Reboot.

---

### Post by mike1122 on 2017-01-19
Ok, good catch.  I've changed the permissions.  On the next reboot only "sudo iwlist scan" would show available networks, but the network manager indicator applet did not (and still doesn't).

Here are the script results from after the reboot:
[ATTACH]273258[/ATTACH]

I opened up the interfaces file and it only had this:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

I temporarily pasted in additional text from an earlier backup to make it look like this but didn't help:

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-psk <KEY>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid Michael1
```

What should the contents of the interfaces file be?

Also tried:

```
sudo ifconfig wlan0 up
```

and

```
sudo iwconfig wlan0 essid Michael1
```

Thanks everyone!

---

### Post by mike1122 on 2017-01-19
Did some research now I understand the interfaces file should only show default info when using network manager.  Once I reverted the file to the correct contents, the wifi networks reappeared in GUI.  Connection attempts still time out.

---

### Post by Hadaka on 2017-01-19
Hi, glad you figured that out, i had just prepared a file to fix that.
your interface file should only have..
 cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```
please click your wifi icon and then > Edit Connections > Wireless
and delete everything. Boot then attempt to connect to your network
by selecting it from the list.

---

### Post by mike1122 on 2017-01-19
Thanks but still nothing further.  Tried setting ipv6 to ignore as well.  Will try removing security next..

---

### Post by Hadaka on 2017-01-19
Hi please post the output of...
```
cat /etc/network/interfaces
```
And also please post a new wireless report.
then configure your connection like the 4 screenshots attached.
[ATTACH=CONFIG]273263[/ATTACH][ATTACH=CONFIG]273264[/ATTACH][ATTACH=CONFIG]273265[/ATTACH][ATTACH=CONFIG]273266[/ATTACH]
thanks

---

### Post by mike1122 on 2017-01-19
```
michael@michael-Inspiron-1100:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

Wireless report:
[ATTACH]273267[/ATTACH]

The wireless configuration interface I have shows the selected Mode as "Client" (other options are "Ad-Hoc" and "Hotspot").  I'm thinking "Infrastructure", as you have, is equivalent.  I ticked "Available to all users" and added the DNS server addresses.

much appreciated..

---

### Post by mike1122 on 2017-01-20
Ok, Network Manager popped up asking for wifi password to be entered twice (which is weird since it's already saved in the connection editor).  Anyhow, two "associations" are now shown in dmesg.  The only thing I may've done that preceded this was starting the r8169 module.  Tried to flip it off and on again with no success in reproducing the associations for wlan0 so seems barely worth mentioning.

```
[  930.093887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1039.000237] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 1039.000251] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 1177.000147] b44 ssb1:0 eth0: Link is down
[ 1188.758907] wlan0: authenticate with 00:18:xx:xx:xx:xx
[ 1188.761099] wlan0: send auth to 00:18:xx:xx:xx:xx (try 1/3)
[ 1188.965321] wlan0: send auth to 00:18:xx:xx:xx:xx (try 2/3)
[ 1189.168135] wlan0: send auth to 00:18:xx:xx:xx:xx (try 3/3)
[ 1189.372075] wlan0: authentication with 00:18:xx:xx:xx:xx timed out
[ 1200.162219] wlan0: authenticate with 00:18:xx:xx:xx:xx
[ 1200.171147] wlan0: send auth to 00:18:xx:xx:xx:xx (try 1/3)
[ 1200.372119] wlan0: send auth to 00:18:xx:xx:xx:xx (try 2/3)
[ 1200.576139] wlan0: send auth to 00:18:xx:xx:xx:xx (try 3/3)
[ 1200.780139] wlan0: authentication with 00:18:xx:xx:xx:xx timed out
[ 1213.089668] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1256.554905] wlan0: authenticate with 00:18:xx:xx:xx:xx
[ 1256.557117] wlan0: send auth to 00:18:xx:xx:xx:xx (try 1/3)
[ 1256.760135] wlan0: send auth to 00:18:xx:xx:xx:xx (try 2/3)
[ 1256.964150] wlan0: send auth to 00:18:xx:xx:xx:xx (try 3/3)
[ 1256.966569] wlan0: authenticated
[ 1256.970359] wlan0: associate with 00:18:xx:xx:xx:xx (try 1/3)
[ 1257.172093] wlan0: associate with 00:18:xx:xx:xx:xx (try 2/3)
[ 1257.376084] wlan0: associate with 00:18:xx:xx:xx:xx (try 3/3)
[ 1257.408940] wlan0: RX AssocResp from 00:18:xx:xx:xx:xx (capab=0x431 status=0 aid=1)
[ 1257.416173] wlan0: associated
[ 1257.416358] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1267.430224] wlan0: deauthenticating from 00:18:xx:xx:xx:xx by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1267.505424] cfg80211: World regulatory domain updated:
[ 1267.505438] cfg80211:  DFS Master region: unset
[ 1267.505441] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 1267.505448] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 1267.505453] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 1267.505456] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[ 1267.505461] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[ 1267.505466] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[ 1267.505470] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[ 1267.505474] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[ 1267.505478] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[ 1267.575676] cfg80211: Regulatory domain changed to country: US
[ 1267.575688] cfg80211:  DFS Master region: FCC
[ 1267.575692] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 1267.575698] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[ 1267.575703] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[ 1267.575708] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[ 1267.575713] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[ 1267.575717] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[ 1267.575721] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[ 1284.110785] wlan0: authenticate with 00:18:xx:xx:xx:xx
[ 1284.113396] wlan0: send auth to 00:18:xx:xx:xx:xx (try 1/3)
[ 1284.316128] wlan0: send auth to 00:18:xx:xx:xx:xx (try 2/3)
[ 1284.318800] wlan0: authenticated
[ 1284.321925] wlan0: associate with 00:18:xx:xx:xx:xx (try 1/3)
[ 1284.524147] wlan0: associate with 00:18:xx:xx:xx:xx (try 2/3)
[ 1284.728075] wlan0: associate with 00:18:xx:xx:xx:xx (try 3/3)
[ 1284.730663] wlan0: RX AssocResp from 00:18:xx:xx:xx:xx (capab=0x431 status=0 aid=1)
[ 1284.736151] wlan0: associated
[ 1294.754202] wlan0: deauthenticating from 00:18:xx:xx:xx:xx by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1294.828540] cfg80211: World regulatory domain updated:
[ 1294.828555] cfg80211:  DFS Master region: unset
[ 1294.828559] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 1294.828567] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 1294.828571] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 1294.828575] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[ 1294.828580] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[ 1294.828585] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[ 1294.828589] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[ 1294.828593] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[ 1294.828597] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[ 1294.895683] cfg80211: Regulatory domain changed to country: US
[ 1294.895697] cfg80211:  DFS Master region: FCC
[ 1294.895701] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 1294.895707] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[ 1294.895712] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[ 1294.895717] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[ 1294.895721] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[ 1294.895725] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[ 1294.895729] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[ 1314.808594] wlan0: authenticate with 00:18:xx:xx:xx:xx
[ 1314.808865] wlan0: send auth to 00:18:xx:xx:xx:xx (try 1/3)
[ 1315.012130] wlan0: send auth to 00:18:xx:xx:xx:xx (try 2/3)
[ 1315.216139] wlan0: send auth to 00:18:xx:xx:xx:xx (try 3/3)
[ 1315.420146] wlan0: authentication with 00:18:xx:xx:xx:xx timed out
[ 1326.211705] wlan0: authenticate with 00:18:xx:xx:xx:xx
[ 1326.212006] wlan0: send auth to 00:18:xx:xx:xx:xx (try 1/3)
[ 1326.416134] wlan0: send auth to 00:18:xx:xx:xx:xx (try 2/3)
[ 1326.620127] wlan0: send auth to 00:18:xx:xx:xx:xx (try 3/3)
[ 1326.824161] wlan0: authentication with 00:18:xx:xx:xx:xx timed out



```

---

### Post by Hadaka on 2017-01-20
Hi you loaded the b43 legacy dirver, it is no longer valid.
  From a working wired connection please do..
```
sudo rm -rf dell_laptop
sudo rm -rf b43legacy
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

ROUTER *
Also you are on channel 3 for some reason...please choose  ch# 1,6 or 11
and choose wpa2 AES wpa2 ccmp....NO  TKIP..please remove.
thanks.

---

### Post by mike1122 on 2017-01-20
Followed your router instructions first and that produced several 'authentication' messages and password requests immediately. Then 'association' times out.

The b43legacy module appears to be loading on boot.  And I still see it in '[COLOR=#000000][FONT=&amp]lsmod'[/FONT][/COLOR] after running '[COLOR=#000000][FONT=&amp]sudo rm -rf b43legacy'[/FONT][/COLOR] (not sure if that is ok).  I also see b43legacy has claimed wireless interface in 'lshw -C network'.  I think I can get b43 to claim the wireless network, will at least attempt it.[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]cat /etc/modules[/FONT][/COLOR] contains 'lp' and 'ndiswrapper'

[COLOR=#000000][FONT=&amp]Thanks.


[/FONT][/COLOR]

---

### Post by mike1122 on 2017-01-20
Note, when b43 claims wireless network I can no longer see wifi networks or wlan0 anywhere.

---

### Post by Hadaka on 2017-01-20
hi, let's fix this..
"[COLOR=#000000][FONT=&amp]cat /etc/modules[/FONT][/COLOR] contains 'lp' and 'ndiswrapper'
please do... to overwrite the file...
```
echo "lp" | sudo tee /etc/modules
sudo modprobe b43
```
remove wired connection, any usb devices ,BOOT and test wireless
*If you still do not connect please post a fresh wireless diagnostic report.
Thanks.

---

### Post by mike1122 on 2017-01-20
Ok, I think the modules file looks good now, but no connection on boot.  b43legacy is still appearing, as you can see in attached report.  Really appreciate your help, we will get there!

---

### Post by mike1122 on 2017-01-20
[ATTACH]273290[/ATTACH]

---

### Post by Hadaka on 2017-01-21
Hi, please do from a working wired connection..
```
sudo modprobe -rf b43
sudo apt-get remove --purge firmware-b43legacy-installer
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
remove the wired connection,any usb device..BOOT and test wireless.
Thanks

---

### Post by mike1122 on 2017-01-21
Success!   Well, I was pretty confident that b43-legacy was getting us closer to a connection so purged the legacy installer files first as you said, but then re-installed them, (instead of using b43).  Also, had just prior to that repeated nearly all of your earlier command suggestions.  dmesg has been stacking up a bunch of the following error messages but I think we can save that for a new post another day perhaps b43legacy-phy0 ERROR: PHY transmission error  Final wireless results file for records: [ATTACH]273292[/ATTACH]  Thank you very much Hadaka!

---

### Post by Hadaka on 2017-01-21
Great ! glad to see you got it working.
Thank you for taking the time to mark
your thread Solved.

---

### Post by mike1122 on 2017-01-31
Update: my connection problems returned.  While I had been connected for hours at a time initially, and through multiple reboots, I was shortly thereafter disconnected mid-session, while computer was idle, and also after reboots.  I had not performed any updates or system changes, except to repeat commands found in this thread.  Given the [bug reports]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558950") regarding this card, I decided to put it out of its misery and install a panda wireless usb adapter.  Popped it in and was connected within moments.  Was also able to return router to mixed mode security settings.

---

