---
title: "gateway GWNC214H34-SL no wifi but bluetooth work"
date: 2024-03-26
forum: Networking &amp; Wireless
---

### Post by mr.thraz on 2024-03-26
[ATTACH=CONFIG]293539[/ATTACH]


OK, got a cheap gateway GWNC214H34-SL second hand for 20 bucks.

installed Ubuntu but i can't get the wifi working even thought the bluetooth does.

attached a device  image of it but i don't know if that's it or if it's picking up my wifi dongle.

i did ```
mrthraz@slim-gwnc214h34sl:~$ lspci
00:00.0 Host bridge: Intel Corporation Gemini Lake Host Bridge (rev 06)
00:00.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant (rev 06)
00:02.0 VGA compatible controller: Intel Corporation GeminiLake [UHD Graphics 600] (rev 06)
00:0e.0 Audio device: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio (rev 06)
00:0f.0 Communication controller: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface (rev 06)
00:12.0 SATA controller: Intel Corporation Celeron/Pentium Silver Processor SATA Controller (rev 06)
00:13.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.1 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.2 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:15.0 USB controller: Intel Corporation Celeron/Pentium Silver Processor USB 3.0 xHCI Controller (rev 06)
00:16.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 06)
00:16.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 06)
00:16.2 Signal processing controller: Intel Corporation Device 31b0 (rev 06)
00:16.3 Signal processing controller: Intel Corporation Device 31b2 (rev 06)
00:17.0 Signal processing controller: Intel Corporation Device 31b4 (rev 06)
00:17.1 Signal processing controller: Intel Corporation Device 31b6 (rev 06)
00:17.2 Signal processing controller: Intel Corporation Device 31b8 (rev 06)
00:17.3 Signal processing controller: Intel Corporation Device 31ba (rev 06)
00:18.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:18.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:18.2 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:18.3 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:19.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 06)
00:19.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 06)
00:19.2 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 06)
00:1c.0 SD Host controller: Intel Corporation Celeron/Pentium Silver Processor SDA Standard Compliant SD Host Controller (rev 06)
00:1f.0 ISA bridge: Intel Corporation Celeron/Pentium Silver Processor LPC Controller (rev 06)
00:1f.1 SMBus: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 06)

```


but can't make sense of it.


this is the device:  [https://www.target.com/p/gateway-14-1-34-laptop-intel-celeron-4gb-ram-128gb-storage-silver-gwnc214h34-sl/-/A-89423968?afid=google&ref=tgt_adv_xsf&CPNG=Electronics&adgroup=56-1](https://www.target.com/p/gateway-14-1-34-laptop-intel-celeron-4gb-ram-128gb-storage-silver-gwnc214h34-sl/-/A-89423968?afid=google&ref=tgt_adv_xsf&CPNG=Electronics&adgroup=56-1)

---

### Post by mr.thraz on 2024-03-27
ubuntu studio 22.04 btw

---

### Post by mr.thraz on 2024-03-27
anybody?

---

### Post by mr.thraz on 2024-03-30
hello?

---

### Post by jeremy31 on 2024-03-31
See the wireless script link in my signature and post results

---

### Post by mr.thraz on 2024-03-31
hope i did this right.

```

########## wireless info START ##########

Report from: 31 Mar 2024 11:26 CDT -0500

Booted last: 31 Mar 2024 00:00 CDT -0500

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.4 LTS
Release:	22.04
Codename:	jammy

##### kernel ############################

Linux 5.15.0-101-lowlatency #111-Ubuntu SMP PREEMPT Mon Mar 11 11:10:57 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, threadirqs, quiet, splash, vt.handoff=1

##### desktop ###########################

Plasma (X11)

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID ab20:1276 SunplusIT Inc PC Camera
Bus 001 Device 004: ID 0bda:d723 Realtek Semiconductor Corp. 802.11n WLAN Adapter
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

cfg80211              983040  0
r8188eu               688128  0

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
4: wlx<IF from MAC [IF1]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF1]>' [IF1]> brd <MAC address>
    inet 192.168.1.247/24 brd 192.168.1.255 scope global dynamic noprefixroute wlx<IF from MAC [IF1]>
       valid_lft 86396sec preferred_lft 86396sec
    inet6 2600:1702:4eb3:a2d0::3f/128 scope global dynamic noprefixroute 
       valid_lft 3595sec preferred_lft 3595sec
    inet6 2600:1702:4eb3:a2d0:cf0:517d:89eb:b6c6/64 scope global temporary dynamic 
       valid_lft 3596sec preferred_lft 3596sec
    inet6 2600:1702:4eb3:a2d0:2ca:2d07:d663:2d63/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3596sec preferred_lft 3596sec
    inet6 fe80::d945:ca4c:4ad7:d338/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  IEEE 802.11bgn  ESSID:"PWTMNB3"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'PWTMNB3' [AC5]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/100  Signal level=-58 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

default via 192.168.1.254 dev wlx<IF from MAC [IF1]> proto dhcp metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF1]> scope link metric 1000 
192.168.1.0/24 dev wlx<IF from MAC [IF1]> proto kernel scope link src 192.168.1.247 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search attlocal.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root         822       1  0 Mar30 ?        00:00:48 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/4
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8188EUS 802.11n Wireless Network Adapter
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 5.15.0-101-lowlatency
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               4 (full)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/usb1/1-5/1-5:1.0/net/wlx<IF from MAC [IF1]>
GENERAL.PATH:                           pci-0000:00:15.0-usb-0:5:1.0
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     PWTMNB3
GENERAL.CON-UUID:                       677416e5-34be-4037-a4e2-8a296c718654
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.ADDRESS[1]:                         192.168.1.247/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[3]:                        domain_name = attlocal.net
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        expiry = 1711988757
DHCP4.OPTION[6]:                        ip_address = 192.168.1.247
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
DHCP4.OPTION[24]:                       routers = 192.168.1.254
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2600:1702:4eb3:a2d0:cf0:517d:89eb:b6c6/64
IP6.ADDRESS[2]:                         2600:1702:4eb3:a2d0::3f/128
IP6.ADDRESS[3]:                         2600:1702:4eb3:a2d0:2ca:2d07:d663:2d63/64
IP6.ADDRESS[4]:                         fe80::d945:ca4c:4ad7:d338/64
IP6.GATEWAY:                            fe80::be9a:8eff:fe06:b701
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
IP6.ROUTE[2]:                           dst = 2600:1702:4eb3:a2d0::/64, nh = ::, mt = 600
IP6.ROUTE[3]:                           dst = 2600:1702:4eb3:a2d0::/60, nh = fe80::be9a:8eff:fe06:b701, mt = 600
IP6.ROUTE[4]:                           dst = ::/0, nh = fe80::be9a:8eff:fe06:b701, mt = 600
IP6.ROUTE[5]:                           dst = 2600:1702:4eb3:a2d0::3f/128, nh = ::, mt = 600
IP6.DNS[1]:                             2600:1702:4eb3:a2d0::1
IP6.SEARCHES[1]:                        attlocal.net
DHCP6.OPTION[1]:                        dhcp6_domain_search = attlocal.net
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2600:1702:4eb3:a2d0::1
DHCP6.OPTION[3]:                        ip6_address = 2600:1702:4eb3:a2d0::3f
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   677416e5-34be-4037-a4e2-8a296c718654 | PWTMNB3

SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
PWTMNB3                 <MAC 'PWTMNB3' [AC5]>  Infra  6     2437 MHz  16 Mbit/s  39      &#9602;&#9604;__  WPA2       yes     *      
Filimin_40F520388788    <MAC 'Filimin_40F520388788' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  0       ____  WPA2       no             
0497b2                  <MAC '0497b2' [AC1]>  Infra  1     2412 MHz  44 Mbit/s  0       ____  WPA1 WPA2  no             
ATTCTCth3A              <MAC 'ATTCTCth3A' [AC3]>  Infra  1     2412 MHz  16 Mbit/s  0       ____  WPA2       no             
ATT4Jdu3zq              <MAC 'ATT4Jdu3zq' [AC2]>  Infra  1     2412 MHz  16 Mbit/s  0       ____  WPA2       no             
MMSA                    <MAC 'MMSA' [AC6]>  Infra  5     2432 MHz  44 Mbit/s  0       ____  WPA2       no             
ATTIetZTxi              <MAC 'ATTIetZTxi' [AN7]>  Infra  5     2432 MHz  16 Mbit/s  0       ____  WPA2       no             
MyOptimum 1ff591        <MAC 'MyOptimum 1ff591' [AC4]>  Infra  5     2432 MHz  16 Mbit/s  0       ____  WPA2       no             
Nuke                    <MAC 'Nuke' [AC8]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  WPA2       no             
NTGR_VMB_1406851332     <MAC 'NTGR_VMB_1406851332' [AN10]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  WPA2       no             
ATTNABK6a2              <MAC 'ATTNABK6a2' [AC7]>  Infra  7     2442 MHz  16 Mbit/s  0       ____  WPA2       no             
ATTqZ8P93A              <MAC 'ATTqZ8P93A' [AC10]>  Infra  9     2452 MHz  16 Mbit/s  0       ____  WPA2       no             
ATTDGyDbub              <MAC 'ATTDGyDbub' [AC12]>  Infra  9     2452 MHz  16 Mbit/s  0       ____  WPA2       no             
winnies                 <MAC 'winnies' [AN14]>  Infra  10    2457 MHz  16 Mbit/s  0       ____  WPA2       no             
TP-Link_898D            <MAC 'TP-Link_898D' [AC9]>  Infra  10    2457 MHz  16 Mbit/s  0       ____  WPA1 WPA2  no             
--                      <MAC '' [AC11]>  Infra  10    2457 MHz  16 Mbit/s  0       ____  WPA2       no             
AT_301_WLRGL5825F_3035  <MAC 'AT_301_WLRGL5825F_3035' [AC13]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  WPA2       no             
Verizon_4C36TJ          <MAC 'Verizon_4C36TJ' [AC14]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  WPA2       no             
GoogleFiber             <MAC 'GoogleFiber' [AC15]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  WPA2       no             

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

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/PWTMNB3.nmconnection]] (600 root)
[connection] id=PWTMNB3 | type=wifi | permissions=user:mrthraz:;
[wifi] ssid=PWTMNB3
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

wlx<IF from MAC [IF1]>  13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC '0497b2' [AC1]>
                    ESSID:"0497b2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 02 - Address: <MAC 'ATT4Jdu3zq' [AC2]>
                    ESSID:"ATT4Jdu3zq"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 03 - Address: <MAC 'ATTCTCth3A' [AC3]>
                    ESSID:"ATTCTCth3A"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 04 - Address: <MAC 'MyOptimum 1ff591' [AC4]>
                    ESSID:"MyOptimum 1ff591"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 05 - Address: <MAC 'PWTMNB3' [AC5]>
                    ESSID:"PWTMNB3"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=59/100  
          Cell 06 - Address: <MAC 'MMSA' [AC6]>
                    ESSID:"MMSA"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 07 - Address: <MAC 'ATTNABK6a2' [AC7]>
                    ESSID:"ATTNABK6a2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 08 - Address: <MAC 'Nuke' [AC8]>
                    ESSID:"Nuke"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 09 - Address: <MAC 'TP-Link_898D' [AC9]>
                    ESSID:"TP-Link_898D"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 10 - Address: <MAC 'ATTqZ8P93A' [AC10]>
                    ESSID:"ATTqZ8P93A"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 11 - Address: <MAC '' [AC11]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 12 - Address: <MAC 'ATTDGyDbub' [AC12]>
                    ESSID:"ATTDGyDbub"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 13 - Address: <MAC 'AT_301_WLRGL5825F_3035' [AC13]>
                    ESSID:"AT_301_WLRGL5825F_3035"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:108 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 14 - Address: <MAC 'Verizon_4C36TJ' [AC14]>
                    ESSID:"Verizon_4C36TJ"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 15 - Address: <MAC 'GoogleFiber' [AC15]>
                    ESSID:"GoogleFiber"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.15.0-101-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-101-lowlatency SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8188eu]
filename:       /lib/modules/5.15.0-101-lowlatency/kernel/drivers/staging/r8188eu/r8188eu.ko
description:    Realtek Wireless Lan Driver
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       5.15.0-101-lowlatency SMP preempt mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_led_enable:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_led_enable: 1
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/dkms.conf]
blacklist rtw88_8821ce

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libhackrf0.conf]
blacklist hackrf

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[74069.449129] r8188eu 1-5:1.0 wlx<IF from MAC [IF1]>: renamed from wlan0
[74076.610262] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF1]>: link becomes ready
[74181.008472] r8188eu 1-5:1.0 wlx<IF from MAC [IF1]>: renamed from wlan0
[74185.649953] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF1]>: link becomes ready

########## wireless info END ############


```

---

### Post by mr.thraz on 2024-03-31
it only seemed to work with my dongle attached to get wifi access

---

### Post by jeremy31 on 2024-03-31
I take it you had a USB wifi device that you used to connect with?  For the one device, you will need to disable Secure Boot in BIOS settings, or you could update to the 6.5 kernel

---

### Post by mr.thraz on 2024-03-31
made sure secure boot was off and updated the kernel to 6.5.

still no ability to pick up the wifi from anything but this dongle.


```

########## wireless info START ##########

Report from: 31 Mar 2024 12:09 CDT -0500

Booted last: 31 Mar 2024 00:00 CDT -0500

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.4 LTS
Release:	22.04
Codename:	jammy

##### kernel ############################

Linux 5.15.0-101-lowlatency #111-Ubuntu SMP PREEMPT Mon Mar 11 11:10:57 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, threadirqs, quiet, splash, vt.handoff=1

##### desktop ###########################

Plasma (X11)

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID ab20:1276 SunplusIT Inc PC Camera
Bus 001 Device 003: ID 0bda:d723 Realtek Semiconductor Corp. 802.11n WLAN Adapter
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

cfg80211              983040  0
r8188eu               688128  0

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlx<IF from MAC [IF1]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF1]>' [IF1]> brd <MAC address>
    inet 192.168.1.247/24 brd 192.168.1.255 scope global dynamic noprefixroute wlx<IF from MAC [IF1]>
       valid_lft 86299sec preferred_lft 86299sec
    inet6 2600:1702:4eb3:a2d0::3f/128 scope global dynamic noprefixroute 
       valid_lft 3499sec preferred_lft 3499sec
    inet6 2600:1702:4eb3:a2d0:c28a:22a9:78c0:d6a5/64 scope global temporary dynamic 
       valid_lft 3499sec preferred_lft 3499sec
    inet6 2600:1702:4eb3:a2d0:2ca:2d07:d663:2d63/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3499sec preferred_lft 3499sec
    inet6 fe80::d945:ca4c:4ad7:d338/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  IEEE 802.11bgn  ESSID:"PWTMNB3"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'PWTMNB3' [AC1]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/100  Signal level=-62 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

default via 192.168.1.254 dev wlx<IF from MAC [IF1]> proto dhcp metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF1]> scope link metric 1000 
192.168.1.0/24 dev wlx<IF from MAC [IF1]> proto kernel scope link src 192.168.1.247 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search attlocal.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root         805       1  0 12:06 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8188EUS 802.11n Wireless Network Adapter
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 5.15.0-101-lowlatency
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               4 (full)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/usb1/1-4/1-4:1.0/net/wlx<IF from MAC [IF1]>
GENERAL.PATH:                           pci-0000:00:15.0-usb-0:4:1.0
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     PWTMNB3
GENERAL.CON-UUID:                       677416e5-34be-4037-a4e2-8a296c718654
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.ADDRESS[1]:                         192.168.1.247/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[3]:                        domain_name = attlocal.net
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        expiry = 1711991280
DHCP4.OPTION[6]:                        ip_address = 192.168.1.247
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
DHCP4.OPTION[24]:                       routers = 192.168.1.254
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2600:1702:4eb3:a2d0:c28a:22a9:78c0:d6a5/64
IP6.ADDRESS[2]:                         2600:1702:4eb3:a2d0::3f/128
IP6.ADDRESS[3]:                         2600:1702:4eb3:a2d0:2ca:2d07:d663:2d63/64
IP6.ADDRESS[4]:                         fe80::d945:ca4c:4ad7:d338/64
IP6.GATEWAY:                            fe80::be9a:8eff:fe06:b701
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
IP6.ROUTE[2]:                           dst = 2600:1702:4eb3:a2d0::/64, nh = ::, mt = 600
IP6.ROUTE[3]:                           dst = 2600:1702:4eb3:a2d0::/60, nh = fe80::be9a:8eff:fe06:b701, mt = 600
IP6.ROUTE[4]:                           dst = ::/0, nh = fe80::be9a:8eff:fe06:b701, mt = 600
IP6.ROUTE[5]:                           dst = 2600:1702:4eb3:a2d0::3f/128, nh = ::, mt = 600
IP6.DNS[1]:                             2600:1702:4eb3:a2d0::1
IP6.SEARCHES[1]:                        attlocal.net
DHCP6.OPTION[1]:                        dhcp6_domain_search = attlocal.net
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2600:1702:4eb3:a2d0::1
DHCP6.OPTION[3]:                        ip6_address = 2600:1702:4eb3:a2d0::3f
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   677416e5-34be-4037-a4e2-8a296c718654 | PWTMNB3

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
--                   <MAC '' [AC2]>  Infra  1     2412 MHz  44 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2       no             
PWTMNB3              <MAC 'PWTMNB3' [AC1]>  Infra  6     2437 MHz  16 Mbit/s  33      &#9602;&#9604;__  WPA2       yes     *      
ATTj96RumS           <MAC 'ATTj96RumS' [AC4]>  Infra  4     2427 MHz  16 Mbit/s  0       ____  WPA2       no             
MyOptimum 1ff591     <MAC 'MyOptimum 1ff591' [AC3]>  Infra  5     2432 MHz  16 Mbit/s  0       ____  WPA2       no             
ATTIetZTxi           <MAC 'ATTIetZTxi' [AC5]>  Infra  5     2432 MHz  16 Mbit/s  0       ____  WPA2       no             
Nuke                 <MAC 'Nuke' [AC6]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  WPA2       no             
NTGR_VMB_1406851332  <MAC 'NTGR_VMB_1406851332' [AC8]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  WPA2       no             
ATTNABK6a2           <MAC 'ATTNABK6a2' [AC7]>  Infra  7     2442 MHz  16 Mbit/s  0       ____  WPA2       no             
winnies              <MAC 'winnies' [AC9]>  Infra  10    2457 MHz  16 Mbit/s  0       ____  WPA2       no             
TP-Link_898D         <MAC 'TP-Link_898D' [AC11]>  Infra  10    2457 MHz  16 Mbit/s  0       ____  WPA1 WPA2  no             
--                   <MAC '' [AC10]>  Infra  10    2457 MHz  16 Mbit/s  0       ____  WPA2       no             

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

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/PWTMNB3.nmconnection]] (600 root)
[connection] id=PWTMNB3 | type=wifi | permissions=user:mrthraz:;
[wifi] ssid=PWTMNB3
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

wlx<IF from MAC [IF1]>  13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'PWTMNB3' [AC1]>
                    ESSID:"PWTMNB3"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=26/100  
          Cell 02 - Address: <MAC '' [AC2]>
                    ESSID:""
                    Protocol:IEEE 802.11gn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:108 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=58/100  
          Cell 03 - Address: <MAC 'MyOptimum 1ff591' [AC3]>
                    ESSID:"MyOptimum 1ff591"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 04 - Address: <MAC 'ATTj96RumS' [AC4]>
                    ESSID:"ATTj96RumS"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 05 - Address: <MAC 'ATTIetZTxi' [AC5]>
                    ESSID:"ATTIetZTxi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 06 - Address: <MAC 'Nuke' [AC6]>
                    ESSID:"Nuke"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 07 - Address: <MAC 'ATTNABK6a2' [AC7]>
                    ESSID:"ATTNABK6a2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 08 - Address: <MAC 'NTGR_VMB_1406851332' [AC8]>
                    ESSID:"NTGR_VMB_1406851332"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 09 - Address: <MAC 'winnies' [AC9]>
                    ESSID:"winnies"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 10 - Address: <MAC '' [AC10]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 11 - Address: <MAC 'TP-Link_898D' [AC11]>
                    ESSID:"TP-Link_898D"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 12 - Address: <MAC 'ATTCTCth3A' [AC12]>
                    ESSID:"ATTCTCth3A"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac028c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 13 - Address: <MAC 'AT_301_WLRGL5825F_3035' [AC13]>
                    ESSID:"AT_301_WLRGL5825F_3035"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:108 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 14 - Address: <MAC 'chaney' [AC14]>
                    ESSID:"chaney"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.15.0-101-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-101-lowlatency SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8188eu]
filename:       /lib/modules/5.15.0-101-lowlatency/kernel/drivers/staging/r8188eu/r8188eu.ko
description:    Realtek Wireless Lan Driver
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       5.15.0-101-lowlatency SMP preempt mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_led_enable:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_led_enable: 1
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/dkms.conf]
blacklist rtw88_8821ce

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libhackrf0.conf]
blacklist hackrf

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    6.059234] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723d_fw.bin
[    6.063962] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723d_config.bin
[   65.821779] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   65.899077] r8188eu 1-4:1.0 wlx<IF from MAC [IF1]>: renamed from wlan0
[   69.183073] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF1]>: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2024-03-31
You aren't using the 6.5 kernel yet, still booted to 5.15.0-101-lowlatency

---

### Post by mr.thraz on 2024-03-31
OMG thank you!

now connected natively. 


Is there a Low-latency version of this kernel?

you got a koffie or something?

---

### Post by jeremy31 on 2024-03-31
There appears to be a lowlatency version in the repos

---

