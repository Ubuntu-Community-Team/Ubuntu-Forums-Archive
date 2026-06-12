---
title: "AR242x / AR542x Wireless Network Adapter - WIFI Not working"
date: 2021-04-24
forum: Networking &amp; Wireless
---

### Post by remece on 2021-04-24
Hello, thank you very much for the help you may have with my case.

I have installed Lubuntu on an old Notebook.
 -Toshiba Satellite L305-SP5920C

Everything is fine with the exception of WiFi.
Apparently it would be disconnected and I have not been able to activate it despite many hours of searching on the internet.

```
*-network DESACTIVADO
       descripción: Interfaz inalámbrica
       producto: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       fabricante: Qualcomm Atheros
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: wlp3s0
       versión: 01
       serie: 00:24:d2:06:89:ce
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=ath5k driverversion=4.15.0-142-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       recursos: irq:17 memoria:94600000-9460ffff

```

I would appreciate any help with this case.

Just as additional information, the same situation occurred to me after installing the Peppermint OS, in the same notebook of course. 

I am recovering this old notebook to be used by one of my children at school now that the classes are remote.

Best Regards,

Remece

---

### Post by guiverc on 2021-04-24
Providing full details of what Lubuntu you installed is always helpful. We currently don't know which desktop you're using (be it a *legacy* release which reaches EOL this month for Lubuntu support using LXDE), or a *modern* release using LXQt.  Further if it's a LTS release two stacks are available (GA or HWE) where the default is set by which ISO you install with.

I'll point you to [https://ubuntuforums.org/showthread.php?t=2180357](https://ubuntuforums.org/showthread.php?t=2180357) which maybe helpful.

Currently we don't know what software stack you're talking about (ie. release details are unknown).  I see a 4.15 so it's possibly you're using 18.04 with GA or a EOL release using HWE.  If it was a just installed Lubuntu 18.04 LTS system I'd expect it to be using the much later 5.4 kernel though.

---

### Post by remece on 2021-04-24
Thanks for your reply.

I apologize for my ignorance on the subject.
The version I downloaded to install was:

lubuntu-18.04-alternate-i386.iso

I will be grateful if you can point me to a better way to get that information.

Remece

---

### Post by remece on 2021-04-24
Hello, This is the result of the Link you posted.


```

########## wireless info START ##########

Report from: 24 Apr 2021 23:52 -03 -0300

Booted last: 24 Apr 2021 00:00 -03 -0300

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-142-generic #146-Ubuntu SMP Tue Apr 13 01:06:13 UTC 2021 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems RTL810xE PCI Express Fast Ethernet controller [1179:ff66]
    Kernel driver in use: r8169

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card [144f:7128]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

ath5k                 135168  0
ath                    24576  1 ath5k
mac80211              684032  1 ath5k
cfg80211              540672  3 mac80211,ath,ath5k
wmi                    20480  1 toshiba_acpi

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.0.111/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 82885sec preferred_lft 82885sec
    inet6 fe80::<IP6 'enp2s0' [IF1]>/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp3s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.0.1 dev enp2s0 proto dhcp metric 100 
192.168.0.0/24 dev enp2s0 proto kernel scope link src 192.168.0.111 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       461     1  0 18:23 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       e9e0d84b-f610-47f4-bcf4-55ed5c5378ad
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.111/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_domain_search = 1
DHCP4.OPTION[2]:                        dhcp_message_type = 5
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_netbios_scope = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        expiry = 1619402044
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.111
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.0.1 0.0.0.0
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF1]>/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f1fe11c6-a469-398f-a1f4-dda35d09fc75 | netplan-enp2s0
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   e9e0d84b-f610-47f4-bcf4-55ed5c5378ad | Wired connection 1

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.15.0-142-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

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
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-netcfg.yaml]
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: yes

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    13 channels in total; available frequencies :
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

##### iwlist scan #######################

wlp3s0    Interface doesn't support scanning : Network is down

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.15.0-142-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
depends:        mac80211,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath5k
vermagic:       4.15.0-142-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.15.0-142-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-142-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.15.0-142-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-142-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-142-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-142-generic SMP mod_unload modversions 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N

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

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 2675.004401] r8169 0000:02:00.0 enp2s0: link down
[ 2676.802435] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 2676.848113] r8169 0000:02:00.0 enp2s0: link down
[ 2676.848202] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 2676.851957] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2721.835933] r8169 0000:02:00.0 enp2s0: link up
[ 2721.835955] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 2756.185195] r8169 0000:02:00.0 enp2s0: link down
[ 2758.190059] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 2758.228185] r8169 0000:02:00.0 enp2s0: link down
[ 2758.228273] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 2758.231579] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2785.416587] r8169 0000:02:00.0 enp2s0: link up
[ 2785.416607] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 7986.512945] r8169 0000:02:00.0 enp2s0: link down
[ 7988.117634] r8169 0000:02:00.0 enp2s0: link up

########## wireless info END ############


```

I hope this information will help.

Thanks you

remece

---

### Post by remece on 2021-04-24
Please forget all messages.
Thank you very much for the help.

This old notebook has a physical switch to enable or disable the WiFi.

It's really embarrassing, I had to spend 2 days googling to finally get to this, which was right under my nose the whole time.

Thank you very much again and sorry for the inconvenience.

remece

---

### Post by guiverc on 2021-04-24
I'm glad it got solved for you :)  and no inconvenience at all.

It must be a lower-powered device, as the alternate ISO was for machines with <768MB of RAM (*700MB or less on some sites*) so I never used it.

All devices I used had 1GB (*or claimed 1GB even if only 732MB was actually usable*) so I never had need to use it.   I didn't start testing Lubuntu until after 18.04 had been released, and as that ISO was never re-spun, (*you'll have had to download all updates from 2018-April till now instead of installing them pre-updated by using 18.04.5 media*).  That ISO results in you using the GA kernel (ie. 4.15 as you said) where as 18.04.5 media would have resulted in HWE (5.4 kernel)

---

