---
title: "Broadcom W-Lan Driver Problems"
date: 2015-11-10
forum: Networking &amp; Wireless
---

### Post by pascal14 on 2015-11-10
Hey,

First I want to say I'm German, so sorry for bad spelling.

I'm new on Linux as Desktop OS, so I does not know a lot, only a few things, so I'm sorry if I not understand a tip to solve the problem :D

My Problem:

I have setup Ubuntu as Dualboot a few days earlier, I have no problems with any driver expect my W-Lan Driver.
I have a Lenovo G710 Laptop.
[U]
What for a W-Lan Card is build in in my Laptop?[/U]
The *lspci* output says:
```
07:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
```

The *lspci -vnn | grep Network* output says:
```
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```

_What is the problem?_
The problem is not that I can't connect to the W-Lan, the problem is that my Internet connection breaks after a few time.
The connection does not break fully, it shows at the W-Lan Icon that I'm connected, but I can't load any Webpage or connect to a server (TS or another).
When I disable the wireless network fully over the W-Lan Icon and re-enable it I can use my Internet, but after a few time the connection breaks again.
Before the connection breaks I can see at the connection informations that the Mb/s speed is going down to 6-19Mb/s (but I can't use any kind of my Internet, like a full break of the connection)
When I use Windows or another Device with the router, it works without problems.
Nothing of the things I tested before creating this post worked, and I didn't found anything to my Network Card.

[U]What I did before I posted this thread?
[/U]I reinstalled the drivers *bcmwl-kernel-source* which comes with ubuntu (the drivers I currently used)
I testet the command listed on ubuntu's wiki: *'sudo iwconfig <interface> power off' *and set it in the /etc/rs.local

Best regards,
Pascal :D

---

### Post by slickymaster on 2015-11-10
Hi pascal14, welcome to the forums.

I moved your thread to the **Networking & Wireless** sub-forum, where luckily you have better chances of getting the proper help for your problem.

---

### Post by pascal14 on 2015-11-10
Ok, thanks for the Information :)

---

### Post by slickymaster on 2015-11-11
You can go ahead and download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Bucky Ball on 2015-11-11
Before the we go to the wireless script perhaps give the output of:

```
sudo lshw -C network
```

That will tell us what driver you currently have in there and some other details about wireless to start with. Might be something obvious there.

---

### Post by pascal14 on 2015-11-11
> **Bucky Ball said:**
> Before the we go to the wireless script perhaps give the output of:

```
sudo lshw -C network
```

That will tell us what driver you currently have in there and some other details about wireless to start with. Might be something obvious there.

The command returns the following:

```
  *-network               
       Beschreibung: Kabellose Verbindung
       Produkt: BCM43142 802.11b/g/n
       Hersteller: Broadcom Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:07:00.0
       Logischer Name: wlp7s0
       Version: 01
       Seriennummer: 48:5a:b6:e5:31:f7
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.0.110 latency=0 multicast=yes wireless=IEEE 802.11abg
       Ressourcen: irq:17 memory:d1500000-d1507fff
  *-network
       Beschreibung: Ethernet interface
       Produkt: QCA8172 Fast Ethernet
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:08:00.0
       Logischer Name: enp8s0
       Version: 10
       Seriennummer: 20:25:64:3c:03:67
       Kapazität: 100Mbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       Ressourcen: irq:33 memory:d1400000-d143ffff ioport:3000(Größe=128)
  *-network
       Beschreibung: Ethernet interface
       Physische ID: 1
       Logischer Name: enx023238575351
       Seriennummer: 02:32:38:57:53:51
       Fähigkeiten: ethernet physical
       Konfiguration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.115 link=yes multicast=yes
```

---

### Post by Bucky Ball on 2015-11-11
I see the BCM. Are the other two cable connections (can't read the language sorry, but suspecting they are). Are you running wireless with no cable plugged in? If you have an active ethernet cable plugged in, you can get odd results.

---

### Post by pascal14 on 2015-11-11
> **slickymaster said:**
> You can go ahead and download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

I've runned the script and attached the log file as tar.gz
[ATTACH]265493[/ATTACH]

---

### Post by pascal14 on 2015-11-11
I plugged in no Ethernet-Cable only a Smartphone with thetering to have a stable connection without timeouts, if it's recommended I redo the steps without the Tethering

---

### Post by pascal14 on 2015-11-11
I redid the Logs without have plugged in any other Cable or Tethering Device, only W-Lan was enabled.

The *sudo lshw -C network *Command gave out:

```
  *-network               
       Beschreibung: Kabellose Verbindung
       Produkt: BCM43142 802.11b/g/n
       Hersteller: Broadcom Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:07:00.0
       Logischer Name: wlp7s0
       Version: 01
       Seriennummer: 48:5a:b6:e5:31:f7
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.0.110 latency=0 multicast=yes wireless=IEEE 802.11abg
       Ressourcen: irq:17 memory:d1500000-d1507fff
  *-network
       Beschreibung: Ethernet interface
       Produkt: QCA8172 Fast Ethernet
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:08:00.0
       Logischer Name: enp8s0
       Version: 10
       Seriennummer: 20:25:64:3c:03:67
       Kapazität: 100Mbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       Ressourcen: irq:33 memory:d1400000-d143ffff ioport:3000(Größe=128)


```

And the Test Scipt: 
```

########## wireless info START ##########

Report from: 11 Nov 2015 17:26 CET +0100

Booted last: 11 Nov 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]
    Kernel driver in use: wl

08:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Qualcomm Atheros Device [1969:1090]
    Kernel driver in use: alx

##### lsusb #############################

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 004: ID 5986:0295 Acer, Inc 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 002: ID 04d9:a067 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: ideapad_3g: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              548864  1 wl
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0
video                  36864  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp8s0    Link encap:Ethernet  HWaddr <MAC 'enp8s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlp7s0    Link encap:Ethernet  HWaddr <MAC 'wlp7s0' [IF]>  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp7s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1454 errors:0 dropped:0 overruns:0 frame:1186
          TX packets:1554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:945347 (945.3 KB)  TX bytes:180845 (180.8 KB)
          Interrupt:17 

##### iwconfig ##########################

lo        no wireless extensions.

enp8s0    no wireless extensions.

wlp7s0    IEEE 802.11abg  ESSID:"dlinkZ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'dlinkZ' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp7s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp7s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       662     1  0 16:54 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlp7s0
GENERAL.IP-IFACE:                       wlp7s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     dlinkZ
GENERAL.CON-UUID:                       a610bb5a-2b61-4964-9672-8dd406b3b070
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     13 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a610bb5a-2b61-4964-9672-8dd406b3b070 | dlinkZ
IP4.ADDRESS[1]:                         192.168.0.110/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1447862544
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 604800
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.110
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
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp7s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8172 Fast Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
dlinkZ  <MAC 'dlinkZ' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/dlinkZ]] (600 root)
[connection] id=dlinkZ | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp7s0' [IF]> | mac-address-blacklist= | ssid=dlinkZ
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp8s0    no frequency information.

wlp7s0    32 channels in total; available frequencies :
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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp8s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlp7s0    Scan completed :
          Cell 01 - Address: <MAC 'dlinkZ' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"dlinkZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-18-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-18-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        93:AD:27:02:12:25:CE:1B:B4:86:5E:4B:AB:1E:2B:6A:5F:09:94:29
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

coretemp

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

iwconfig wlp7s0 power off

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  731.658177] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)

########## wireless info END ############


```

---

### Post by pascal14 on 2015-11-20
Anyone can help?
I like to use Ubuntu, but without WIFI it's not possible :(

---

### Post by kurt18947 on 2015-11-21
It looks like chili555 is on the forum. Praseodym is another guru and gives Berlin as a location. My wifi knowledge is limited to a few devices and no Broadcom so I can't help you, sorry.

---

### Post by pascal14 on 2015-11-27
> **kurt18947 said:**
> It looks like chili555 is on the forum. Praseodym is another guru and gives Berlin as a location. My wifi knowledge is limited to a few devices and no Broadcom so I can't help you, sorry.

Thanks for the reply, but there must be any driver or anything other out to use the Broadcom Card :(

NOTE: Tested ndiswarpper to check if the windows driver works, but does not worked :(

---

### Post by Hadaka on 2015-11-27
Hi, this dmesg error that you are getting..
```
[  731.658177] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)
```
is an indication that the driver "wl" is incorrect....that is not true,
Lets try a couple of things and see if it helps.
discconecrt any usb modules  or teathers...use only your wired solid connection.
please open a terminal ctrl/alt/t then COPY and paste one line at a time..
```
sudo apt-get update
echo "blacklist ideapad-laptop" | sudo tee -a blacklist.conf
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
next please access your router settings and remove the TKIP setting
and relpace it with WPA2 AES.
reboot and test wireless.
thanks.

---

### Post by pascal14 on 2015-11-29
> **Hadaka said:**
> Hi, this dmesg error that you are getting..
```
[  731.658177] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)
```
is an indication that the driver "wl" is incorrect....that is not true,
Lets try a couple of things and see if it helps.
discconecrt any usb modules  or teathers...use only your wired solid connection.
please open a terminal ctrl/alt/t then COPY and paste one line at a time..
```
sudo apt-get update
echo "blacklist ideapad-laptop" | sudo tee -a blacklist.conf
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
next please access your router settings and remove the TKIP setting
and relpace it with WPA2 AES.
reboot and test wireless.
thanks.

Have run the commands, the connection is currently working.
I will reply later in a few hours if the connection is working without problems or not (more testing)

The W-Lan settings of my router has been not changed, I have no access to them (only my parents)

Thanks for your help :)

---

### Post by pascal14 on 2015-11-30
Update:

After running the commands and rebooting from the introduction of @Hadaka the Internet worked as well.
But after ca. 2-3 hours the Internet started the crash a few times.
Now it's nearly like before running the commands... :(

---

### Post by Hadaka on 2015-11-30
Hi, please run those commands again,then disconnect the wired connection,
the ethernet. make sure you dont have any usb wifi or teathers connected.
then run and post the wireless script again. also, changing the TKIP setting
in the router will not affect the other devices that attach to it..cell,computers
whatever. so if you like,tell us the brand of your router and we will talk you
through changing it.
thanks.

---

