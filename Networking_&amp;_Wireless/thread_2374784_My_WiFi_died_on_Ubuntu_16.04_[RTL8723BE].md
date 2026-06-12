---
title: "My WiFi died on Ubuntu 16.04 [RTL8723BE]"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by skime on 2017-10-19
[FONT=verdana]Hello. My WiFi card was working fine but after update of the OS it stopped showing the access points. I have Windows 10 on the same computer, it works fine, the same on Live Ubuntu...

WiFi info:

[/FONT]```


########## wireless info START ##########


Report from: 19 Oct 2017 10:01 CEST +0200


Booted last: 19 Oct 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2248]
    Kernel driver in use: r8169


09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b3c8 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
Bus 002 Device 003: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 3938:1080  
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
rtl8723be              90112  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              782336  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              602112  2 mac80211,rtlwifi
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0    Link encap:Ethernet  HWaddr <MAC 'enp8s0' [IF1]>  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9a66:4323:47dc:cf10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2498153 (2.4 MB)  TX bytes:92366 (92.3 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52812 (52.8 KB)  TX bytes:52812 (52.8 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       857     1  0 09:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       d5586003-9151-3db1-87f2-7c10d3d82642
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d5586003-9151-3db1-87f2-7c10d3d82642 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.28/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = skime
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1508486264
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.28
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::9a66:4323:47dc:cf10/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceGeneric
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.10.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              yes
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
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


[[/etc/NetworkManager/system-connections/GRC Advisory 2]] (600 root)
[connection] id=GRC Advisory 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=GRC Advisory 2
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


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


enp8s0    no frequency information.


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


enp8s0    Interface doesn't support scanning.


wlo1      Interface doesn't support scanning : Network is down


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     8A4042E8F447BFEE8F45BA5
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 
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
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


[rtl8723_common]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B06F4AE01E9561133D82E7E
depends:        
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 


[rtl_pci]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B93F82B28F7945C22514E4D
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     884DE3F31278351A45DA409
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
ant_sel: 2
debug: 0
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   18.481834] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   18.527438] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.527646] rtlwifi: rtlwifi: wireless switch is on
[   18.597251] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   18.597253] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   18.670421] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   18.670425] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   18.670429] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   19.192107] rtl8723be 0000:09:00.0 wlo1: renamed from wlan0
[   29.583020] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   29.628262] r8169 0000:08:00.0 enp8s0: link down
[   29.628322] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   81.867200] r8169 0000:08:00.0 enp8s0: link up
[   81.867210] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready


########## wireless info END ############



```

[FONT=verdana]I've tried: "[/FONT]sudo apt-get install --reinstall linux-image-extra-$(uname -r)" but there are some errors:
```

ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtlwifi-new-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.10.0-37-generic (x86_64)

W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915




```

[FONT=verdana]How to resolve this problem?
[/FONT]

---

### Post by jeremy31 on 2017-10-19
Where did you get the source code to build this driver?  It might not be needed with the 4.10 kernel

---

### Post by skime on 2017-10-19
Of course on one site where they gave advice to update the driver to newest version. How should I proceed?

---

### Post by jeremy31 on 2017-10-19
I would remove it but I can't give accurate instructions unless I know where this code came from

---

### Post by skime on 2017-10-20
I've tried many things but one of them was this: [https://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work](https://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work)
```

sudo rm /etc/modprobe.d/rtl8723be.conf
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms
```

---

### Post by jeremy31 on 2017-10-20
```
sudo apt-get remove rtlwifi-new-dkms
```
```
sudo rm /etc/modprobe.d/50-rtl8723be.conf
```
reboot and see what setting works better
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|level'
```
If ant_sel=1 has best results do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be-ant.conf
```
If ant_sel=2 has best results do
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be-ant.conf
```

---

### Post by skime on 2017-10-20
Okay, remove is done. Error after "[COLOR=#000000]sudo apt-get install --reinstall linux-image-extra-$(uname -r)[/COLOR]" is gone but WiFi still is not working:

```
skime@skime:~$ sudo modprobe -r rtl8723be[sudo] password for skime: 
skime@skime:~$ sudo modprobe rtl8723be ant_sel=1
skime@skime:~$ iwlist scan | egrep -i 'ssid|level'
lo        Interface doesn't support scanning.


wlo1      Failed to read scan data : Network is down


enp8s0    Interface doesn't support scanning.


skime@skime:~$ sudo modprobe -r rtl8723be
skime@skime:~$ sudo modprobe rtl8723be ant_sel=2
skime@skime:~$ iwlist scan | egrep -i 'ssid|level'
lo        Interface doesn't support scanning.


wlo1      Failed to read scan data : Network is down


enp8s0    Interface doesn't support scanning.


skime@skime:~$ 



```

Any ideas?

---

### Post by jeremy31 on 2017-10-20
Run the wireless script again and post results

---

### Post by skime on 2017-10-20
Actual results:

```


########## wireless info START ##########


Report from: 20 Oct 2017 13:51 CEST +0200


Booted last: 20 Oct 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2248]
	Kernel driver in use: r8169


09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: WLAN
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b3c8 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
Bus 002 Device 003: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 3938:1080  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8723be              90112  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              782336  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              602112  2 mac80211,rtlwifi
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0    Link encap:Ethernet  HWaddr <MAC 'enp8s0' [IF1]>  
          inet addr:172.16.10.45  Bcast:172.16.10.255  Mask:255.255.255.0
          inet6 addr: fe80::9a66:4323:47dc:cf10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39168869 (39.1 MB)  TX bytes:3616344 (3.6 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56552 (56.5 KB)  TX bytes:56552 (56.5 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.10.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
172.16.10.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       852     1  0 13:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       d5586003-9151-3db1-87f2-7c10d3d82642
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d5586003-9151-3db1-87f2-7c10d3d82642 | Wired connection 1
IP4.ADDRESS[1]:                         172.16.10.45/24
IP4.GATEWAY:                            172.16.10.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 172.16.10.1
DHCP4.OPTION[10]:                       expiry = 1508584209
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 172.16.10.45
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 172.16.10.1
DHCP4.OPTION[19]:                       broadcast_address = 172.16.10.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 172.16.10.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 172.16.10.1
IP6.ADDRESS[1]:                         fe80::9a66:4323:47dc:cf10/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceGeneric
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.10.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              yes
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
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


[[/etc/NetworkManager/system-connections/GRC Advisory 2]] (600 root)
[connection] id=GRC Advisory 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=GRC Advisory 2
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


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


enp8s0    no frequency information.


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


wlo1      Interface doesn't support scanning : Network is down


enp8s0    Interface doesn't support scanning.


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     8A4042E8F447BFEE8F45BA5
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 
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
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


[rtl8723_common]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B06F4AE01E9561133D82E7E
depends:        
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 


[rtl_pci]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B93F82B28F7945C22514E4D
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884DE3F31278351A45DA409
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-37-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
ant_sel: 0
debug: 0
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
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   19.326761] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   19.326763] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   19.526641] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   19.526645] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   19.526649] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   20.062438] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   20.066224] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.066428] rtlwifi: rtlwifi: wireless switch is on
[   20.087845] rtl8723be 0000:09:00.0 wlo1: renamed from wlan0
[   29.683266] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   29.969625] r8169 0000:08:00.0 enp8s0: link down (repeated 2 times)
[   29.969682] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   31.558639] r8169 0000:08:00.0 enp8s0: link up
[   31.558648] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2017-10-20
```
sudo ifconfig wl1 up
```
See if it scans then or gives an error

---

### Post by skime on 2017-10-20
You meant sudo ifconfig wlo1 up?

```
skime@skime:~$ sudo ifconfig wl1 up
[sudo] password for skime: 
wl1: ERROR while getting interface flags: No such device
skime@skime:~$ sudo ifconfig wlo1 up
skime@skime:~$ ifconfig
enp8s0    Link encap:Ethernet  HWaddr 64:51:06:a7:e5:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47688 (47.6 KB)  TX bytes:47688 (47.6 KB)


wlo1      Link encap:Ethernet  HWaddr 90:48:9a:94:5a:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


skime@skime:~$ iwlist scan | egrep -i 'ssid|level'
wlo1      Failed to read scan data : Network is down


lo        Interface doesn't support scanning.


enp8s0    Interface doesn't support scanning.




```

So there is no error... It don't react.

---

### Post by jeremy31 on 2017-10-20
Post results for ```
dkms status
```
Do you still have the ISO you installed Ubuntu with?  Try using it without reinstalling to see if 
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|level'
```
Makes any difference

---

### Post by praseodym on 2017-10-21
Try

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be_options.conf
```
Reboot. Or this one

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be_options.conf 
```
Reboot

---

### Post by skime on 2017-10-22
On Live Ubuntu WiFi is working but rtl8732be is not found, results:

Live Ubuntu:
```
ubuntu@ubuntu:~$ sudo modprobe -r rtl8732be
modprobe: FATAL: Module rtl8732be not found.
ubuntu@ubuntu:~$ sudo modprobe rtl8723be ant_sel=1
ubuntu@ubuntu:~$ iwlist scan | egrep -i 'ssid|level'
                    Quality=70/70  Signal level=-26 dBm  
                    ESSID:"GRC Advisory 2"
                    Quality=60/70  Signal level=-50 dBm  
                    ESSID:"Orange-E73C"
                    Quality=28/70  Signal level=-82 dBm  
                    ESSID:"studnia_internetu_bez_dna"
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"multimedia_Arkabar"
                    Quality=50/70  Signal level=-60 dBm  
                    ESSID:"FunBox2-17E7"
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"ammon"
                    Quality=54/70  Signal level=-56 dBm  
                    ESSID:"FunBox2-AC75"
                    Quality=56/70  Signal level=-54 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=40/70  Signal level=-70 dBm  
                    ESSID:"tiaco"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"NETIASPOT-755480"
enp8s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                    Quality=32/70  Signal level=-78 dBm  
                    ESSID:"coin"
ubuntu@ubuntu:~$ sudo modprobe -r rtl8732be
modprobe: FATAL: Module rtl8732be not found.
ubuntu@ubuntu:~$ sudo modprobe rtl8723be ant_sel=2
ubuntu@ubuntu:~$ iwlist scan | egrep -i 'ssid|level'
enp8s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                    Quality=70/70  Signal level=-24 dBm  
                    ESSID:"GRC Advisory 2"
                    Quality=60/70  Signal level=-50 dBm  
                    ESSID:"Orange-E73C"
                    Quality=52/70  Signal level=-58 dBm  
                    ESSID:"studnia_internetu_bez_dna"
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=30/70  Signal level=-80 dBm  
                    ESSID:"multimedia_Arkabar"
                    Quality=52/70  Signal level=-58 dBm  
                    ESSID:"FunBox2-17E7"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=40/70  Signal level=-70 dBm  
                    ESSID:"ammon"
                    Quality=56/70  Signal level=-54 dBm  
                    ESSID:"FunBox2-AC75"
                    Quality=56/70  Signal level=-54 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"WIFISIFI3"
                    Quality=30/70  Signal level=-80 dBm  
                    ESSID:"multimedia_kamczi"
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ifconfig
enp8s0    Link encap:Ethernet  HWaddr 64:51:06:a7:e5:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127685 (127.6 KB)  TX bytes:127685 (127.6 KB)

wlo1      Link encap:Ethernet  HWaddr 90:48:9a:94:5a:03  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::391a:357f:12a5:2864/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6547637 (6.5 MB)  TX bytes:622288 (622.2 KB)

ubuntu@ubuntu:~$ iwconfig
wlo1      IEEE 802.11  ESSID:"GRC Advisory 2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: AC:22:0B:7C:65:00   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

enp8s0    no wireless extensions.

lo        no wireless extensions.

ubuntu@ubuntu:~$ dkms status
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.3
Python version: 3.5.2 final 0
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


```

On installed Ubuntu:
```
$ dkms status
ndiswrapper, 1.60, 4.10.0-37-generic, x86_64: installed
ndiswrapper, 1.60, 4.10.0-38-generic, x86_64: installed
```

> echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be_options.conf
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be_options.confis not working.

---

### Post by jeremy31 on 2017-10-22
You had a typo in the first command
```
ubuntu@ubuntu:~$ sudo modprobe -r rtl8732be
```
is not correct it should be rtl8723be not rtl8732be

---

### Post by skime on 2017-10-22
Sorry for that.

Live Ubuntu from pendrive:
```
ubuntu@ubuntu:~$ sudo modprobe -r rtl8723be
ubuntu@ubuntu:~$ sudo modprobe rtl8723be ant_sel=1
ubuntu@ubuntu:~$ iwlist scan | egrep -i 'ssid|level'
enp8s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

ubuntu@ubuntu:~$ sudo modprobe -r rtl8723be
ubuntu@ubuntu:~$ sudo modprobe rtl8723be ant_sel=2
ubuntu@ubuntu:~$ iwlist scan | egrep -i 'ssid|level'
enp8s0    Interface doesn't support scanning.

                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"multimedia_Arkabar"
                    Quality=56/70  Signal level=-54 dBm  
                    ESSID:"Orange-E73C"
lo        Interface doesn't support scanning.

                    Quality=36/70  Signal level=-74 dBm  
                    ESSID:"studnia_internetu_bez_dna"
                    Quality=52/70  Signal level=-58 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=36/70  Signal level=-74 dBm  
                    ESSID:"NETIASPOT-755480"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"Asia13"
                    Quality=60/70  Signal level=-50 dBm  
                    ESSID:"FunBox2-AC75"
                    Quality=60/70  Signal level=-50 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=28/70  Signal level=-82 dBm  
                    ESSID:"coin"
                    Quality=70/70  Signal level=-28 dBm  
                    ESSID:"GRC Advisory 2"
                    Quality=36/70  Signal level=-74 dBm  
                    ESSID:"ammon"
                    Quality=40/70  Signal level=-70 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=28/70  Signal level=-82 dBm  
                    ESSID:"Darmowe_Orange_WiFi"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"tiaco"
                    Quality=40/70  Signal level=-70 dBm  
                    ESSID:"multimedia_kamczi"
                    Quality=40/70  Signal level=-70 dBm  
                    ESSID:"FunBox2-17E7"


```

---

### Post by skime on 2017-10-25
Do you have any further advice?

---

### Post by jeremy31 on 2017-10-25
On the HDD install see what we can find with ```
dmesg | grep rtl
```

---

### Post by skime on 2017-10-25
Result:
```
skime@skime:~$ dmesg | grep rtl
[   15.870091] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   15.870093] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   15.936585] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   15.936588] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   15.936592] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   19.384915] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   19.388473] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.388714] rtlwifi: rtlwifi: wireless switch is on
[   19.870192] rtl8723be 0000:09:00.0 wlo1: renamed from wlan0
```

---

### Post by jeremy31 on 2017-10-25
Nothing there to indicate an issue, perhaps ```
dmesg | grep wlo1
```

---

### Post by skime on 2017-10-25
The same as above:

```
skime@skime:~$ dmesg | grep wlo1
[   20.615856] rtl8723be 0000:09:00.0 wlo1: renamed from wlan0
```

---

### Post by jeremy31 on 2017-10-25
It might be wifi power management causing issues for you
```
 sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
echo "options rtl8723be ips=N" | sudo tee /etc/modprobe.d/rtl8723be-ips.conf
```
Reboot and see if it works and try these commands again to see if the ant_sel parameter halps any
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|level'
```

---

### Post by skime on 2017-10-26
Still not working...

---

### Post by jeremy31 on 2017-10-26
About the only thing I can think of is to make a backup of your install, then install Ubuntu again, replace Ubuntu with Ubuntu but don't allow it to format as this should keep your home folder intact.  The backup is just in case something goes wrong

---

### Post by skime on 2017-10-27
This is weird: I've reinstalled Ubuntu as you said, without formatting but it wouldn't help... 

Anyway I've formatted the drive and installed Ubuntu from start again. WiFi is working... It seems like there are no drivers for rtl8723be...

---

### Post by jeremy31 on 2017-10-27
I am not sure what happened as the script results showed kernel modules loaded but for some reason they didn't want to work, but we could find no reason why

---

