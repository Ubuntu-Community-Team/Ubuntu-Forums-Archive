---
title: "Help with wireless rtl8723be drivers and wifi connection"
date: 2016-06-09
forum: Networking &amp; Wireless
---

### Post by Matthew_Jonat on 2016-06-09
So I was having connection problems in linux only and then found this: [https://chirath02.wordpress.com/2016/05/12/installing-realtek-rtl8723be-driver-for-ubuntu-16-04/](https://chirath02.wordpress.com/2016/05/12/installing-realtek-rtl8723be-driver-for-ubuntu-16-04/)

I followed those instructions all the way through to the point where it says "If you are not able to see your wifi networks, follow the steps below" but if anything when I got to that point the wifi was even worse than before so i mentioned it to the author and he just said to continue all of the steps so stupidly I did and now I get no wifi connection at all although I can see access points but even when I boot into windows I cant even get a wifi connection there! Although I can see access points in windows aswell...
Basically I just need to undo this and reset if at all possible? If I were to download and re-install the drivers in windows would this fix the issue? If there is a terminal issue that can be solved in Linux I am open to that as well...

I am using ubuntu 16.04

Thanks!

Matt

---

### Post by Hadaka on 2016-06-09
Hi Matt, from a working wired connection please open a terminal  ctrl/alt/t
then Copy and paste one line at a time...
```
sudo apt-get install linux-headers-generic git dkms build-essential
rm -rf rtlwifi_new
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms build -m rtlwifi-new -v 0.6
sudo dkms install -m rtlwifi-new -v 0.6
```
disconnect your wired connection boot and test wireless,

*If you still have no wireless then,,,
Please open a terminal ctrl/alt/t then Copy and paste the following command
and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
Next.
From your directory please copy,paste and post the **wireless-info.txt**
thanks.

---

### Post by Matthew_Jonat on 2016-06-10
Thanks for the help!

Updates on progress...I entered all the commands line by line, rebooted and now i cant even see any wifi networks haha...im hoping this is a form of progress though?

Anyway output of wireless-info.txt:



```
########## wireless info START ##########


Report from: 10 Jun 2016 10:58 ICT +0700


Booted last: 10 Jun 2016 00:00 ICT +0700


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Foxconn WLAN Realtek Skyray RTL8723BE bgn 1x1
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:227e]


##### lsusb #############################


Bus 001 Device 004: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
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


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8723be             135168  0
btcoexist             180224  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1c3d:584c:3474:7bac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108509 (108.5 KB)  TX bytes:45417 (45.4 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
192.168.66.1    192.168.1.1     255.255.255.255 UGH   100    0        0 eno1


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       887     1  1 10:56 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
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
GENERAL.CON-UUID:                       183c7159-8f3f-4a31-9c9d-b92620f3c807
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   183c7159-8f3f-4a31-9c9d-b92620f3c807 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.128/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 192.168.66.1/32, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             202.58.98.202
IP4.DNS[2]:                             202.58.98.203
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.66.1
DHCP4.OPTION[10]:                       expiry = 1465559900
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 28800
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.128
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 202.58.98.202 202.58.98.203
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.66.1
IP6.ADDRESS[1]:                         fe80::1c3d:584c:3474:7bac/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
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
WIFI-PROPERTIES.AP:                     yes
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
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/NIKA'S Residence]] (600 root)
[connection] id=NIKA'S Residence | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=NIKA'S Residence
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NIKA'S Residence1]] (600 root)
[connection] id=NIKA'S Residence1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=NIKA'S Residence1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Panha-2]] (600 root)
[connection] id=Panha-2 | type=wifi | permissions=user:matthew:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Panha-2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AngkorHUB]] (600 root)
[connection] id=AngkorHUB | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=AngkorHUB
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GKO-WIRELESS]] (600 root)
[connection] id=GKO-WIRELESS | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=GKO-WIRELESS
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=user:matthew:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Matthew's iPhone]] (600 root)
[connection] id=Matthew's iPhone | type=wifi | permissions=user:matthew:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Matthew's iPhone
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Phnom_Penh (based on set time zone)


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


eno1      no frequency information.


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


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


wlo1      No scan results


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/4.4.0-24-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     00619764255210776FAB54D
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


[rtl_pci]
filename:       /lib/modules/4.4.0-24-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D4A9EE2656319D4E47FDF5B
depends:        mac80211,rtlwifi
vermagic:       4.4.0-24-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.4.0-24-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C87E9FBCC0C85BB3E3D9782
depends:        mac80211,cfg80211
vermagic:       4.4.0-24-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
ant_sel: 2
debug: 1
disable_watchdog: N
fwlps: Y
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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[   14.221720] rtlwifi: country code 11
[   14.312455] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.312952] rtlwifi: wireless switch is on
[   14.768184] rtl8723be 0000:08:00.0 wlo1: renamed from wlan0
[   16.814269] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   16.814285] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   46.451098] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[   48.046924] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   48.295347] r8169 0000:09:00.0 eno1: link down
[   48.295416] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   49.041473] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  103.741647] r8169 0000:09:00.0 eno1: link up
[  103.741656] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[  164.267720] NETDEV WATCHDOG: eno1 (r8169): transmit queue 0 timed out
[  164.286480] r8169 0000:09:00.0 eno1: link up


########## wireless info END ############
```


Thanks again!!

---

### Post by Matthew_Jonat on 2016-06-10
So after a few minutes of using the system (with a wired connection) Access points now do appear again but I still can not connect...

---

### Post by jojo11 on 2016-06-10
> **Matthew_Jonat said:**
> So after a few minutes of using the system (with a wired connection) Access points now do appear again but I still can not connect...  Hi, have the same problem with a HP 250 G2 AMD K6. Made same changes in 50-RTL8723be.conf. (options ant__sel=2, msi=1, flwps=0). Can see ap#s in ful strengt, but cannot connect to ap or internet. Is there a solution?? Many thanks in advance Jo

---

### Post by Hadaka on 2016-06-10
@ matt, please copy and paste one line at a time..
```
sudo iw reg set KH
sudo sed -i 's/^REG.*=$/&KH/' /etc/default/crda
```
then, check your network manager setting and also the Edit connections
and delete any connections with a "1" after them

@jojo11 please start your own thread 
thanks.

---

### Post by Matthew_Jonat on 2016-06-12
Hey I have done this now although still not able to connect.

When I go through my connections as instructed only 2 connections have a 1 after them, 1 a previous access point that had that name anyway and the other a wired connection "Wired Connection 1" Which I am currently using...I deleted the access point only...

I also assume a restart is required?

---

### Post by Hadaka on 2016-06-12
It would probably be better to delete all of them..,boot
then add your connection and password.

---

### Post by Matthew_Jonat on 2016-06-13
OK...thanks!

When I get a chance i'll reboot and then let you know how it goes!

---

### Post by jeremy31 on 2016-06-13
Matthew
Please post the output to ```
dkms status; lshw -c net
```
I think there might be a conflict

---

### Post by Matthew_Jonat on 2016-06-13
```
sudo dkms status; lshw -c net
rtlwifi-new, 0.10, 4.4.0-22-generic, x86_64: installed
rtlwifi-new, 0.10, 4.4.0-24-generic, x86_64: built
rtlwifi-new, 0.6, 4.4.0-24-generic, x86_64: installed
vboxhost, 5.0.20, 4.4.0-24-generic, x86_64: installed
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlo1
       version: 00
       serial: 74:29:af:92:ce:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:4000(size=256) memory:b2500000-b2503fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 08
       serial: 38:63:bb:a6:4d:75
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-2_0.0.1 04/23/13 ip=192.168.1.128 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:b2404000-b2404fff memory:b2400000-b2403fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```






...not sure why its saying that at the bottom? I ran as sudo?

Anyway...thanks for the continued help!

---

### Post by jeremy31 on 2016-06-13
Lets get rid of one dkms```
sudo apt-get remove rtlwifi-new-dkms
```
We can also add the parameter to disable power management for wifi ```
echo "options rtl8723be ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot
Have you tried ant_sel=1

The warning about using sudo is normal

---

### Post by Matthew_Jonat on 2016-06-13
Thanks...I'm still busy working although I have implemented the above...just dont have time to reboot right now haha...

In regards to the ant_sel=1 thing...a previous tutorial (i think i link to it in my OP) it asked me to change it to 2 and I think this is one of the things that affected my connection in windows as well as linux? (as in...not working in either) so im a bit reluctant to change that haha...I think its currently set to 0...what does this actually do?

---

### Post by Hadaka on 2016-06-13
Mathew, dont change any wifi settings in windows.
windows works when it is set to zero because the vendor of your wifi card
designed it to be controlled by windows software, not linux, so windows will
chose the best connection no matter what it is set to. Linux/Ubuntu usually
works best with "ANT sel =2" . That command is to select the antenna connection
there are 2 connections...1 & 2.  so do this.. First try 2...then boot...next test wifi...ubuntu and then windows
*If that does not work set it to .. 1      
X can be 0..1..2,  all you need to do is copy and paste, change the value of X

```
echo "options rtl8723be ant_sel=X" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```
thanks

@jeremy31..corrected..thanks.

---

### Post by jeremy31 on 2016-06-13
Hadaka, in his case he should use ```
echo "options rtl8723be ant_sel=X" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```

I am fairly sure the 50-rtl8723be.conf came from Larry Finger's github

I can't imagine this setting affecting windows but there is a chance the firmware it uses might cause an issue if you reboot into windows rather than a shutdown and a cold boot into windows

This is what I suggest doing to test this parameter


```

sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```

Then we check the second option to find which one works better

```

sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 is better

```

echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```
If ant_sel=2 is better
```

echo "options rtl8723be ant_sel=2" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

The iwlist scan command allows you to compare the number of access points detected and the signal strength for the 2 ant_sel options.

---

### Post by Matthew_Jonat on 2016-06-13
Ok....so firstly...thanks again for the help guys...I really appreciate it!

I noticed @hadakas most recent post before I noticed @jeremy31s...So I tried what @hadaka suggested, inserting the commands replacing X with 2 and then 1...unfortunately no change in linux and I still cant connect to anything...

I then noticed what @jeremy31 had posted...the commands are slightly different so thought I would go through them and test along the way...I got to the second command in the first block you sent: [COLOR=#000000][FONT=&quot]sudo modprobe rtl8723 ant_sel=1

[/FONT][/COLOR]Which returned: modprobe: FATAL: Module rtl8723 not found in directory /lib/modules/4.4.0-24-generic

Initially I thought this error might have come because you got me to uninstall something earlier in the thread but then I noticed in the second line [COLOR=#000000][FONT=&quot]rtl8723[/FONT][/COLOR] should be [COLOR=#000000][FONT=&quot]rtl8723be[/FONT][/COLOR] so I tried with that and it worked...is this correct?

The output of the first block of commands:

lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"AngkorHUB"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"GKO-WIRELESS"


Second block:

lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"GKO-WIRELESS"


FYI: I did not restart inbetween inputting these...should I have?

As far as determining which one is better I assume we are looking at quality and signal level? Both of which are the same although for some reason only one access point came up with [COLOR=#000000][FONT=&quot]ant_sel=2[/FONT][/COLOR] so im gonna go ahead and assume that [COLOR=#000000][FONT=&quot]ant_sel=1[/FONT][/COLOR] is the better? I'm about to input the last command: [COLOR=#000000][FONT=&quot]echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf[/FONT][/COLOR] and reboot...will report back here afterwards...

Thanks again!

---

### Post by Matthew_Jonat on 2016-06-13
So I just got back from the reboot...its all the same :( the wifi icon gives the animation as if to say its searching / connecting but nothing happens...sometimes it asks me for the wifi password again but it never connects...I am reverting back to ant_sel=0 by giving the following commands:

sudo modprobe -r rtl8723be
sudo modprobe rtl8723 ant_sel=0
echo "options rtl8723be ant_sel=0" | sudo tee -a /etc/modprobe.d/rtl8723be.conf

Let me know if you have any further suggestions or if im just ****ed haha...thanks again guys!

---

### Post by Matthew_Jonat on 2016-06-13
OK so this is interesting...I entered the above commands but did not reboot and just carried on using the wired connection and randomly a message popped up saying the wifi is connected but it only had 2 bars so I pulled out the LAN cable and it jumped to full...im sending this via a wifi connection now! 

Not sure what did it or if its properly fixed but I'll continue to use the wifi and report back any issues that come up...

Its more progress than I've had in a while so thanks a lot guys!

---

### Post by Matthew_Jonat on 2016-06-14
Just wanted to give an update...I still havent re-booted my machine since this morning but have been using the wifi incident free all day...so yeah...if anything its better than it was before!

Still really scared about what might happen after rebooting although if you dont hear from me after this...assume its all good!

Thanks again!

---

