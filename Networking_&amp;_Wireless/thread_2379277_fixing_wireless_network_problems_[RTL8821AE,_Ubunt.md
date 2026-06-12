---
title: "fixing wireless network problems [RTL8821AE, Ubuntu 16.04]"
date: 2017-12-03
forum: Networking &amp; Wireless
---

### Post by severin-kunz on 2017-12-03
Hi everyone, I am having some troubles with wifi on my laptop. I'm a beginner with Linux, so I may require some patience.

I've already posted on AskUbuntu, but people on there couldn't help me. This is the link to my post:
[https://askubuntu.com/questions/982481/wifi-cuts-out-after-a-while-on-asus-e202s?noredirect=1#comment1579949_982481](https://askubuntu.com/questions/982481/wifi-cuts-out-after-a-while-on-asus-e202s?noredirect=1#comment1579949_982481)

Right now, I can not connect to wifi at all anymore.
Before that, it disconnected after some time.

---

### Post by wildmanne39 on 2017-12-03
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by severin-kunz on 2017-12-04
It can't find chmod

I tried this: [https://ubuntuforums.org/showthread.php?t=1963921](https://ubuntuforums.org/showthread.php?t=1963921)
And it doesn't work neither with typing chmod or /bin/chmod

---

### Post by severin-kunz on 2017-12-04
Alright, I had to execute it one by one, this is the result:

```
[COLOR=#000000][FONT=&quot]########## wireless info START ##########[/FONT][/COLOR]
Report from: 04 Dec 2017 11:37 CET +0100

Booted last: 04 Dec 2017 00:00 CET +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.10.0-40-generic #44~16.04.1-Ubuntu SMP Thu Nov 9 15:37:44 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: ASUSTeK Computer Inc. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1043:207f]
	Kernel modules: rtl8821ae

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b54b Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 2717:ff88  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mac80211              782336  0
cfg80211              602112  1 mac80211
video                  40960  3 asus_wmi,int3406_thermal,i915
wmi                    16384  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s20u2 Link encap:Ethernet  HWaddr <MAC 'enp0s20u2' [IF1]>  
          inet addr:192.168.42.181  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::8f87:2f05:a29a:55d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90169 (90.1 KB)  TX bytes:28625 (28.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30169 (30.1 KB)  TX bytes:30169 (30.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20u2  no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20u2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20u2
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20u2

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       790     1  0 11:14 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         MediaTek
GENERAL.PRODUCT:                        Redmi
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enp0s20u2
GENERAL.IP-IFACE:                       enp0s20u2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kabelnetzwerkverbindung 1
GENERAL.CON-UUID:                       9783b593-4440-3e69-b97c-2a96b1742fb1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9783b593-4440-3e69-b97c-2a96b1742fb1 | Kabelnetzwerkverbindung 1
IP4.ADDRESS[1]:                         192.168.42.181/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.181
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1512387255
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = kunzseverin
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::8f87:2f05:a29a:55d1/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_AC_C1_EE_87_98_26
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1ee79f88-5fa4-40bb-985d-48928367e5ac | Redmi-Netzwerk

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

[[/etc/NetworkManager/system-connections/TP-LINK_22DC]] (600 root)
[connection] id=TP-LINK_22DC | type=wifi | permissions=user:kunzseverin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_22DC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sigh Nish So Lau]] (600 root)
[connection] id=Sigh Nish So Lau | type=wifi | permissions=user:kunzseverin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Sigh Nish So Lau
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi 1]] (600 root)
[connection] id=Redmi 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZHAW]] (600 root)
[connection] id=ZHAW | type=wifi | permissions=user:kunzseverin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ZHAW
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Zurich (based on set time zone)

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

enp0s20u2  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s20u2  Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.10.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-40-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-40-generic SMP mod_unload 
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae fwlps=N

##### rc.local ##########################

echo 6000 > /sys/class/backlight/intel_backlight/brightness

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.542687] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   13.542691] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_config.bin
[   13.658665] bluetooth hci0: Direct firmware load for rtl_bt/rtl8821a_config.bin failed with error -2
[   13.658672] Bluetooth: hci0: Failed to load rtl_bt/rtl8821a_config.bin
[   13.658678] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   15.627591] rndis_host 1-2:1.0 enp0s20u2: renamed from usb0
[   29.325792] IPv6: ADDRCONF(NETDEV_UP): enp0s20u2: link is not ready
[ 1186.784200] rndis_host 1-2:1.0 enp0s20u2: unregister 'rndis_host' usb-0000:00:14.0-2, RNDIS device
[ 1187.443202] rndis_host 1-2:1.0 enp0s20u2: renamed from usb0
[ 1187.500972] IPv6: ADDRCONF(NETDEV_UP): enp0s20u2: link is not ready

########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-12-04
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2017-12-04
To run the script you run the following command all at once, it is all one command and I have not seen it fail in over 5 years so I hope it did not start now.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
Copy and paste all commands for accuracy, please run:
```
sudo modprobe rtl8821ae
```
Does the wifi come on? can you connect? if not was there output from that command? if so please post it here.
and run:
```
lsmod | grep rtl8821
```
post the results.

Thanks

---

### Post by severin-kunz on 2017-12-05
Thank you very much for your help.

This is the result:

```
$ sudo modprobe rtl8821ae
modprobe: ERROR: could not insert 'rtl8821ae': Required key not available
```

---

### Post by jeremy31 on 2017-12-05
Go into BIOS/UEFI settings and disable secure boot

---

### Post by wildmanne39 on 2017-12-05
Let us know if you have an issue disabling secure boot.

---

### Post by severin-kunz on 2017-12-05
Thank you very much.

After I did the steps you suggested, it succesfully connected to the wireless network again and until now it didn't yet loose connection. I'll see what happens after more extensive use, but it already seems better than before, as it disconnected after around 3 websites before.

However, the issue right now is that it only lists 1 available network somehow. It's not an issue right now as it somehow shows the one I was connected to, but it's not something normal.

---

