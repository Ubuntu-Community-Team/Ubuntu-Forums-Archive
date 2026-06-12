---
title: "[Ubuntu] Realtek Wireless issues"
date: 2016-10-31
forum: Networking &amp; Wireless
---

### Post by David_Distracto on 2016-10-31
I recently bought a Lenovo ideapad 110 that came with Windows. I wiped the harddrive and installed Ubuntu. From the beginning I had issues with the wifi. The wifi would see my network and connect with it, but after about 30 seconds or a minute, it would stop talking to the router. I couldn't ping anything on the web or even ping the router. It would just show connection time out, though it would still show formally connected to the router. I figured that Ubuntu just needed to update, so I plugged into a wired connection and installed all the updates. No dice. Same problem.

Then I googled around a bit and found that I was not the only person having issues with Realtek wifi cards. I read through this thread:

[http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-8723be-wireless-card-to-work](http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-8723be-wireless-card-to-work)

I followed the steps listed out in it (except I changed the name of the wifi card to my wifi card RTL8821AE rather than the 8723be). Now my computer doesn't seem to recognize the wifi card at all. I ran the wifi info app and will cut and paste the info below. Thank in advance for any help with this. I'm starting to get a bit frustrated.


```
########## wireless info START ##########

Report from: 31 Oct 2016 15:13 CDT -0500

Booted last: 31 Oct 2016 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
	Kernel modules: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:381e]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 5986:06b3 Acer, Inc 
Bus 002 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

mac80211              737280  0
cfg80211              565248  1 mac80211
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2601:2c2:c300:5af0:a31d:ba8:e596:d771/64 Scope:Global
          inet6 addr: 2601:2c2:c300:5af0:65fd:444:a3fb:b2f7/64 Scope:Global
          inet6 addr: fe80::dfd1:c228:ed44:d631/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1682738 (1.6 MB)  TX bytes:367480 (367.4 KB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.tx.comcast.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root       980     1  0 15:07 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7fd49846-5437-39d8-a3e7-b85aa0cbf281
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7fd49846-5437-39d8-a3e7-b85aa0cbf281 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.19/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.tx.comcast.net.
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 192.168.0.19
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = hsd1.tx.comcast.net.
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1478030870
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2601:2c2:c300:5af0:65fd:444:a3fb:b2f7/64
IP6.ADDRESS[2]:                         2601:2c2:c300:5af0:a31d:ba8:e596:d771/64
IP6.ADDRESS[3]:                         fe80::dfd1:c228:ed44:d631/64
IP6.GATEWAY:                            fe80::425d:82ff:fef2:5452
IP6.ROUTE[1]:                           dst = 2601:2c2:c300:5af0::/60, nh = fe80::425d:82ff:fef2:5452, mt = 100
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:f4:1c:9d:27:2c:8a:7c:2b:6f:c1:b8:13:59:1c:d2:6a

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

[[/etc/NetworkManager/system-connections/The 3rd one down]] (600 root)
[connection] id=The 3rd one down | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=The 3rd one down
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Buttercup]] (600 root)
[connection] id=Buttercup | type=wifi | permissions=user:furcas:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Buttercup
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae ant_sel=2

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   39.329388] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   39.329394] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   55.428275] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   55.761268] r8169 0000:02:00.0 enp2s0: link down
[   55.761358] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   55.767809] r8169 0000:02:00.0 enp2s0: link down
[   57.363606] r8169 0000:02:00.0 enp2s0: link up
[   57.363625] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2016-10-31
What is the exact result of the command:```
sudo modprobe rtl8821ae
```Also, we see this:> [/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae ant_sel=2Is ant_sel an available parameter in this driver?```
modinfo rtl8821ae
```If not, then you have requested something that is impossible to perform. You may as well remove the conf file:```
sudo rm /etc/modprobe.d/rtl8821ae.conf
```It is almost never productive to simply, "... except I changed the name of the wifi card to my wifi card RTL8821AE rather than the 8723be ..."

---

### Post by jeremy31 on 2016-10-31
I secure boot enabled in BIOS?  As that would cause this issue if you are using the driver from Pilot6(hanipouspilot) PPA as the new kernels enforce secure boot rules and that prevents unsigned modules from being loaded and most modules that aren't in the kernel are unsigned

---

### Post by David_Distracto on 2016-11-01
sudo modprobe rtl8821ae yields the following:

>modprobe: ERROR: could not insert 'rtl8821ae': Required key not available

"Is ant_sel an available parameter in this driver?"

I don't know how to go about answering this question. Where would I find this out.

"It is almost never productive to simply," 

I am not a smart man. I know just enough to really get myself in trouble and then not know how to fix it.

"is secure boot enabled in BIOS"

No, when I installed the above driver, it walked through a thing to turn it off.

---

### Post by chili555 on 2016-11-01
> modprobe: ERROR: could not insert 'rtl8821ae': Required key not availableThis suggests that secure boot* is* still enabled. Please double-check.

---

