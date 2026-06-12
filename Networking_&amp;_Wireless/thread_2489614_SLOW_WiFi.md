---
title: "SLOW WiFi"
date: 2023-08-04
forum: Networking &amp; Wireless
---

### Post by lwalper on 2023-08-04
My WiFi works, but it is SLOW on a laptop with Ubuntu installed as the only OS -- 5mb/s on a 50mb/sec DSL connection. Other devices readily hit 45-50mb/s. Is there some way to "turn up the heat" to get this thing cookin'?

```
lspci -nnk|grep -iA3 net

0000:01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:a85a]
    Subsystem: Hewlett-Packard Company Device [103c:88e2]
    Kernel driver in use: rtw89_8852ae
    Kernel modules: rtw89_8852ae
```

---

### Post by lwalper on 2023-08-05
When I run
```
sudo lshw -C network
```
I get
```
  *-network                 
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 00
       serial: 14:13:33:85:27:3b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw89_8852ae driverversion=6.2.0-26-generic firmware=N/A ip=192.168.1.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:157 ioport:3000(size=256) memory:54000000-540fffff
```

---

### Post by lwalper on 2023-08-05
```
[COLOR=#202124][FONT=&amp]ifconfig | more
```
gives me
[/FONT][/COLOR]```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 873  bytes 98869 (98.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 873  bytes 98869 (98.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.14  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::7314:458a:6cb3:10de  prefixlen 64  scopeid 0x20<link>
        ether 14:13:33:85:27:3b  txqueuelen 1000  (Ethernet)
        RX packets 180740  bytes 156628923 (156.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 102216  bytes 16408244 (16.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by lwalper on 2023-08-05
I've also got a different laptop running WiFi on Windows 10 which consistently downloads at 49+ mb/s. What's up with Ubuntu?

---

### Post by lwalper on 2023-08-05
Running
```
speedtest
```
I, at this moment get
```
Retrieving speedtest.net configuration...
Testing from DTC Communications (64.253.209.72)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Perry Spencer Communications (St Meinrad, IN) [241.85 km]: 60.508 ms
Testing download speed................................................................................
Download: 43.56 Mbit/s
Testing upload speed......................................................................................................
Upload: 10.81 Mbit/s
```
No consistency -- and a 60ms ping?

---

### Post by jeremy31 on 2023-08-05
See the wireless script link in my signature and post results

---

### Post by morrownr on 2023-08-05
> What's up with Ubuntu?

May not be an Ubuntu specific problem but rather a driver problem. That's what I would investigate. Since the driver is an in-kernel, we need to know what kernel version you are using. I think 22.04 started with kernel 5.15 and then 5,19 become available and I think 6.2 is available now. Do you know how to install a HWE kernel? There might be a newer firmware for that chipset also.

I monitor linux-wireless and the driver rtw89 has been undergoing a lot of work over the last few months so moving your installation up to a more modern kernel is what I would start with.

You can even go all the way up to kernel 6.4 if you want to use:

[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

I have a short guide if you want to go that direction.

---

### Post by lwalper on 2023-08-06
This is a portion of the txt file generated --
```
GENERAL.PRODUCT:                        Tiger Lake-LP PCI Express Root Port
GENERAL.DRIVER:                         rtw89_8852ae
GENERAL.DRIVER-VERSION:                 6.2.0-26-generic
```
Updating the kernel is a possibility. You have a guide for that process?

---

### Post by jeremy31 on 2023-08-07
3 lines of the script result isn't much to work with.   It was designed to get all relevant info without revealing much personal information

---

### Post by lwalper on 2023-08-08
```



########## wireless info START ##########


Report from: 06 Aug 2023 13:04 CDT -0500


Booted last: 06 Aug 2023 00:00 CDT -0500


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy


##### kernel ############################


Linux 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


0000:01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:a85a]
	Subsystem: Hewlett-Packard Company Device [103c:88e2]
	Kernel driver in use: rtw89_8852ae


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b710 Chicony Electronics Co., Ltd HP TrueVision HD Camera
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0bda:385a Realtek Semiconductor Corp. Bluetooth Radio
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot disabled
Platform is in Setup Mode


##### lsmod #############################


mac80211             1617920  2 rtw89_core,rtw89_pci
cfg80211             1241088  3 rtw89_core,mac80211,rtw89_8852a
hp_wmi                 24576  0
sparse_keymap          16384  1 hp_wmi
platform_profile       16384  1 hp_wmi
wmi_bmof               16384  0
libarc4                16384  1 mac80211
wmi                    40960  3 hp_wmi,video,wmi_bmof


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF1]> brd <MAC address>
    inet 192.168.1.14/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp1s0
       valid_lft 86213sec preferred_lft 86213sec
    inet6 fe80::7314:458a:6cb3:10de/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"Comtrend3930"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Comtrend3930' [AC3]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:71   Missed beacon:0


##### route #############################


default via 192.168.1.1 dev wlp1s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 
192.168.1.0/24 dev wlp1s0 proto kernel scope link src 192.168.1.14 metric 600 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad
search Home


##### network managers ##################


Installed:


	NetworkManager


Running:


root         592       1  0 06:37 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        Tiger Lake-LP PCI Express Root Port
GENERAL.DRIVER:                         rtw89_8852ae
GENERAL.DRIVER-VERSION:                 6.2.0-26-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/0000:01:00.0/net/wlp1s0
GENERAL.PATH:                           pci-0000:01:00.0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Comtrend3930
GENERAL.CON-UUID:                       5fe38eb6-32e4-4800-9627-08158080d942
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.ADDRESS[1]:                         192.168.1.14/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.DNS[1]:                             64.253.208.121
IP4.DNS[2]:                             208.118.192.121
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[3]:                        domain_name = Home
DHCP4.OPTION[4]:                        domain_name_servers = 64.253.208.121 208.118.192.121
DHCP4.OPTION[5]:                        expiry = 1691431255
DHCP4.OPTION[6]:                        ip_address = 192.168.1.14
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_domain_name = 1
DHCP4.OPTION[9]:                        requested_domain_name_servers = 1
DHCP4.OPTION[10]:                       requested_domain_search = 1
DHCP4.OPTION[11]:                       requested_host_name = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[14]:                       requested_nis_domain = 1
DHCP4.OPTION[15]:                       requested_nis_servers = 1
DHCP4.OPTION[16]:                       requested_ntp_servers = 1
DHCP4.OPTION[17]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[18]:                       requested_root_path = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       requested_subnet_mask = 1
DHCP4.OPTION[22]:                       requested_time_offset = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       routers = 192.168.1.1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::7314:458a:6cb3:10de/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1,/org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5fe38eb6-32e4-4800-9627-08158080d942 | Comtrend3930
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   43e0de62-4cc5-4796-b968-1cb1a5dc3da7 | CXNK010F18A3


GENERAL.DEVICE:                         p2p-dev-wlp1s0
GENERAL.TYPE:                           wifi-p2p
GENERAL.NM-TYPE:                        NMDeviceWifiP2P
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/6
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         (unknown)
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /virtual/device/placeholder/4
GENERAL.PATH:                           --
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     no
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID                BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
CXNK010F18A3        <MAC 'CXNK010F18A3' [AC1]>  Infra  1     2412 MHz  130 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no             
--                  <MAC '' [AC5]>  Infra  1     2412 MHz  130 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no             
CXNK010F18A3        <MAC 'CXNK010F18A3' [AC4]>  Infra  44    5220 MHz  540 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no             
--                  <MAC '' [AC6]>  Infra  44    5220 MHz  540 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no             
Comtrend3930        <MAC 'Comtrend3930' [AC3]>  Infra  6     2437 MHz  270 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     *      
Comtrend3930_2GEXT  <MAC 'Comtrend3930_2GEXT' [AC2]>  Infra  6     2437 MHz  130 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
Comtrend3930_5GEXT  <MAC 'Comtrend3930_5GEXT' [AN7]>  Infra  153   5765 MHz  270 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no             


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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com./


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Comtrend3930.nmconnection]] (600 root)
[connection] id=Comtrend3930 | type=wifi
[wifi] ssid=Comtrend3930
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CXNK010F18A3.nmconnection]] (600 root)
[connection] id=CXNK010F18A3 | type=wifi
[wifi] ssid=CXNK010F18A3
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


wlp1s0    32 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:5.22 GHz (Channel 44)


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'CXNK010F18A3' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"CXNK010F18A3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000098a44f45a6
                    Extra: Last beacon: 4912ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Comtrend3930_2GEXT' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Comtrend3930_2GEXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000098a4259b5f
                    Extra: Last beacon: 312ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Comtrend3930' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"Comtrend3930"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003af953b84fb
                    Extra: Last beacon: 328ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'CXNK010F18A3' [AC4]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"CXNK010F18A3"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000098a466f400
                    Extra: Last beacon: 3380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000098a44ffe2c
                    Extra: Last beacon: 4908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000098a46762c7
                    Extra: Last beacon: 3380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[mac80211]
filename:       /lib/modules/6.2.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/6.2.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


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


[ 9005.693062] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_fw.bin
[ 9005.693077] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_config.bin
[ 9009.435646] wlp1s0: authenticate with <MAC 'Comtrend3930' [AC3]>
[ 9009.542588] wlp1s0: send auth to <MAC 'Comtrend3930' [AC3]> (try 1/3)
[ 9009.545494] wlp1s0: authenticated
[ 9009.549462] wlp1s0: associate with <MAC 'Comtrend3930' [AC3]> (try 1/3)
[ 9009.556600] wlp1s0: RX AssocResp from <MAC 'Comtrend3930' [AC3]> (capab=0x411 status=0 aid=7)
[ 9009.669843] wlp1s0: associated
[ 9009.729456] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[10205.806158] wlp1s0: deauthenticating from <MAC 'Comtrend3930' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[10456.782830] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_fw.bin
[10456.782880] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_config.bin
[10460.519984] wlp1s0: authenticate with <MAC 'Comtrend3930' [AC3]>
[10460.630304] wlp1s0: send auth to <MAC 'Comtrend3930' [AC3]> (try 1/3)
[10460.632762] wlp1s0: authenticated
[10460.636629] wlp1s0: associate with <MAC 'Comtrend3930' [AC3]> (try 1/3)
[10460.648660] wlp1s0: RX AssocResp from <MAC 'Comtrend3930' [AC3]> (capab=0x411 status=0 aid=8)
[10460.760990] wlp1s0: associated
[10460.840717] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[11656.885731] wlp1s0: deauthenticating from <MAC 'Comtrend3930' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[23007.599165] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_fw.bin
[23007.599179] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_config.bin
[23011.382681] wlp1s0: authenticate with <MAC 'Comtrend3930' [AC3]>
[23011.494655] wlp1s0: send auth to <MAC 'Comtrend3930' [AC3]> (try 1/3)
[23011.497021] wlp1s0: authenticated
[23011.500404] wlp1s0: associate with <MAC 'Comtrend3930' [AC3]> (try 1/3)
[23011.504430] wlp1s0: RX AssocResp from <MAC 'Comtrend3930' [AC3]> (capab=0x411 status=0 aid=10)
[23011.616807] wlp1s0: associated
[23011.668616] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2023-08-08
Does it work better after ```
sudo iwconfig wlp1s0 power off
```

---

### Post by lwalper on 2023-08-10
Don't know if this info is useful?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292585&stc=1[/IMG]

---

### Post by lwalper on 2023-08-10
> **jeremy31 said:**
> Does it work better after ```
sudo iwconfig wlp1s0 power off
```
Ran that bit of code and didn't really notice any change. I have upgraded to 23.04 (which still has the 6.2 kernel) and have upgraded iy DSL to 300/300 fiber.
```
speedtest
Retrieving speedtest.net configuration...
Testing from DTC Communications (173.242.241.148)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by iRis Networks (Nashville, TN) [67.70 km]: 11.268 ms
Testing download speed................................................................................
Download: 97.32 Mbit/s
Testing upload speed......................................................................................................
Upload: 232.31 Mbit/s

```
Still inconsistent and nowhere near the 300/300 theoretical speeds.

---

### Post by morrownr on 2023-08-10
> **lwalper said:**
> 

Updating the kernel is a possibility. You have a guide for that process?


2023-02-05


Purpose: To test drivers on or with kernels beyond what
is currently included in the release versions of Ubuntu.


Upgrading the Linux Kernel on Ubuntu based amd64 systems


Note: Turn secure boot off before installing. These kernels
do not support secure boot.


You will need to make a directory to hold some downloaded
files, Since we are downloading a 6.1 kernel I use:


~/src/6.1


... anywhere in your home directory should work fine.


Go to:


[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)


Note: This guide is an example for kernel 6.1.9 Please
make adjustments for other kernels.


Download into a clean directory: (no other .deb files)


```
linux-headers-6.1.9-060109_6.1.9-060109.202302010835_all.deb
linux-headers-6.1.9-060109-generic_6.1.9-060109.202302010835_amd64.deb
linux-image-unsigned-6.1.9-060109-generic_6.1.9-060109.202302010835_amd64.deb
linux-modules-6.1.9-060109-generic_6.1.9-060109.202302010835_amd64.deb
```


----


To install:


```
sudo dpkg -i *.deb
```


Once the installation is finished, reboot.


You can use grub during boot to decide which kernel to boot. The
default is the most modern kernel installed.


-----


To remove:


Note: To remove a kernel you installed this way, you will
need to boot the computer to a different kernel.


```
sudo apt remove linux-headers-6.1.9*
```


```
sudo apt remove linux-modules-6.1.9*
```


```
sudo apt remove linux-image-unsigned-6.1.9*
```


Note: Once complete, reboot and the default kernel will now be
the most modern kernel still on your system. To select another
kernel version to boot, use the grub menu.

---

### Post by lwalper on 2023-08-11
OK, thanks. I'll give it a try.

---

