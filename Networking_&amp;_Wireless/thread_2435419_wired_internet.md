---
title: "wired internet"
date: 2020-01-20
forum: Networking &amp; Wireless
---

### Post by rdema19403 on 2020-01-20
i just a fresh install of ubuntu 18.04 and cannot get the wired lan to work 
the wireless works great when i try to connect it says connection failed
aany ideas 
Thanks in advance

---

### Post by praseodym on 2020-01-20
Please run the wireless script from the sticky thread and show the outputs

---

### Post by rdema19403 on 2020-01-21
__i need help the wired portion to connect to the internet my wireless works okay
Thanks

---

### Post by TheFu on 2020-01-21
This link has some basic steps to follow: [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
Is is mostly ping steps in a specific order to see where the issue lies.

If the ping stuff doesn't work, **sudo lshw -C network** will get into the driver stuff.

---

### Post by rdema19403 on 2020-01-22
sudo lshw -c network results```

sudo] password for rd: 
  *-network                 
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlp14s0
       version: 00
       serial: 00:16:ea:75:d3:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-74-generic firmware=8.83.5.1 build 33692 ip=192.168.1.22 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:25 memory:f2100000-f2101fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: enp20s0
       version: 02
       serial: 00:1e:ec:5b:ee:30
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 ioport:4000(size=256) memory:f2010000-f2010fff memory:f2000000-f200ffff memory:80600000-8060ffff
rd@rd-Vostro-2420:~$
```

computer ip address```

<pre>1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp20s0: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1e:ec:5b:ee:30 brd ff:ff:ff:ff:ff:ff
3: wlp14s0: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:16:ea:75:d3:8e brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.22/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp14s0
       valid_lft 84324sec preferred_lft 84324sec
    inet6 fe80::50af:da47:1834:6319/64 scope link noprefixroute 
       valid_lft forever preferred_lft foreve</pre>
```

router ip address```

rd@rd-Vostro-2420:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp14s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp14s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp14s0
rd@rd-Vostro-2420:~$
```

---

### Post by coffeecat on 2020-01-22
@redema19403, without BBCode code tags your terminal output lost formatting and was almost impossible to read. I have added code tags to restore formatting and merged the three posts into one.

Please use code tags where necessary. There's a link in my sig for using code tags if you need it.

---

### Post by rdema19403 on 2020-01-22
thankyou

---

### Post by TheFu on 2020-01-22
Disable the wifi interface, please and re-run the **ip addr** and **ping** tests.

Lots of people have issues with RTL8111/8168/8411 PCI Express Gigabit NICs. These forums are full of advice to get those working. The driver and specific VERSION of the NIC matter.

And don't forget to change the cat5e cable and try a different switch port.

It looks like the wifi adaptor taking priority.

---

### Post by deadflowr on 2020-01-22
> **rdema19403 said:**
> __i need help the wired portion to connect to the internet my wireless works okay
Thanks

The script outputs useful information on both wired and wireless.

---

### Post by rdema19403 on 2020-01-22
```
[@rd-Vostro-2420:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp20s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1e:ec:5b:ee:30 brd ff:ff:ff:ff:ff:ff
3: wlp14s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 00:16:ea:75:d3:8e brd ff:ff:ff:ff:ff:ff

```

```
rd@rd-Vostro-2420:~$  ping
Usage: ping [-aAbBdDfhLnOqrRUvV64] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
Usage: ping -6 [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
             [-l preload] [-m mark] [-M pmtudisc_option]
             [-N nodeinfo_option] [-p pattern] [-Q tclass] [-s packetsize]
             [-S sndbuf] [-t ttl] [-T timestamp_option] [-w deadline]
             [-W timeout] destination
rd@rd-Vostro-2420:~$
```

---

### Post by rdema19403 on 2020-01-23
i was wondering if somebody can give me an idea really not sure what to do?

Thanks in advane

---

### Post by TheFu on 2020-01-23
> **rdema19403 said:**
> i was wondering if somebody can give me an idea really not sure what to do?

Thanks in advane

Have you done the things requested above?

---

### Post by rdema19403 on 2020-01-23
yes i have

---

### Post by TheFu on 2020-01-23
> **rdema19403 said:**
> yes i have

Ok, where's the **wireless-info** script output? There's a sticky thread for this at the top of the Networking - so you can find it next time.  [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Initially, a link for troubleshooting wired Linux connections was provided which has a number of basic steps to gather information. I haven't seen that output either.  BTW - some later posts make it clear that those troubleshooting steps aren't likely to help, but we would have learned so much from them if provided when requested.

Whenever doing the testing for wired, please disable the wireless connection.

Hard to help without the needed info.

I suggested that others had similar issues with similar hardware in these forums. Their solutions are very likely to work for you. When you searched for those, which did you try, exactly?

---

### Post by rdema19403 on 2020-01-24
wireless info from link
```

########## wireless info START ##########

Report from: 24 Jan 2020 13:28 EST -0500

Booted last: 24 Jan 2020 00:00 EST -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

0e:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
	Kernel driver in use: iwlwifi

14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: COMPAL Electronics Inc RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [14c0:0031]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 064e:a115 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: compal-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: compal-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
iwldvm                229376  0
mac80211              786432  1 iwldvm
iwlwifi               290816  1 iwldvm
cfg80211              622592  3 iwldvm,iwlwifi,mac80211

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp20s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp20s0' [IF1]> brd <MAC address>
    inet6 fe80::11f8:3474:cb5b:21f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp14s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp14s0' [IF2]> brd <MAC address>
    inet 192.168.1.22/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp14s0
       valid_lft 86297sec preferred_lft 86297sec
    inet6 fe80::d780:ecfe:1c7f:923a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp20s0   no wireless extensions.

wlp14s0   IEEE 802.11  ESSID:"NETGEAR66"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'NETGEAR66' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0

##### route #############################

default via 192.168.1.1 dev wlp14s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp14s0 scope link metric 1000 
192.168.1.0/24 dev wlp14s0 proto kernel scope link src 192.168.1.22 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

	NetworkManager

Running:

root       545     1  0 13:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp14s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        WiFi Link 5100 (AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.15.0-74-generic
GENERAL.FIRMWARE-VERSION:               8.83.5.1 build 33692
GENERAL.HWADDR:                         <MAC 'wlp14s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0/net/wlp14s0
GENERAL.IP-IFACE:                       wlp14s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     NETGEAR66 1
GENERAL.CON-UUID:                       59eeefb2-5df8-40f5-942f-3cbb66a190b0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
IP4.ADDRESS[1]:                         192.168.1.22/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_interface_mtu = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_ntp_servers = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        expiry = 1579976782
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_broadcast_address = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       ip_address = 192.168.1.22
DHCP4.OPTION[16]:                       requested_subnet_mask = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       requested_netbios_scope = 1
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       routers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_static_routes = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::d780:ecfe:1c7f:923a/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   59eeefb2-5df8-40f5-942f-3cbb66a190b0 | NETGEAR66 1

GENERAL.DEVICE:                         enp20s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp20s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          70 (connecting (getting IP configuration))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:14:00.0/net/enp20s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       39d55932-269c-3ac2-93c1-037d16a3524c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   39d55932-269c-3ac2-93c1-037d16a3524c | Wired connection 1

SSID                           BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
NETGEAR66                      <MAC 'NETGEAR66' [AC1]>  Infra  1     2412 MHz  195 Mbit/s  81      &#9602;&#9604;&#9606;&#9608;  --        yes     *      
linksys                        <MAC 'linksys' [AC2]>  Infra  6     2437 MHz  54 Mbit/s   79      &#9602;&#9604;&#9606;_  --        no             
NETGEAR66-5G                   <MAC 'NETGEAR66-5G' [AC4]>  Infra  149   5745 MHz  135 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2      no             
linksys                        <MAC 'linksys' [AC3]>  Infra  6     2437 MHz  54 Mbit/s   55      &#9602;&#9604;__  --        no             
DIRECT-1B-HP ENVY 4520 series  <MAC 'DIRECT-1B-HP ENVY 4520 series' [AN5]>  Infra  11    2462 MHz  65 Mbit/s   35      &#9602;&#9604;__  WPA2      no             

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NETGEAR66]] (600 root)
[connection] id=NETGEAR66 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR66
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR66 1]] (600 root)
[connection] id=NETGEAR66 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp14s0' [IF2]> | mac-address-blacklist= | ssid=NETGEAR66
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp20s0   no frequency information.

wlp14s0   32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp20s0   Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.745 GHz

wlp14s0   Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR66' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000031c7f3d6e95
                    Extra: Last beacon: 124ms ago
          Cell 02 - Address: <MAC 'linksys' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000056bbbb94a3b
                    Extra: Last beacon: 4956ms ago
          Cell 03 - Address: <MAC 'linksys' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f189a18ca1
                    Extra: Last beacon: 4944ms ago
          Cell 04 - Address: <MAC 'NETGEAR66-5G' [AC4]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR66-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031c7fb47461
                    Extra: Last beacon: 824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.15.0-74-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     5144A889CD9311D5F87BAC3
depends:        mac80211,iwlwifi,cfg80211
retpoline:      Y
intree:         Y
name:           iwldvm
vermagic:       4.15.0-74-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.15.0-74-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A4E977BF9AF960320AE4253
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-74-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.15.0-74-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
srcversion:     68E0A9555B721ED50137C51
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-74-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.15.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8074B69894BD60D7367507A
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-74-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    6.558935] IPv6: ADDRCONF(NETDEV_UP): enp20s0: link is not ready
[    6.605238] r8169 0000:14:00.0 enp20s0: link down (repeated 2 times)
[    6.605346] IPv6: ADDRCONF(NETDEV_UP): enp20s0: link is not ready
[    7.772299] iwlwifi 0000:0e:00.0 wlp14s0: renamed from wlan0
[    8.082431] IPv6: ADDRCONF(NETDEV_UP): wlp14s0: link is not ready
[    8.091481] iwlwifi 0000:0e:00.0: Radio type=0x1-0x2-0x0 (repeated 2 times)
[    8.343847] IPv6: ADDRCONF(NETDEV_UP): wlp14s0: link is not ready (repeated 2 times)
[    9.398310] r8169 0000:14:00.0 enp20s0: link up
[    9.398323] IPv6: ADDRCONF(NETDEV_CHANGE): enp20s0: link becomes ready
[   11.655243] wlp14s0: authenticate with <MAC 'NETGEAR66' [AC1]>
[   11.657418] wlp14s0: send auth to <MAC 'NETGEAR66' [AC1]> (try 1/3)
[   11.660181] wlp14s0: authenticated
[   11.660468] wlp14s0: waiting for beacon from <MAC 'NETGEAR66' [AC1]>
[   11.744045] wlp14s0: associate with <MAC 'NETGEAR66' [AC1]> (try 1/3)
[   11.747373] wlp14s0: RX AssocResp from <MAC 'NETGEAR66' [AC1]> (capab=0x401 status=0 aid=10)
[   11.750160] wlp14s0: associated
[   11.751291] IPv6: ADDRCONF(NETDEV_CHANGE): wlp14s0: link becomes ready
[   36.933113] wlp14s0: deauthenticating from <MAC 'NETGEAR66' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   36.975928] iwlwifi 0000:0e:00.0: RF_KILL bit toggled to disable radio.
[   36.975932] iwlwifi 0000:0e:00.0: reporting RF_KILL (radio disabled)
[   69.762858] iwlwifi 0000:0e:00.0: RF_KILL bit toggled to enable radio.
[   69.762862] iwlwifi 0000:0e:00.0: reporting RF_KILL (radio enabled)
[   69.774136] iwlwifi 0000:0e:00.0: Radio type=0x1-0x2-0x0 (repeated 2 times)
[   69.930302] IPv6: ADDRCONF(NETDEV_UP): wlp14s0: link is not ready (repeated 2 times)
[   73.210643] wlp14s0: authenticate with <MAC 'NETGEAR66' [AC1]>
[   73.212198] wlp14s0: send auth to <MAC 'NETGEAR66' [AC1]> (try 1/3)
[   73.216379] wlp14s0: authenticated
[   73.220385] wlp14s0: associate with <MAC 'NETGEAR66' [AC1]> (try 1/3)
[   73.223939] wlp14s0: RX AssocResp from <MAC 'NETGEAR66' [AC1]> (capab=0x401 status=0 aid=10)
[   73.226128] wlp14s0: associated
[   73.227404] IPv6: ADDRCONF(NETDEV_CHANGE): wlp14s0: link becomes ready

########## wireless info END ############

```

---

### Post by rdema19403 on 2020-01-24
ip address from lan this is from a laptop computer
```
rd@rd-Vostro-2420:~$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp20s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1e:ec:5b:ee:30 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::11f8:3474:cb5b:21f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp14s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 00:16:ea:75:d3:8e brd ff:ff:ff:ff:ff:ff
rd@rd-Vostro-2420:~$ 

```

---

### Post by rdema19403 on 2020-01-24
ip address from wifi

```
rd@rd-Vostro-2420:~$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp20s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1e:ec:5b:ee:30 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::11f8:3474:cb5b:21f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp14s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:16:ea:75:d3:8e brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.22/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp14s0
       valid_lft 86254sec preferred_lft 86254sec
    inet6 fe80::d780:ecfe:1c7f:923a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
rd@rd-Vostro-2420:~$ 

```

---

