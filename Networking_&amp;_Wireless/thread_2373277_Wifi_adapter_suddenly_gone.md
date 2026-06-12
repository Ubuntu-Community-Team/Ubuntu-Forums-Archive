---
title: "Wifi adapter suddenly gone"
date: 2017-10-04
forum: Networking &amp; Wireless
---

### Post by dirkjanvanvliet on 2017-10-04
Recently I've switched from Windows 10 to Ubuntu 16.04. Everything went fine. Wifi was working as it should, until this afternoon. I've done nothing special with my installation, but suddenly there was no available wifi connection and it seemed that also my wifi adapter was completely gone in Ubuntu. I did some research and used the wireless script info ([https://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)). Here is the output: 

```



########## wireless info START ##########


Report from: 04 Oct 2017 20:56 CEST +0200


Booted last: 04 Oct 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.10.0-35-generic #39~16.04.1-Ubuntu SMP Wed Sep 13 09:02:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3854]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 04f2:b57e Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 258a:0001  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


wmi                    16384  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.2.19  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::82d5:fee:ecba:4de0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:931299 (931.2 KB)  TX bytes:232705 (232.7 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50486 (50.4 KB)  TX bytes:50486 (50.4 KB)


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF2]>  
          inet addr:192.168.123.1  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet1' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF3]>  
          inet addr:192.168.45.1  Bcast:192.168.45.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet8' [IF3]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


vmnet1    no wireless extensions.


vmnet8    no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.254   0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0
192.168.45.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.123.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       977     1  0 20:52 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       ec874f3a-76a4-305e-bc7d-0ade65c71cfb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ec874f3a-76a4-305e-bc7d-0ade65c71cfb | Wired connection 1
IP4.ADDRESS[1]:                         192.168.2.19/24
IP4.GATEWAY:                            192.168.2.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.254
IP4.DNS[2]:                             195.121.1.34
IP4.DNS[3]:                             195.121.1.66
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.2.254
DHCP4.OPTION[10]:                       expiry = 1507229573
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.2.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.19
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.2.254 195.121.1.34 195.121.1.66
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.2.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.254
IP6.ADDRESS[1]:                         fe80::82d5:fee:ecba:4de0/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         vmnet1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vmnet1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vmnet1
GENERAL.IP-IFACE:                       vmnet1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         192.168.123.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'vmnet1' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         vmnet8
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vmnet8' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vmnet8
GENERAL.IP-IFACE:                       vmnet8
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         192.168.45.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'vmnet8' [IF3]>/64
IP6.GATEWAY:                            


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


[[/etc/NetworkManager/system-connections/Dirk-Jan]] (600 root)
[connection] id=Dirk-Jan | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Dirk-Jan
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Kantoor]] (600 root)
[connection] id=Kantoor | type=wifi | permissions=user:dirk-jan:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Kantoor
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Amsterdam (based on set time zone)


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


lo        no frequency information.


enp1s0    no frequency information.


vmnet1    no frequency information.


vmnet8    no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


vmnet1    Interface doesn't support scanning.


vmnet8    Interface doesn't support scanning.


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


[/etc/modprobe.d/ideapad-blacklist.conf]
blacklist ideapad-laptop


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   14.879157] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   14.895979] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   14.896033] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   17.355756] r8169 0000:01:00.0 enp1s0: link up
[   17.355762] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[   23.186064] bridge-enp1s0: up
[   23.186066] bridge-enp1s0: attached
[   40.830522] bridge-enp1s0: disabling the bridge on dev down
[   40.830727] bridge-enp1s0: down
[   40.830766] bridge-enp1s0: detached
[   44.342536] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   44.359954] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   44.360042] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   44.360109] bridge-enp1s0: up
[   44.360111] bridge-enp1s0: attached
[   44.360135] bridge-enp1s0: disabling the bridge on dev down
[   44.360173] bridge-enp1s0: down
[   44.360175] bridge-enp1s0: detached
[   46.697545] r8169 0000:01:00.0 enp1s0: link up
[   46.697553] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[   46.698632] bridge-enp1s0: up
[   46.698660] bridge-enp1s0: attached


########## wireless info END ############

```
[ATTACH]276976[/ATTACH]

So it seems that Ubuntu doesn't detect my wifi adapter at all anymore. 

I've checked whether there is some hardware switch on my laptop, there isn't. Also, I've double checked whether wifi is enabled in my bios, it is. I've also tried to disable wifi in my bios, booted ubuntu, rebooted and enabled wifi again and then booted back into Ubuntu. That also didn't help.

What could be the problem? 

Specs:
Lenovo Ideapad 510-15ISK
Ubuntu 16.04

---

### Post by wildmanne39 on 2017-10-04
Please do:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms
```
you will need an internet connection.
Reboot and let us know if it worked.

---

### Post by dirkjanvanvliet on 2017-10-05
Thanks for your reply. However, a miracle happened tonight. I turned off my laptop, and this morning I booted into Ubuntu again and now it works again. Without doing anything. Maybe the trick was to really turn it off instead of merely rebooting it? I'm now guessing some hardware failure. I'll get back here when it happens again and I can't fix it.

---

### Post by wildmanne39 on 2017-10-05
It sounds like a hardware failure, that was always possible but now very likely, I doubt if or when it stops working again we can do anything about it.

---

### Post by Autodave on 2017-10-05
If and when all else fails and nothing makes sense with a laptop, try this:

   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

