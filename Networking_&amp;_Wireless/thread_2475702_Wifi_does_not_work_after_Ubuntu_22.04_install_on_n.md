---
title: "Wifi does not work after Ubuntu 22.04 install on new computer"
date: 2022-06-05
forum: Networking &amp; Wireless
---

### Post by eddugo on 2022-06-05
Just installed Ubuntu 22.04 on a new HP 17-cn1053cl laptop.  Wifi worked fine during live distro, but after install it did not. 
I reinstalled network manager and it came on for a short time.  
I then entered the following: 
```
$ sudo lshw -C network
[sudo] password for ed: 
  *-generic DISABLED        
       description: Wireless interface
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: ff
       serial: b4:b5:b6:df:bf:57
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8821ce driverversion=5.15.0-35-generic firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
       resources: irq:148 ioport:3000(size=256) memory:54000000-5400ffff
```

Can this be enabled permanently?

Thank you

Ed

---

### Post by TheFu on 2022-06-05
Run an update/full-upgrade cycle.  I.e. apply all current patches.  That has helped others.
If that doesn't work, run the wireless-info script from the ubuntuforums github page and post the results here. Someone who can read that information will probably recognize the issue.

---

### Post by grahammechanical on 2022-06-06
> driver=rtw_8821ce driverversion=5.15.0-35-generic

That tells me that there is a driver installed. It could be that the WiFi adapter is disabled in the UEFI settings utility. Or, if you have Windows installed and the WiFi is turned off then Ubuntu is unable to turn it back on. This used to happen years ago. I do not know if it still happens. In System Setting WiFi there should be a master slider for the WiFi adapter other than the Airplane mode slider. Is the slider off?

Regards

---

### Post by eddugo on 2022-06-07
grahammechanical;
Thank you for the reply.  The Wifi worked during installation and shortly after.  it also works if I reinstall the network manager and if i do a update/upgrade, but it only lasts a few minutes then quits.  Right now I am stuck as my ISP Wifi is not working so I have to wait until it's fixed before I can look into UEFI settings.  Wifi is turned "ON".  There is no Windows installed as I chose to erase when i  installed 22.04, but I think it's strange - I still get GRUB with  a Windows option.  If I select Windows, it asks for the Windows recovery disk.

---

### Post by TheFu on 2022-06-07
Run
```
 sudo update-grub
```
I think that will remove Windows from the menu, but it might leave the recovery partition boot in the menu.

I take it you have chosen NOT to run the wireless-info script as suggested?

---

### Post by eddugo on 2022-06-08
TheFu;  I will be running the wireless script, but the wireless is out from my ISP so I haven't been working on it  that machine has no connection for wired network - been running it off USB WIfi adapter.  Wireless went out after a lightning storm - thought it was the router so i installed a new one - same thing - barely a signal.  Hard to contact Centurylink - this is a rural area and they are the only game in town.  Right now I can only use wired connection on my other machines.

---

### Post by TheFu on 2022-06-08
> **eddugo said:**
> TheFu;  I will be running the wireless script, but the wireless is out from my ISP so I haven't been working on it  that machine has no connection for wired network - been running it off USB WIfi adapter.  Wireless went out after a lightning storm - thought it was the router so i installed a new one - same thing - barely a signal.  Hard to contact Centurylink - this is a rural area and they are the only game in town.  Right now I can only use wired connection on my other machines.

The wireless-info script isn't just for wireless. It is for all networking between the computer and the router.  Could this be part of the confusion?
Also, it feels like you are mixing up a wireless connection from the home to the internet and wireless connection from the computer to the local router.  Those are 2 very different things.

Run the script if you want help.

---

### Post by ActionParsnip on 2022-06-08
If the system has a shortcut to enable / disable WiFi then press it. May help

---

### Post by eddugo on 2022-06-09
Here is the output from Github Wireless Info:

```
########## wireless info START ##########

Report from: 09 Jun 2022 06:24 EDT -0400

Booted last: 09 Jun 2022 00:00 EDT -0400

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy

##### kernel ############################

Linux 5.15.0-35-generic #36-Ubuntu SMP Sat May 21 02:24:07 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

0000:02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821] (rev ff)
	Kernel driver in use: rtw_8821ce
	Kernel modules: rtw88_8821ce

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05c8:03ef Cheng Uei Precision Industry Co., Ltd (Foxlink) HP True Vision HD Camera
Bus 001 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 005: ID 0bda:b00e Realtek Semiconductor Corp. Bluetooth Radio 
Bus 001 Device 002: ID 1c4f:0034 SiGma Micro XM102K Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

r8188eu               671744  0
mac80211             1228800  2 rtw88_pci,rtw88_core
cfg80211              958464  2 rtw88_core,mac80211
libarc4                16384  1 mac80211
hp_wmi                 20480  0
sparse_keymap          16384  1 hp_wmi
platform_profile       16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    32768  2 hp_wmi,wmi_bmof

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
    inet 192.168.0.44/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx<IF from MAC [IF1]>
       valid_lft 85853sec preferred_lft 85853sec
    inet6 fe80::2b60:6501:eb85:119f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  IEEE 802.11bgn  ESSID:"FBIVan07"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FBIVan07' [AC1]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-42 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.0.1 dev wlx<IF from MAC [IF1]> proto dhcp metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF1]> scope link metric 1000 
192.168.0.0/24 dev wlx<IF from MAC [IF1]> proto kernel scope link src 192.168.0.44 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search Home

##### network managers ##################

Installed:

	NetworkManager

Running:

root         784       1  0 06:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8188EUS 802.11n Wireless Network Adapter
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 5.15.0-35-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlx<IF from MAC [IF1]>
GENERAL.PATH:                           pci-0000:00:14.0-usb-0:2:1.0
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FBIVan07 1
GENERAL.CON-UUID:                       c6a905a5-36d7-4c88-b432-7708d18b91c4
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
IP4.ADDRESS[1]:                         192.168.0.44/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             205.171.3.26
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[3]:                        domain_name = Home
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.0.1 205.171.3.26
DHCP4.OPTION[5]:                        expiry = 1654856147
DHCP4.OPTION[6]:                        ip_address = 192.168.0.44
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
DHCP4.OPTION[24]:                       routers = 192.168.0.1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::2b60:6501:eb85:119f/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c6a905a5-36d7-4c88-b432-7708d18b91c4 | FBIVan07 1

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821CE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtw_8821ce
GENERAL.DRIVER-VERSION:                 5.15.0-35-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/net/wlp2s0
GENERAL.PATH:                           pci-0000:02:00.0
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
FBIVan07        <MAC 'FBIVan07' [AC1]>  Infra  1     2412 MHz  16 Mbit/s  93      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     *      
FBIVan07_2GEXT  <MAC 'FBIVan07_2GEXT' [AC2]>  Infra  1     2412 MHz  16 Mbit/s  0       ____  WPA1 WPA2  no             

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

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

[[/etc/NetworkManager/system-connections/FBIVan07.nmconnection]] (600 root)
[connection] id=FBIVan07 | type=wifi
[wifi] ssid=FBIVan07
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FBIVan07 1.nmconnection]] (600 root)
[connection] id=FBIVan07 1 | type=wifi
[wifi] ssid=FBIVan07
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/00-default-nm-renderer.yaml]
network:
  renderer: NetworkManager

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

wlx<IF from MAC [IF1]>  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'FBIVan07' [AC1]>
                    ESSID:"FBIVan07"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=32/100  
          Cell 02 - Address: <MAC 'FBIVan07_2GEXT' [AC2]>
                    ESSID:"FBIVan07_2GEXT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0

wlp2s0    No scan results

##### module infos ######################

[r8188eu]
filename:       /lib/modules/5.15.0-35-generic/kernel/drivers/staging/r8188eu/r8188eu.ko
description:    Realtek Wireless Lan Driver
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       5.15.0-35-generic SMP mod_unload modversions 
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

[mac80211]
filename:       /lib/modules/5.15.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.15.0-35-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.15.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-35-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/udev/rules.d/70-snap.network-manager.rules]
# network-manager
KERNEL=="rfkill", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="ppp", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="tty[a-zA-Z]*[0-9]*", TAG+="snap_network-manager_networkmanager"
TAG=="snap_network-manager_networkmanager", RUN+="/usr/lib/snapd/snap-device-helper $env{ACTION} snap_network-manager_networkmanager $devpath $major:$minor"

##### dmesg #############################

[  667.691865] CPU: 4 PID: 8498 Comm: iwlist Tainted: G        WC        5.15.0-35-generic #36-Ubuntu

########## wireless info END ############
```

---

### Post by slickymaster on 2022-06-09
*Thread moved to **Networking & Wireless**.*

@eddugo
Because output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand, [please use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). This will make the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by eddugo on 2022-06-09
Here it is again - sorry about all this. but this is an area I know nothing about


```

########## wireless info START ##########

Report from: 09 Jun 2022 06:24 EDT -0400

Booted last: 09 Jun 2022 00:00 EDT -0400

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy

##### kernel ############################

Linux 5.15.0-35-generic #36-Ubuntu SMP Sat May 21 02:24:07 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

0000:02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821] (rev ff)
	Kernel driver in use: rtw_8821ce
	Kernel modules: rtw88_8821ce

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05c8:03ef Cheng Uei Precision Industry Co., Ltd (Foxlink) HP True Vision HD Camera
Bus 001 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 005: ID 0bda:b00e Realtek Semiconductor Corp. Bluetooth Radio 
Bus 001 Device 002: ID 1c4f:0034 SiGma Micro XM102K Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

r8188eu               671744  0
mac80211             1228800  2 rtw88_pci,rtw88_core
cfg80211              958464  2 rtw88_core,mac80211
libarc4                16384  1 mac80211
hp_wmi                 20480  0
sparse_keymap          16384  1 hp_wmi
platform_profile       16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    32768  2 hp_wmi,wmi_bmof

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
    inet 192.168.0.44/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx<IF from MAC [IF1]>
       valid_lft 85853sec preferred_lft 85853sec
    inet6 fe80::2b60:6501:eb85:119f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  IEEE 802.11bgn  ESSID:"FBIVan07"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FBIVan07' [AC1]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-42 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.0.1 dev wlx<IF from MAC [IF1]> proto dhcp metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF1]> scope link metric 1000 
192.168.0.0/24 dev wlx<IF from MAC [IF1]> proto kernel scope link src 192.168.0.44 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search Home

##### network managers ##################

Installed:

	NetworkManager

Running:

root         784       1  0 06:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8188EUS 802.11n Wireless Network Adapter
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 5.15.0-35-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlx<IF from MAC [IF1]>
GENERAL.PATH:                           pci-0000:00:14.0-usb-0:2:1.0
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FBIVan07 1
GENERAL.CON-UUID:                       c6a905a5-36d7-4c88-b432-7708d18b91c4
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
IP4.ADDRESS[1]:                         192.168.0.44/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             205.171.3.26
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[3]:                        domain_name = Home
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.0.1 205.171.3.26
DHCP4.OPTION[5]:                        expiry = 1654856147
DHCP4.OPTION[6]:                        ip_address = 192.168.0.44
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
DHCP4.OPTION[24]:                       routers = 192.168.0.1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::2b60:6501:eb85:119f/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c6a905a5-36d7-4c88-b432-7708d18b91c4 | FBIVan07 1

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821CE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtw_8821ce
GENERAL.DRIVER-VERSION:                 5.15.0-35-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/0000:02:00.0/net/wlp2s0
GENERAL.PATH:                           pci-0000:02:00.0
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
FBIVan07        <MAC 'FBIVan07' [AC1]>  Infra  1     2412 MHz  16 Mbit/s  93      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     *      
FBIVan07_2GEXT  <MAC 'FBIVan07_2GEXT' [AC2]>  Infra  1     2412 MHz  16 Mbit/s  0       ____  WPA1 WPA2  no             

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

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

[[/etc/NetworkManager/system-connections/FBIVan07.nmconnection]] (600 root)
[connection] id=FBIVan07 | type=wifi
[wifi] ssid=FBIVan07
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FBIVan07 1.nmconnection]] (600 root)
[connection] id=FBIVan07 1 | type=wifi
[wifi] ssid=FBIVan07
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/00-default-nm-renderer.yaml]
network:
  renderer: NetworkManager

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

wlx<IF from MAC [IF1]>  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'FBIVan07' [AC1]>
                    ESSID:"FBIVan07"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=32/100  
          Cell 02 - Address: <MAC 'FBIVan07_2GEXT' [AC2]>
                    ESSID:"FBIVan07_2GEXT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie =dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0

wlp2s0    No scan results

##### module infos ######################

[r8188eu]
filename:       /lib/modules/5.15.0-35-generic/kernel/drivers/staging/r8188eu/r8188eu.ko
description:    Realtek Wireless Lan Driver
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       5.15.0-35-generic SMP mod_unload modversions 
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

[mac80211]
filename:       /lib/modules/5.15.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.15.0-35-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.15.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-35-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/udev/rules.d/70-snap.network-manager.rules]
# network-manager
KERNEL=="rfkill", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="ppp", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="tty[a-zA-Z]*[0-9]*", TAG+="snap_network-manager_networkmanager"
TAG=="snap_network-manager_networkmanager", RUN+="/usr/lib/snapd/snap-device-helper $env{ACTION} snap_network-manager_networkmanager $devpath $major:$minor"

##### dmesg #############################

[  667.691865] CPU: 4 PID: 8498 Comm: iwlist Tainted: G        WC        5.15.0-35-generic #36-Ubuntu

########## wireless info END ############

```

---

### Post by TheFu on 2022-06-09
Looks like there are 2 wifi adapters.  One if USB and the other is built in.  Disable the one you don't want to use as a starting point in the BIOS or simply unplug the USB adapter. Beginners should only use 1 network adapter.

One of the adapters appears to be getting DHCP settings from somewhere. By only having 1 network device, the confusion may end.

I don't use network manager or systemd-resolved, so I cannot help with those.  Hopefully, someone with wifi expertise will be able to help beyond the general stuff I've posted. Now they have some data to work with.

---

### Post by eddugo on 2022-06-09
The only way I can connect to the internet is using a USB Wifi adapter - this laptop has no ethernet connection.  If I remove the USB wifi adapter, the settings/wifi shows "no visable networks"

---

### Post by eddugo on 2022-06-09
I have an USB adapter coming Monday so I can run from wired connection to get a better output

---

### Post by TheFu on 2022-06-09
> **eddugo said:**
> The only way I can connect to the internet is using a USB Wifi adapter - this laptop has no ethernet connection.  If I remove the USB wifi adapter, the settings/wifi shows "no visable networks"

Ah.  I'm a little slow sometimes.  My laptop uses intel wifi, which "just works", but if I google for "RTL8821CE ubuntu 22.04" seems that you aren't alone.
If the Live-Boot flash environment works, you can boot into that, install the wifi-info script and find exactly which driver it uses, then install that in the full install version.  That's all I have as a guess for now.  The answers in the google results are less than great. [https://askubuntu.com/questions/1407357/rtl8821ce-driver-not-working-on-ubuntu-22-04](https://askubuntu.com/questions/1407357/rtl8821ce-driver-not-working-on-ubuntu-22-04) has some things to try.  Your setup is unlikely to be the same, but it a workable solution is there, and no other harm happens, fantastic.  
Removing the blacklist line for the driver would certainly be the first I checked out. If the driver for your wifi adapter is blacklisted, it certainly won't work.  I'm not seeing any wifi "rtw" blacklists here, but who knows what happened on your box?

Save the **lshw -C network** output for both the working driver and the non-working driver so the differences can be checked.  I'd save the information to a flash data drive or somewhere on my network storage in 2 different files, but there are lots of other ways. Just be certain to use different filenames.

There's a tool - **meld** - that makes comparing files easy, but diff, sdiff, and 50 others can be used too. Whatever works for you.  I think meld is the best program for this specific task on any platform in the world.

---

### Post by eddugo on 2022-06-10
TheFu;
Thank you and the others for all your work and suggestions.  I'll mark this solved and try some of the things to try above.  I have 2 other HP laptops running 22.04 that "just work" and after running the script on them, neither uses RTL8821CE.  I also saw that I am not alone.   Worst case here is that I will always have to use the USB adapter or a USB to ethernet adapter.

---

### Post by TheFu on 2022-06-10
> **eddugo said:**
> TheFu;
Thank you and the others for all your work and suggestions.  I'll mark this solved and try some of the things to try above.  I have 2 other HP laptops running 22.04 that "just work" and after running the script on them, neither uses RTL8821CE.  I also saw that I am not alone.   Worst case here is that I will always have to use the USB adapter or a USB to ethernet adapter.

It would be better NOT to mark this solved, until it actually is.  The community here uses that SOLVED tag when seeking solutions and when seeking to help.  You'll just raise hope for others and send the most qualified to actually help away in doing that.
I'd be surprised of the answer wasn't getting the correct, already available, driver to install or perhaps disabling some power settings in the driver config.

OTOH, if you do work through those ideas in that post and find one that works, it would really help others to know what worked in your situation. Please be specific.

---

### Post by eddugo on 2022-06-10
Ok, got it.  I changed it to unsolved

---

### Post by eddugo on 2022-06-11
ThFu;

Please look at these two outputs:

Ubuntu 22.04  Live session:
```

ubuntu@ubuntu:~$ sudo lshw -c network
  *-network                 
       description: Wireless interface
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: b4:b5:b6:df:bf:57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8821ce driverversion=5.15.0-25-generic firmware=N/A ip=192.168.0.47 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:149 ioport:3000(size=256) memory:54000000-5400ffff
ubuntu@ubuntu:~$ 

```

Installed version:

```

ed@ed-main1:~$ sudo lshw -c network
[sudo] password for ed: 
  *-generic                 
       description: Wireless interface
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: ff
       serial: b4:b5:b6:df:bf:57
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8821ce driverversion=5.15.0-37-generic firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
       resources: irq:148 ioport:3000(size=256) memory:54000000-5400ffff
  *-network
       description: Wireless interface
       physical id: 10
       bus info: usb@1:1.3
       logical name: wlx984827ebefb9
       serial: 98:48:27:eb:ef:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu driverversion=5.15.0-37-generic ip=192.168.0.44 multicast=yes wireless=IEEE 802.11bgn
ed@ed-main1:~$ 

```

looks like the installed version is 32 bit - could that be the reason it doesn't work?  If so, how can that be changed?
Thank you

---

### Post by TheFu on 2022-06-11
Compare the differences between the working and non-working adapter.  What's different?  I see a few things.  If it were me, I'd install the working version and tell APT to "hold" it, so it doesn't get updated.

You need to do the work.

---

### Post by eddugo on 2022-06-14
don't mind doing the work at all.  I installed  5.15.0-25 generic (driver in install files) as the wifi will stay on as long as the live session is running.  It will come on for a short period with update/upgrade and also if I update snaps.  After install, I thought it would then appear in Software/drivers tab - nope.  Is there a tutorial anywhere with instruction to install the driver.  I guess I ran out of Know-how.

---

### Post by TheFu on 2022-06-14
> **eddugo said:**
> don't mind doing the work at all.  I installed  5.15.0-25 generic (driver in install files) as the wifi will stay on as long as the live session is running.  It will come on for a short period with update/upgrade and also if I update snaps.  After install, I thought it would then appear in Software/drivers tab - nope.  Is there a tutorial anywhere with instruction to install the driver.  I guess I ran out of Know-how.

In post #15 above, I suggested a program to use.  Did you use it to compare the outputs and see all the differences?

BTW, Manually installed software (source --> compile --> install) doesn't show up in the package managers.

---

### Post by eddugo on 2022-10-08
After trying every fix i could find since June, even using USB WIFI adapters i finally got it working.  I bought several USB WIFI adapters and after a while, it quit recognising any of them.  I was so disgusted with this laptop that it nearly hit the recycle.  They I finally found Ubuntu mainline installer.  Downloaded it, upgraded to Kernel 6.0 and it works perfectly.  Also it is much faster.

---

