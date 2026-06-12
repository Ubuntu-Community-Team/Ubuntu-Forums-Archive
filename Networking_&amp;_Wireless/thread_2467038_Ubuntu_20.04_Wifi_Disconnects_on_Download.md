---
title: "Ubuntu 20.04 Wifi Disconnects on Download"
date: 2021-09-14
forum: Networking &amp; Wireless
---

### Post by konoza on 2021-09-14
Hello,

I have an issue with my wifi. When browsing the internet, like through firefox there is no problem I stay connected and continue forever like that. However, If i start a download(like a  1gb file) or try to do an apt-update, the wifi will disconnect within 5 minutes of beginning the download. The wireless adapter i am using is quite old, but there is nothing wrong with as I also use it in dual boot windows with no issues. I have run wireless script, would appreciate any help.

---

### Post by chili555 on 2021-09-14
I'm very confused. Your wireless info shows NO wireless device at all; only an ethernet device.

The loaded kernel modules include rt2800pci, a well known driver for PCI devices.

Your logs show a wireless interface wlx-something, where the wlx means, generally, WireLesseXternal, usually a USB wireless device, although none is shown in lsusb.

We also wonder why a wireless interface is shown but it won't scan.

What kind of quite old wireless adapter is this, exactly? If it is PCMCIA, then this is your lucky day as the only person here old enough to know anything about PCMCIA is me.

:confused::confused:

---

### Post by morrownr on 2021-09-14
> **chili555 said:**
> 

What kind of quite old wireless adapter is this, exactly? If it is PCMCIA, then this is your lucky day as the only person here old enough to know anything about PCMCIA is me.

:confused::confused:

Chili555, don't bet on yourself being the only one here old enough to know about pcmcia.

However, my bet is on this:

ID 148f:2870 Ralink Technology, Corp. RT2870 Wireless Adapter

I suspect maybe a little corrosion or dust in a usb port. I think the OP should get a can of air and dust some ports and the adapter out and maybe put the usb wifi adapter back into a different port than it was in.

That little Ralink adapter is an 80211n device so it is modern and useful. If I have to, I will turn on my IBM PC that pre-dates USB. Heck, it pre-dates CD_ROM. Runs good. You should see MS Flight Sim 5.1 on it.

---

### Post by konoza on 2021-09-14
Hi chilli, I was confused when to run the script. This is it when the internet is working fine.

```

########## wireless info START ##########

Report from: 14 Sep 2021 10:30 CAT +0200

Booted last: 14 Sep 2021 00:00 CAT +0200

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.11.0-34-generic #36~20.04.1-Ubuntu SMP Fri Aug 27 08:06:32 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: Hewlett-Packard Company 82579LM Gigabit Network Connection (Lewisville) [103c:339a]

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 036: ID 050d:935a Belkin Components F6D4050 N150 Enhanced Wireless Network Adapter v1000 [Ralink RT3070]
Bus 001 Device 004: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 003: ID 046d:0819 Logitech, Inc. Webcam C210
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

rt2800pci              16384  0
rt2800mmio             24576  1 rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
eeprom_93cx6           16384  1 rt2800pci
rt2800usb              32768  0
rt2x00usb              24576  1 rt2800usb
rt2800lib             131072  3 rt2800usb,rt2800mmio,rt2800pci
rt2x00lib              65536  7 rt2800usb,rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2x00usb,rt2800lib
mac80211             1024000  4 rt2x00pci,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              888832  2 rt2x00lib,mac80211
libarc4                16384  1 mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
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
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp0s25
5: wlx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 10.0.0.9/24 brd 10.0.0.255 scope global dynamic noprefixroute wlx<IF from MAC [IF2]>
       valid_lft 85718sec preferred_lft 85718sec
    inet6 fe80::f48b:3982:644d:5dd2/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:"ROMANBABY"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'ROMANBABY' [AC1]>   
          Bit Rate=13 Mb/s   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:82  Invalid misc:278   Missed beacon:0

##### route #############################

default via 10.0.0.2 dev wlx<IF from MAC [IF2]> proto dhcp metric 600 
10.0.0.0/24 dev wlx<IF from MAC [IF2]> proto kernel scope link src 10.0.0.9 metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF2]> scope link metric 1000 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad

##### network managers ##################

Installed:

    NetworkManager

Running:

root       10717       1  0 10:18 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Belkin Components
GENERAL.PRODUCT:                        F6D4050 N150 Enhanced Wireless Network Adapter v1000 [Ralink RT3070]
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 5.11.0-34-generic
GENERAL.FIRMWARE-VERSION:               0.22
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               4 (full)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ROMANBABY
GENERAL.CON-UUID:                       65190330-4306-44eb-befa-fa9ea4a19f63
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     13 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               yes
IP4.ADDRESS[1]:                         10.0.0.9/24
IP4.GATEWAY:                            10.0.0.2
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.0.0.2, mt = 600
IP4.ROUTE[2]:                           dst = 10.0.0.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.0.2
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        domain_name_servers = 10.0.0.2
DHCP4.OPTION[3]:                        expiry = 1631693939
DHCP4.OPTION[4]:                        ip_address = 10.0.0.9
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_domain_name_servers = 1
DHCP4.OPTION[8]:                        requested_domain_search = 1
DHCP4.OPTION[9]:                        requested_host_name = 1
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[12]:                       requested_nis_domain = 1
DHCP4.OPTION[13]:                       requested_nis_servers = 1
DHCP4.OPTION[14]:                       requested_ntp_servers = 1
DHCP4.OPTION[15]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_root_path = 1
DHCP4.OPTION[17]:                       requested_routers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_subnet_mask = 1
DHCP4.OPTION[20]:                       requested_time_offset = 1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       routers = 10.0.0.2
DHCP4.OPTION[23]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::f48b:3982:644d:5dd2/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   65190330-4306-44eb-befa-fa9ea4a19f63 | ROMANBABY

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection (Lewisville)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 5.11.0-34-generic
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID       BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
ROMANBABY  <MAC 'ROMANBABY' [AC1]>  Infra  13    2472 MHz  130 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     *      
Verona     <MAC 'Verona' [AC2]>  Infra  12    2467 MHz  270 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 2

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
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ROMANBABY.nmconnection]] (600 root)
[connection] id=ROMANBABY | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=ROMANBABY
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Africa/Harare (based on set time zone)

global
country ZA: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 30), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.467 GHz (Channel 12)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'ROMANBABY' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ROMANBABY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000074e8f98f22
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Verona' [AC2]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Verona"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c809ade32d
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       5.11.0-34-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
depends:        rt2800lib,rt2x00lib,rt2x00mmio
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       5.11.0-34-generic SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       5.11.0-34-generic SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       5.11.0-34-generic SMP mod_unload modversions 

[rt2800usb]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
description:    Ralink RT2800 USB Wireless LAN driver.
depends:        rt2x00lib,rt2800lib,rt2x00usb
retpoline:      Y
intree:         Y
name:           rt2800usb
vermagic:       5.11.0-34-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00usb
vermagic:       5.11.0-34-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       5.11.0-34-generic SMP mod_unload modversions 
parm:           watchdog:Enable watchdog to detect tx/rx hangs and reset hardware if detected (bool)

[rt2x00lib]
filename:       /lib/modules/5.11.0-34-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       5.11.0-34-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/5.11.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.11.0-34-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.11.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.11.0-34-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: Y

[rt2800usb]
nohwcrypt: N

[rt2800lib]
watchdog: N

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci  nohwcrypt=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1896.786323] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[ 1896.814762] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 0005 detected
[ 1896.858502] rt2800usb 1-1.4:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[ 1896.890349] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 1896.890385] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.22
[ 1898.444204] wlx<IF from MAC [IF2]>: authenticate with <MAC 'ROMANBABY' [AC1]>
[ 1898.466852] wlx<IF from MAC [IF2]>: send auth to <MAC 'ROMANBABY' [AC1]> (try 1/3)
[ 1898.469941] wlx<IF from MAC [IF2]>: authenticated
[ 1898.470148] wlx<IF from MAC [IF2]>: associating with AP with corrupt probe response
[ 1898.471405] wlx<IF from MAC [IF2]>: associate with <MAC 'ROMANBABY' [AC1]> (try 1/3)
[ 1898.475163] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'ROMANBABY' [AC1]> (capab=0x411 status=0 aid=1)
[ 1898.481892] wlx<IF from MAC [IF2]>: associated
[ 1898.574183] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[ 2472.102818] wlx<IF from MAC [IF2]>: deauthenticating from <MAC 'ROMANBABY' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2474.716452] wlx<IF from MAC [IF2]>: authenticate with <MAC 'ROMANBABY' [AC1]>
[ 2474.794254] wlx<IF from MAC [IF2]>: send auth to <MAC 'ROMANBABY' [AC1]> (try 1/3)
[ 2474.795765] wlx<IF from MAC [IF2]>: authenticated
[ 2474.795926] wlx<IF from MAC [IF2]>: associating with AP with corrupt probe response
[ 2474.798961] wlx<IF from MAC [IF2]>: associate with <MAC 'ROMANBABY' [AC1]> (try 1/3)
[ 2474.805599] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'ROMANBABY' [AC1]> (capab=0x411 status=0 aid=1)
[ 2474.812348] wlx<IF from MAC [IF2]>: associated
[ 2474.912337] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############


```

While posting this, the wireless disconnected.
dmesg -w
```
[ 1452.266099] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.270313] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.274520] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.278767] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.283018] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.287269] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.291516] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.295765] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.300018] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.304275] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
[ 1452.513016] usb 1-1.4: USB disconnect, device number 5
[ 1453.128440] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1453.156450] wlx944452800367: deauthenticating from f0:b4:d2:07:2c:6d by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1453.472526] usb 1-1.4: new full-speed USB device number 7 using ehci-pci
[ 1453.556516] usb 1-1.4: device descriptor read/64, error -32
[ 1453.744548] usb 1-1.4: device descriptor read/64, error -32
```

syslog(editted this log <address>)
```
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.266099] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.270313] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.274520] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.278767] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.283018] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.287269] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.291516] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.295765] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.300018] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.304275] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71
Sep 15 05:35:44 za-HP-Compaq-Pro-6300-SFF kernel: [ 1452.513016] usb 1-1.4: USB disconnect, device number 5
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF kernel: [ 1453.128440] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF wpa_supplicant[866]: wlx944452800367: CTRL-EVENT-DISCONNECTED bssid=<address> reason=3 locally_generated=1
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <warn>  [1631676945.0452] sup-iface[0x55aa3dd71920,wlx944452800367]: connection disconnected (reason -3)
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF kernel: [ 1453.156450] wlx944452800367: deauthenticating from <address> by local choice (Reason: 3=DEAUTH_LEAVING)
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF avahi-daemon[842]: Interface wlx944452800367.IPv6 no longer relevant for mDNS.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF avahi-daemon[842]: Leaving mDNS multicast group on interface wlx944452800367.IPv6 with address fe80::f48b:3982:644d:5dd2.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF avahi-daemon[842]: Interface wlx944452800367.IPv4 no longer relevant for mDNS.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF avahi-daemon[842]: Leaving mDNS multicast group on interface wlx944452800367.IPv4 with address 10.0.0.9.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF avahi-daemon[842]: Withdrawing address record for fe80::f48b:3982:644d:5dd2 on wlx944452800367.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF avahi-daemon[842]: Withdrawing address record for 10.0.0.9 on wlx944452800367.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <info>  [1631676945.0779] device (wlx944452800367): state change: activated -> unmanaged (reason 'removed', sys-iface-state: 'removed')
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF whoopsie[1087]: [05:35:45] Cannot reach: https://daisy.ubuntu.com
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF whoopsie[1087]: [05:35:45] offline
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF systemd[1]: Starting Load/Save RF Kill Switch Status...
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <info>  [1631676945.1041] dhcp4 (wlx944452800367): canceled DHCP transaction
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <info>  [1631676945.1042] dhcp4 (wlx944452800367): state changed bound -> done
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF systemd[1]: Started Load/Save RF Kill Switch Status.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <info>  [1631676945.1274] manager: NetworkManager state is now DISCONNECTED
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF gnome-shell[1816]: An active wireless connection, in infrastructure mode, involves no access point?
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <info>  [1631676945.1338] radio killswitch /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/ieee80211/phy0/rfkill0 disappeared
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF dbus-daemon[845]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=846 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF NetworkManager[846]: <warn>  [1631676945.1340] dns-sd-resolved[cd5ed873aca85036]: send-updates failed to update systemd-resolved: GDBus.Error:org.freedesktop.resolve1.NoSuchLink: Link 3 not known
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF dbus-daemon[845]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF wpa_supplicant[866]: nl80211: deinit ifname=wlx944452800367 disabled_11b_rates=0
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF gnome-shell[1816]: JS WARNING: [resource:///org/gnome/shell/ui/status/network.js 1213]: reference to undefined property "_strengthChangedId"
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF systemd[1]: Started Network Manager Script Dispatcher Service.
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF nm-dispatcher[5070]: run-parts: failed to stat component /etc/network/if-post-down.d/avahi-daemon: No such file or directory
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF kernel: [ 1453.472526] usb 1-1.4: new full-speed USB device number 7 using ehci-pci
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF kernel: [ 1453.556516] usb 1-1.4: device descriptor read/64, error -32
Sep 15 05:35:45 za-HP-Compaq-Pro-6300-SFF kernel: [ 1453.744548] usb 1-1.4: device descriptor read/64, error -32

```

@morrownr My computer has a few free usb ports, I normally plug the wirless usb into the front and have tried using the back ports also but no difference. Everything was working fine, I did some updates like installing virualbox and just standard apt update, and then from the 13-Sep it started bugging out. Also If I boot into windows, there no issues with adapter it runs perfect - i dont think its a hardware issue. I can see the dpkg logs, showing what was installed(but intrpretting them is beyond me)- would those help should I post them?

---

### Post by chili555 on 2021-09-15
Now we see the USB wireless device. My guess is that it was detached when the first wireless info was collected.

We do not need or want the rt2800pci driver loaded. Let's get rid of it:

```
sudo -i
rm /etc/modprobe.d/rt2800pci.conf
modprobe -r rt2800pci
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
```

Also, you have a needless conf file that we can remove:

```
rm /etc/modprobe.d/iwlwifi.conf
exit
```We notice this in your wireless info:

```
Cell 01 - Address: <MAC 'ROMANBABY' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ROMANBABY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000074e8f98f22
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

```
 sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11 or 13, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router.

This is very interesting in your log:
```
associating with AP with corrupt probe response
```I suspect that rebooting the router may help temporarily. I also suspect that replacing the router will fix it permanently.

---

### Post by konoza on 2021-09-16
Hi chili my internet seems much more stable, after applying the changes  you recommended. There are no more random disconnects as I observed  yesterday. Thank you for sharing your expertise to help me out 3>

---

### Post by konoza on 2021-09-24
After I applied the changes recommended by chili, my internet was very stable no issues. But then this morning I put my computer and the **** is happening again. 
```

$>grep "\ install\ " /var/log/dpkg.log
2021-09-23 11:37:59 install linux-modules-5.11.0-36-generic:amd64 <none> 5.11.0-36.40~20.04.1
2021-09-23 11:38:03 install linux-image-5.11.0-36-generic:amd64 <none> 5.11.0-36.40~20.04.1
2021-09-23 11:38:04 install linux-modules-extra-5.11.0-36-generic:amd64 <none> 5.11.0-36.40~20.04.1
2021-09-23 11:38:15 install linux-hwe-5.11-headers-5.11.0-36:all <none> 5.11.0-36.40~20.04.1
2021-09-23 11:38:23 install linux-headers-5.11.0-36-generic:amd64 <none> 5.11.0-36.40~20.04.1
2021-09-23 14:36:42 install openjdk-11-source:all <none> 11.0.11+9-0ubuntu2~20.04

```

---

### Post by chili555 on 2021-09-26
If you reboot the router by power-cycling it, does the stability improve? As I said above, I suspect the router:

> This is very interesting in your log:
Code:
associating with AP with corrupt probe response
I suspect that rebooting the router may help temporarily. I also suspect that replacing the router will fix it permanently.


---

