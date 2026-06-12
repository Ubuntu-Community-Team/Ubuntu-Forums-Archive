---
title: "HP Pavilion rtl8723be Not showing wifi at all."
date: 2018-05-28
forum: Networking &amp; Wireless
---

### Post by Matthew_Jonat on 2018-05-28
Hi guys,

So I have been through the internet and these forums and tried things to solve this but I think in doing so have probably made things a hell of a lot worse.

It started when I installed kubuntu, my wifi was there and I could connect but for about 5 minutes before things slowly just dissapeared (other visible wifi connections disappeared first and then the hotspot i was connected to would get weaker and weaker and then disappear altogether and then eventually the wifi option itself would disappear).

So I dug out my really long LAN cable and got to the internet to try and repair things.

One of the first things I found was to install drivers that I might not already have / didnt come with ubunutu...I cant remember where I got the drivers exactly but the name of the zip file is rtlwifi_new-rock.new_btcoex.zip if that helps anyway.

This did a whole load of nothing for me so the search continued.

I probably did a few things along the way but the most recent thing was to check the antenna selection and try switching that. This actually worked for me and I assumed the problem was fixed and havent touched my laptop again until today.

The command I ran was: sudo modprobe -v rtl8723be ant_sel=2 
changing the 2 for a 1 and vice versa to see what worked....2 is the one that worked initially.

I came back today but found out it wasnt working and found another site that basically said to try this...switching between 1 and 2 and then running iwlist scan | egrep -i 'ssid|quality'
and seeing if any changes happen....this is my output for both:

eno1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

iwconfig output:

eno1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

ip link show output:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 38:63:bb:a6:4d:75 brd ff:ff:ff:ff:ff:ff

To add insult to injury, I booted up windows today as well where there is normally no issues with this whatsoever and the wifi did work at first but then after about 15 minutes cut out and the access point was completely gone and I'm sure this has something to do with me messing with this in linux?

I'm a bit of a n00b when it comes to all of this and am not really entirely sure what I am doing when messing around with this stuff so any help would be greatly appreciated...or maybe I should just buy a new laptop haha.

Thanks!

---

### Post by jeremy31 on 2018-05-28
Go into the folder you extracted the rtlwifi_new-rock.new_btcoex.zip file to and open in terminal then ```
sudo make uninstall
```
Also check results for ```
dkms status
```
If you installed using dkms, that will need to be removed also with
```
sudo dkms remove rtlwifi-new/0.6 --all
```
Change the ant_sel to 2 and reboot

If you still have issues, see the wireless script link in my signature and post results

---

### Post by Matthew_Jonat on 2018-05-29
Hello...thanks for your reply!

I uninstalled the drivers, changed to ant_sel=2 and rebooted...I can now see the wifi and my access point but when I click connect it thinks about it and the access point then just dissapears.

I tried running dkms but the command was not found.

I ran the script...output here:

```
########## wireless info START ##########

Report from: 29 May 2018 10:19 BST +0100

Booted last: 29 May 2018 00:00 BST +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Plasma

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723] (rev ff)
	Kernel driver in use: rtl8723be
	Kernel modules: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)
	Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:227e]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723be              98304  0
btcoexist             131072  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
mac80211              778240  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              622592  2 mac80211,rtlwifi
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 wmi_bmof,hp_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.1.106/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 86221sec preferred_lft 86221sec
    inet6 fe80::99be:7660:b7a9:9e3e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlo1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlo1' [IF2]> brd <MAC address>

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.1.1 dev eno1 proto dhcp metric 100 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.106 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53
search mynet

##### network managers ##################

Installed:

	NetworkManager

Running:

root       825     1  0 10:14 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f9817f0f-effc-3557-8c37-231b42a46868
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.106/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          mynet
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       domain_name = mynet
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[14]:                       ip_address = 192.168.1.106
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_lease_time = 86400
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       dhcp_message_type = 5
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       expiry = 1527671798
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::99be:7660:b7a9:9e3e/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:6:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_info_refresh_time = 86400
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:11:5f:82:1c:12:3f:33:8c:71:33:f:bd:c9:99:11:f2
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f9817f0f-effc-3557-8c37-231b42a46868 | Wired connection 1

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.15.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a6135a81-ac3f-4e53-9f86-1d6abdb2c1a4 | 1D67 Hyperoptic 1Gbps Broadband

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/1D67 Hyperoptic 1Gbps Broadband]] (600 root)
[connection] id=1D67 Hyperoptic 1Gbps Broadband | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=1D67 Hyperoptic 1Gbps Broadband
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

wlo1      13 channels in total; available frequencies :
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

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlo1      No scan results

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     6A56582B1FEECB841E329C4
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
intree:         Y
name:           rtl8723be
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     90DB9C652E26F4135F339B8
depends:        rtlwifi
retpoline:      Y
intree:         Y
name:           rtl8723_common
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtl_pci]
filename:       /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9F5FA8A771710F4CA500C6E
depends:        mac80211,rtlwifi
retpoline:      Y
intree:         Y
name:           rtl_pci
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtlwifi]
filename:       /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8AB8B2AAF3BCFFB93D91956
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rtlwifi
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-22-generic SMP mod_unload 
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

[cfg80211]
filename:       /lib/modules/4.15.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 2
aspm: 1
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: N
ips: Y
msi: N
swenc: N
swlps: N

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

[/etc/modprobe.d/50-rtl8723be.conf]
options rtl8723be ant_sel=2

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

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0 swlps=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  170.766614] rtl8723be: error H2C cmd because of Fw download fail!!!
[  170.766639] WARNING: CPU: 3 PID: 831 at /build/linux-lZKWha/linux-4.15.0/drivers/net/wireless/realtek/rtlwifi/rtl8723be/fw.c:227 rtl8723be_fill_h2c_cmd+0x109/0x440 [rtl8723be]
[  170.766711] RIP: 0010:rtl8723be_fill_h2c_cmd+0x109/0x440 [rtl8723be]
[  170.766730]  ? rtl8723be_phy_set_rf_reg+0x92/0xb0 [rtl8723be]
[  170.766753]  rtl_btc_ips_notify+0x19/0x20 [btcoexist]
[  170.766757]  rtl_ips_nic_on+0xa6/0xc0 [rtlwifi]
[  170.766760]  rtl_op_config+0x1fc/0x440 [rtlwifi]
[  203.293489] rtl8723be: Init MAC failed (repeated 40 times)

########## wireless info END ############
```

---

### Post by jeremy31 on 2018-05-29
Lets try a different driver
```
sudo apt install git dkms
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Check ```
mokutil --sb-state
```
If it shows Secure Boot enabled you will need to change BIOS settings for this driver to load after a reboot

---

### Post by Matthew_Jonat on 2018-05-29
Secure boot is off...I followed these instructions and rebooted...I am back to seeing no wifi at all...not even the option to turn it on or off.

Really appreciate the help so far by the way!

---

### Post by jeremy31 on 2018-05-29
What happens if you ```
sudo modprobe -v rtl8723be
```

---

### Post by Matthew_Jonat on 2018-05-29
modprobe returns this:

insmod /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko 
modprobe: ERROR: could not insert 'rtl8723be': Unknown symbol in module, or unknown parameter (see dmesg)

I ran dmesg and the output was too much so I couldn't see it all and dont want to post it here as it may contain information I dont want to make public?

I did a quick scan though and there were 2 lines I found that might be relevant?

[   24.689160] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[   24.689186] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)

This was like half way through and then repeated right twice at the end.

---

### Post by jeremy31 on 2018-05-29
What about
```
cd rtlwifi_new
git status
```

---

### Post by Matthew_Jonat on 2018-05-30
On branch master
Your branch is up-to-date with 'origin/master'.


nothing to commit, working tree clean


.....if nothing has changed, does that mean I havent installed correctly?

---

### Post by jeremy31 on 2018-05-30
Any results for ```
ls /lib/firmware/rtlwifi
```

---

### Post by Matthew_Jonat on 2018-05-30
Realtek-Firmware-License.txt  rtl8192cufw_TMSC.bin     rtl8192sefw.old.bin      rtl8723bs_nic.bin        rtl8812aefw_wowlan.bin
rtl8188efw.bin                rtl8192defw_12.bin       rtl8712u.bin             rtl8723bs_wowlan.bin     rtl8821aefw_29.bin
rtl8188eufw.bin               rtl8192defw.bin          rtl8723aufw_A.bin        rtl8723bu_ap_wowlan.bin  rtl8821aefw.bin
rtl8192cfw.bin                rtl8192eefw.bin          rtl8723aufw_B.bin        rtl8723bu_nic.bin        rtl8821aefw_wowlan.bin
rtl8192cfwU_B.bin             rtl8192eefw_new.bin      rtl8723aufw_B_NoBT.bin   rtl8723bu_wowlan.bin     rtl8822befw.bin
rtl8192cfwU.bin               rtl8192eu_ap_wowlan.bin  rtl8723befw_36.bin       rtl8723defw.bin
rtl8192cufw_A.bin             rtl8192eu_nic.bin        rtl8723befw.bin          rtl8723fw_B.bin
rtl8192cufw_B.bin             rtl8192eu_wowlan.bin     rtl8723bs_ap_wowlan.bin  rtl8723fw.bin
rtl8192cufw.bin               rtl8192sefw.bin          rtl8723bs_bt.bin         rtl8812aefw.bin

---

### Post by Matthew_Jonat on 2018-05-30
```

Realtek-Firmware-License.txt  rtl8192cufw_TMSC.bin     rtl8192sefw.old.bin      rtl8723bs_nic.bin        rtl8812aefw_wowlan.bin
rtl8188efw.bin                rtl8192defw_12.bin       rtl8712u.bin             rtl8723bs_wowlan.bin     rtl8821aefw_29.bin
rtl8188eufw.bin               rtl8192defw.bin          rtl8723aufw_A.bin        rtl8723bu_ap_wowlan.bin  rtl8821aefw.bin
rtl8192cfw.bin                rtl8192eefw.bin          rtl8723aufw_B.bin        rtl8723bu_nic.bin        rtl8821aefw_wowlan.bin
rtl8192cfwU_B.bin             rtl8192eefw_new.bin      rtl8723aufw_B_NoBT.bin   rtl8723bu_wowlan.bin     rtl8822befw.bin
rtl8192cfwU.bin               rtl8192eu_ap_wowlan.bin  rtl8723befw_36.bin       rtl8723defw.bin
rtl8192cufw_A.bin             rtl8192eu_nic.bin        rtl8723befw.bin          rtl8723fw_B.bin
rtl8192cufw_B.bin             rtl8192eu_wowlan.bin     rtl8723bs_ap_wowlan.bin  rtl8723fw.bin
rtl8192cufw.bin               rtl8192sefw.bin          rtl8723bs_bt.bin         rtl8812aefw.bin

```

---

### Post by jeremy31 on 2018-05-31
Hi, I installed Ubuntu 18.04 on a spare laptop that I put a Realtek rtl8723be wifi chip in and I cannot duplicate your issue in the 4.15.0-22 kernel
I would go to [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) and file a bug against package linux

---

### Post by Matthew_Jonat on 2018-06-01
Wow...for a while there I thought you had just given up on me haha.

But you did not! Thanks for really going the extra mile!

Even though we couldn't resolve this I really appreciate your help.

Thanks again!

---

