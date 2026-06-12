---
title: "Ubuntu 18.04: Edimax EW-7611ULB WiFi/Bluetooth USB not working"
date: 2018-05-11
forum: Networking &amp; Wireless
---

### Post by Durabys on 2018-05-11
So. I just installed Ubuntu 18.04 on my PC desktop and set up everything and now I am hopelessly trying to make Ubuntu friend with the wireless USB dongle that worked on my Windows 7 before.

---

### Post by praseodym on 2018-05-11
Please run the wireless script from the sticky thread and show the outputs

---

### Post by Durabys on 2018-05-11
Here it is: [http://paste.ubuntu.com/p/Q9kjPPnKGS/](http://paste.ubuntu.com/p/Q9kjPPnKGS/)

```
########## wireless info START ##########

Report from: 11 May 2018 13:50 CEST +0200

Booted last: 11 May 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu Communitheme on Xorg

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
	Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 007: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 002 Device 006: ID 03f0:b611 Hewlett-Packard 
Bus 002 Device 005: ID 7392:a611 Edimax Technology Co., Ltd 
Bus 002 Device 004: ID 046d:c084 Logitech, Inc. 
Bus 002 Device 003: ID 046d:c336 Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 004 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1b1c:0c04 Corsair 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              622592  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
wmi_bmof               16384  0
mxm_wmi                16384  0
wmi                    24576  3 asus_wmi,wmi_bmof,mxm_wmi

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
    inet 10.0.0.34/24 brd 10.0.0.255 scope global dynamic noprefixroute eno1
       valid_lft 86117sec preferred_lft 86117sec
    inet6 2a00:1028:96cb:29a6:49b4:27ea:40b9:ec35/64 scope global temporary dynamic 
       valid_lft 172794sec preferred_lft 85808sec
    inet6 2a00:1028:96cb:29a6:bdd5:9776:c098:940d/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 172794sec preferred_lft 86394sec
    inet6 fe80::4e96:daba:282d:b3c2/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

default via 10.0.0.138 dev eno1 proto dhcp metric 100 
10.0.0.0/24 dev eno1 proto kernel scope link src 10.0.0.34 metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 

##### resolv.conf #######################

nameserver 127.0.0.53
search Home

##### network managers ##################

Installed:

	NetworkManager

Running:

root      3705     1  0 May10 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579V Gigabit Network Connection (P8P67 Deluxe Motherboard)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       4ef427e9-6134-36dc-a7c4-ad1f86e997b1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         10.0.0.34/24
IP4.GATEWAY:                            10.0.0.138
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.0.0.138, mt = 100
IP4.ROUTE[2]:                           dst = 10.0.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.0.138
IP4.DOMAIN[1]:                          Home
IP4.WINS[1]:                            10.0.0.138
DHCP4.OPTION[1]:                        requested_wpad = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 10.0.0.0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        vendor_unknown_3561 = 4:6:46:38:38:45:38:35:5:c:46:38:38:45:38:35:37:30:30:43:43:43:6:e:39:36:33:31:36:39:50:2d:31:38:36:31:4e:36
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       expiry = 1526125549
DHCP4.OPTION[11]:                       next_server = 0.0.0.0
DHCP4.OPTION[12]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 10.0.0.138
DHCP4.OPTION[16]:                       dhcp_lease_time = 86400
DHCP4.OPTION[17]:                       ip_address = 10.0.0.34
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       domain_name = Home
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       netbios_name_servers = 10.0.0.138
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       dhcp_message_type = 5
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.138
DHCP4.OPTION[30]:                       domain_name_servers = 10.0.0.138
IP6.ADDRESS[1]:                         2a00:1028:96cb:29a6:49b4:27ea:40b9:ec35/64
IP6.ADDRESS[2]:                         2a00:1028:96cb:29a6:bdd5:9776:c098:940d/64
IP6.ADDRESS[3]:                         fe80::4e96:daba:282d:b3c2/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = 2a00:1028:96cb:29a6::/64, nh = fe80::1, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::1, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[6]:                           dst = 2a00:1028:96cb:29a6::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4ef427e9-6134-36dc-a7c4-ad1f86e997b1 | Wired connection 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Prague (based on set time zone)

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

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[13472.467573] e1000e: eno1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[13472.467577] e1000e 0000:00:19.0 eno1: 10/100 speed: disabling TSO
[13478.027250] e1000e: eno1 NIC Link is Down
[13478.038311] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[13479.785792] e1000e: eno1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[13479.785797] e1000e 0000:00:19.0 eno1: 10/100 speed: disabling TSO
[13479.785831] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[13561.169919] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:f8:8e:85:70:0c:cc:08:00 SRC=10.0.0.138 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13623.461605] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[13686.153605] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:f8:8e:85:70:0c:cc:08:00 SRC=10.0.0.138 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 

########## wireless info END ############
```

---

### Post by praseodym on 2018-05-11
Driver installation

```
sudo apt-get install git build-essential
git clone https://github.com/lwfinger/rtl8723bu
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu
iwconfig
```

---

### Post by Durabys on 2018-05-11
Wifi now works. But I have multiple identical Edimax WiFi tabs. It seems conflicting driver installations...blacklist? But how?

[IMG]https://preview.ibb.co/dYY3Fd/Screenshot_from_2018_05_11_16_54_38.png[/IMG]

Bluetooth continues to **NOT** work. It is still telling me I have to put an USB dongle with Bluetooth on it. But there is already one!

Results: [http://paste.ubuntu.com/p/wbxTNNzQjf/](http://paste.ubuntu.com/p/wbxTNNzQjf/)

---

### Post by Durabys on 2018-05-11
This is the result of iwconfig:

```
lo        no wireless extensions.

eno1      no wireless extensions.

wlx74da389a8562  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlp0s29u1u5i2  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by praseodym on 2018-05-11
See the dmesg output. Deactivate the firewall

---

### Post by Durabys on 2018-05-12
My dmesg output: [https://pastebin.com/raw/S3Rc5i4R](https://pastebin.com/raw/S3Rc5i4R)
Also deactivated firewall.
Bluetooth still not working. Even after a reboot.

---

### Post by praseodym on 2018-05-12
Lets uninstall it

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by Durabys on 2018-05-12
> **praseodym said:**
> Lets uninstall it

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

Result in the Terminal:

```
**XXXX**:~$ sudo apt-get remove --purge ufw gufw
[sudo] password for **XXXX**: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gufw* ufw*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4&#8239;355 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 202342 files and directories currently installed.)
Removing gufw (18.04.0-0ubuntu1) ...
Removing ufw (0.35-5) ...
Skip stopping firewall: ufw (not enabled)
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
(Reading database ... 202084 files and directories currently installed.)
Purging configuration files for ufw (0.35-5) ...
Purging configuration files for gufw (18.04.0-0ubuntu1) ...
dpkg: warning: while removing gufw, directory '/etc/gufw' not empty so not removed
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10) ...
Processing triggers for rsyslog (8.32.0-1ubuntu4) ...
**XXXX**:~$ sudo iptables -t filter -n -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
**XXXX**:~$ sudo iptables -F
**XXXX**:~$ sudo iptables -X
**XXXX**:~$ 

```

Also. No change those duplicates are still there.

---

### Post by Durabys on 2018-05-13
Hello? Can someone help please?

---

### Post by jeremy31 on 2018-05-13
What results for ```
modinfo rtl8723bu
```

For bluetooth do
```
cd /lib/modules/4.15.0-20-generic/kernel/drivers/bluetooth/
sudo mv btusb.ko btusb.ko.bak
sudo wget https://www.dropbox.com/s/uoovkbe7chgh00p/btusb.ko
```

Reboot and see if bluetooth works

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> What results for ```
modinfo rtl8723bu
```

modinfo: ERROR: Module rtl8723bu not found.

> **jeremy31 said:**
> 
For bluetooth do
[code]cd /lib/modules/4.15.0-20-generic/kernel/drivers/bluetooth/
sudo mv btusb.ko btusb.ko.bak

mv: cannot stat 'btusb.ko': No such file or directory

Not working either.

---

### Post by jeremy31 on 2018-05-14
What about ```
modinfo 8723bu
```
Did you run the third command for the bluetooth after ```
cd /lib/modules/4.15.0-20-generic/kernel/drivers/bluetooth/
```

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> What about ```
modinfo 8723bu
```
```
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/8723bu.ko
version:        v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     E503D6BFCA3F30554C0034F
alias:          usb:v7392pA611d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB720d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
retpoline:      Y
name:           8723bu
vermagic:       4.15.0-20-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_btcoex_enable:Enable BT co-existence mechanism (int)
parm:           rtw_ant_num:Antenna number setting (int)
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
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
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
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
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

```


> **jeremy31 said:**
> 
Did you run the third command for the bluetooth after ```
cd /lib/modules/4.15.0-20-generic/kernel/drivers/bluetooth/
```

This came out:
```
--2018-05-14 17:17:03--  https://www.dropbox.com/s/uoovkbe7chgh00p/btusb.ko
Resolving www.dropbox.com (www.dropbox.com)... 2620:100:6022:1::a27d:4201, 162.125.66.1
Connecting to www.dropbox.com (www.dropbox.com)|2620:100:6022:1::a27d:4201|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://dl.dropboxusercontent.com/content_link/yJjNZUixLei6nR7kXgLONTkMLlWCvsVelTJAOMLpZiMlzBw8LmXdQ25DGfh6AL6n/file [following]
--2018-05-14 17:17:03--  https://dl.dropboxusercontent.com/content_link/yJjNZUixLei6nR7kXgLONTkMLlWCvsVelTJAOMLpZiMlzBw8LmXdQ25DGfh6AL6n/file
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 2620:100:6022:6::a27d:4206, 162.125.66.6
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|2620:100:6022:6::a27d:4206|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 73664 (72K) [application/octet-stream]
Saving to: ‘btusb.ko’

btusb.ko                 100%[==================================>]  71,94K  --.-KB/s    in 0,02s   

2018-05-14 17:17:05 (2,83 MB/s) - ‘btusb.ko’ saved [73664/73664]

```

---

### Post by jeremy31 on 2018-05-14
To fix the 2 interface issue
```
sudo sed -i 's/EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE/#EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE/' ~/rtl8723bu/Makefile
cd rtl8723bu
make clean
make
sudo make install
```
Reboot

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> To fix the 2 interface issue
```
sudo sed -i 's/EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE/#EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE/' ~/rtl8723bu/Makefile
cd rtl8723bu
make clean
make
sudo make install
```
Reboot
Wifi now has only one option and connected successfully and Bluetooth has been activated...but still ***cannot*** connect to any device. Phone, Handset. Anything.

---

### Post by jeremy31 on 2018-05-14
Ok, lets add to the wifi so it won't have to be compiled after every new kernel
```
sudo apt install dkms
sudo dkms add ./rtl8723bu
```

What are the results for ```
dmesg | egrep -i 'blue|firm'
```

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> Ok, lets add to the wifi so it won't have to be compiled after every new kernel
```
sudo apt install dkms
sudo dkms add ./rtl8723bu
```

What are the results for ```
dmesg | egrep -i 'blue|firm'
```
Here:
```
[    2.565125] usb 2-1.6: Product: Edimax Wi-Fi N150 Bluetooth4.0 USB Adapter
[   18.077227] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   18.494565] Bluetooth: Core ver 2.22
[   18.494582] Bluetooth: HCI device and connection manager initialized
[   18.494585] Bluetooth: HCI socket layer initialized
[   18.494586] Bluetooth: L2CAP socket layer initialized
[   18.494591] Bluetooth: SCO socket layer initialized
[   18.819763] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   18.819764] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   18.820081] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   18.820082] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   18.821757] Bluetooth: hci0: rom_version status=0 version=1
[   18.821760] Bluetooth: hci0: cfg_sz 0, total size 22496
[   25.547226] audit: type=1400 audit(1526317844.763:75): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2129 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   25.547393] audit: type=1400 audit(1526317844.763:76): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2129 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   25.548100] audit: type=1400 audit(1526317844.767:77): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2130 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   25.857294] audit: type=1400 audit(1526317845.075:78): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2162 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   25.857717] audit: type=1400 audit(1526317845.075:79): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2163 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   25.857861] audit: type=1400 audit(1526317845.075:80): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2163 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   26.103749] audit: type=1400 audit(1526317845.319:81): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2193 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   26.104137] audit: type=1400 audit(1526317845.323:82): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2192 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   26.104272] audit: type=1400 audit(1526317845.323:83): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2192 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0


```

---

### Post by jeremy31 on 2018-05-14
Did you install a bluez snap package, if you did, remove it

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> Did you install a bluez snap package, if you did, remove it
Removed and rebooted. Still doesn't work.

---

### Post by Durabys on 2018-05-14
This is the result. Bluez is still somewhat there:
```
[    2.557097] usb 2-1.6: Product: Edimax Wi-Fi N150 Bluetooth4.0 USB Adapter
[   14.246951] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   14.888788] Bluetooth: Core ver 2.22
[   14.888803] Bluetooth: HCI device and connection manager initialized
[   14.888805] Bluetooth: HCI socket layer initialized
[   14.888807] Bluetooth: L2CAP socket layer initialized
[   14.888810] Bluetooth: SCO socket layer initialized
[   15.044384] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   15.044386] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   15.056503] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   15.056505] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   15.062350] Bluetooth: hci0: rom_version status=0 version=1
[   15.062354] Bluetooth: hci0: cfg_sz 0, total size 22496
[   25.557457] audit: type=1400 audit(1526319768.770:69): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1898 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   25.570712] audit: type=1400 audit(1526319768.782:70): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1894 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   25.581828] audit: type=1400 audit(1526319768.794:71): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1894 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   25.954199] audit: type=1400 audit(1526319769.166:72): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2113 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   25.954536] audit: type=1400 audit(1526319769.166:73): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2112 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   25.954686] audit: type=1400 audit(1526319769.166:74): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2112 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   26.331050] audit: type=1400 audit(1526319769.542:75): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2145 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   26.331681] audit: type=1400 audit(1526319769.542:76): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2144 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   26.331852] audit: type=1400 audit(1526319769.542:77): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2144 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0

```

---

### Post by jeremy31 on 2018-05-14
Either you will have to get apparmor to allow those operations from bluez or figure out how to really get rid of that snap

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> Either you will have to get apparmor to allow those operations from bluez or figure out how to really get rid of that snap

I tried everything. Even going into Synaptic and deleting ANYTHING Bluez and I still get this:
```
[    2.569245] usb 2-1.6: Product: Edimax Wi-Fi N150 Bluetooth4.0 USB Adapter
[   18.587451] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   18.623754] Bluetooth: Core ver 2.22
[   18.623770] Bluetooth: HCI device and connection manager initialized
[   18.623773] Bluetooth: HCI socket layer initialized
[   18.623775] Bluetooth: L2CAP socket layer initialized
[   18.623780] Bluetooth: SCO socket layer initialized
[   18.887148] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   18.887151] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   18.887504] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   18.887506] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   18.889127] Bluetooth: hci0: rom_version status=0 version=1
[   18.889131] Bluetooth: hci0: cfg_sz 0, total size 22496
[   29.056307] audit: type=1400 audit(1526321054.265:69): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1906 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   29.069455] audit: type=1400 audit(1526321054.277:70): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1904 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   29.081519] audit: type=1400 audit(1526321054.289:71): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1904 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   29.453229] audit: type=1400 audit(1526321054.661:72): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2127 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   29.453394] audit: type=1400 audit(1526321054.661:73): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2127 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   29.453967] audit: type=1400 audit(1526321054.661:74): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2128 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   29.834796] audit: type=1400 audit(1526321055.041:75): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=2157 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   29.834929] audit: type=1400 audit(1526321055.041:76): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=2157 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   29.835513] audit: type=1400 audit(1526321055.041:77): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=2156 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0


```Also. BT is still not working.

---

### Post by jeremy31 on 2018-05-14
What results for 
```
snap list
```

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> What results for 
```
snap list
```
Finally manged remove bluez. Still not working bluetooth.
```
xxxx-linux:~$ snap list
Name                  Version                  Rev   Tracking  Developer     Notes
canonical-livepatch   8.0.1                    39    stable    canonical     -
core                  16-2.32.6                4571  stable    canonical     core
discord               0.0.5                    64    stable    snapcrafters  -
gimp                  2.10.0                   38    stable    snapcrafters  -
gnome-3-26-1604       3.26.0                   64    stable/…  canonical     -
gnome-calculator      3.28.1                   167   stable/…  canonical     -
gnome-characters      3.28.0                   86    stable/…  canonical     -
gnome-logs            3.28.0                   31    stable/…  canonical     -
gnome-system-monitor  3.26.0                   39    stable/…  canonical     -
notepad-plus-plus     7.5.6                    42    stable    mmtrt         -
skype                 8.20.0.9                 30    stable    skype         classic
spotify               1.0.77.338.g758ebd78-41  13    stable    spotify       -
vlc                   3.0.1-4-g14a4897         190   stable    videolan      -
xxxx-linux:~$ dmesg | egrep -i 'blue|firm'
[    2.569240] usb 2-1.6: Product: Edimax Wi-Fi N150 Bluetooth4.0 USB Adapter
[   25.923848] Bluetooth: Core ver 2.22
[   25.923860] Bluetooth: HCI device and connection manager initialized
[   25.923863] Bluetooth: HCI socket layer initialized
[   25.923865] Bluetooth: L2CAP socket layer initialized
[   25.923868] Bluetooth: SCO socket layer initialized
[   25.930375] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   25.930377] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   25.931417] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   25.931419] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   25.933375] Bluetooth: hci0: rom_version status=0 version=1
[   25.933379] Bluetooth: hci0: cfg_sz 0, total size 22496
[   25.975103] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
xxxx-linux:~$ 

```

---

### Post by jeremy31 on 2018-05-14
Try ```
bluetoothctl
```
Followed by
```
power on
scan on
```

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> Try ```
bluetoothctl
```
Got this:
```
Command 'bluetoothctl' not found, but can be installed with:

sudo snap install bluez
sudo apt  install bluez

See 'snap info bluez' for additional versions.

```

> **jeremy31 said:**
> 
Followed by
```
power on
scan on
```
Cannot get to this point because of the above.
Also I tried this:
```

xxxx-linux:~$ snap info bluez
name:      bluez
summary:   Bluez for Ubuntu
publisher: canonical
contact:   https://code.launchpad.net/~snappy-hwe-team/snappy-hwe-snaps/+git/bluez
license:   GPL-2.0
description: |
  no description
snap-id: JmzJi9kQvHUWddZ32PDJpBRXUpGRxvNS
channels:                     
  stable:    5.44-3     (129) 3MB -
  candidate: 5.44-3     (129) 3MB -
  beta:      5.44-3     (129) 3MB -
  edge:      5.47-1-dev (144) 4MB -
```

---

### Post by jeremy31 on 2018-05-14
Just try ```
sudo apt install bluez
```

---

### Post by Durabys on 2018-05-14
> **jeremy31 said:**
> Just try ```
sudo apt install bluez
```
It is starting to work. But right as I connect my smartphone it disconects.

```
xxxx-linux:~$ sudo apt install bluez
[sudo] password for xxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bluez
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 943 kB of archives.
After this operation, 4&#8239;596 kB of additional disk space will be used.
Get:1 http://ftp.cvut.cz/ubuntu bionic/main amd64 bluez amd64 5.48-0ubuntu3 [943 kB]
Fetched 943 kB in 0s (4&#8239;396 kB/s)
Selecting previously unselected package bluez.
(Reading database ... 201044 files and directories currently installed.)
Preparing to unpack .../bluez_5.48-0ubuntu3_amd64.deb ...
Unpacking bluez (5.48-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (237-3ubuntu10) ...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Setting up bluez (5.48-0ubuntu3) ...
Created symlink /etc/systemd/system/dbus-org.bluez.service &#8594; /lib/systemd/system/bluetooth.service.
Created symlink /etc/systemd/system/bluetooth.target.wants/bluetooth.service &#8594; /lib/systemd/system/bluetooth.service.
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10) ...
xxxx-linux:~$ bluetoothctl
[NEW] Controller 74:DA:38:9A:85:63 BLACK-DEMON-LINUX [default]
Agent registered
[bluetooth]# power on
Failed to set power on: org.bluez.Error.Blocked
[CHG] Controller 74:DA:38:9A:85:63 Discoverable: yes
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[CHG] Controller 74:DA:38:9A:85:63 Discoverable: no
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[CHG] Controller 74:DA:38:9A:85:63 Discoverable: yes
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[CHG] Controller 74:DA:38:9A:85:63 Class: 0x00000104
[CHG] Controller 74:DA:38:9A:85:63 Powered: yes
[CHG] Controller 74:DA:38:9A:85:63 Discovering: yes
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[NEW] Device 23:64:E5:90:99:0B 23-64-E5-90-99-0B
[NEW] Device 40:CB:C0:B9:56:1E 40-CB-C0-B9-56-1E
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[CHG] Controller 74:DA:38:9A:85:63 Discoverable: no
[CHG] Controller 74:DA:38:9A:85:63 Discoverable: yes
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[CHG] Controller 74:DA:38:9A:85:63 DiscoverableTimeout: 0x00000000
[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.InProgress
[NEW] Device A0:E4:53:A3:D0:75 TJ Xperia
[CHG] Device A0:E4:53:A3:D0:75 Connected: yes
[CHG] Device A0:E4:53:A3:D0:75 Modalias: usb:v0FCEp0193d0010
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001116-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000111f-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 8e780202-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 8e780622-3c51-11e1-8d8d-001cc4d601d8
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: fa87c0d0-afac-11de-8a39-0800200c9a67
[CHG] Device A0:E4:53:A3:D0:75 ServicesResolved: yes
[CHG] Device A0:E4:53:A3:D0:75 Paired: yes
[CHG] Device A0:E4:53:A3:D0:75 Trusted: yes
[CHG] Device A0:E4:53:A3:D0:75 ServicesResolved: no
[CHG] Device A0:E4:53:A3:D0:75 Connected: no
[CHG] Device A0:E4:53:A3:D0:75 RSSI: -76
[CHG] Device A0:E4:53:A3:D0:75 RSSI: -66
[DEL] Device A0:E4:53:A3:D0:75 TJ Xperia
[NEW] Device A0:E4:53:A3:D0:75 TJ Xperia
[CHG] Device A0:E4:53:A3:D0:75 Connected: yes
[CHG] Device A0:E4:53:A3:D0:75 Modalias: usb:v0FCEp0193d0010
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001116-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000111f-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 8e780202-0000-1000-8000-00805f9b34fb
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: 8e780622-3c51-11e1-8d8d-001cc4d601d8
[CHG] Device A0:E4:53:A3:D0:75 UUIDs: fa87c0d0-afac-11de-8a39-0800200c9a67
[CHG] Device A0:E4:53:A3:D0:75 ServicesResolved: yes
[CHG] Device A0:E4:53:A3:D0:75 Paired: yes
[CHG] Device A0:E4:53:A3:D0:75 Trusted: yes
[CHG] Device A0:E4:53:A3:D0:75 ServicesResolved: no
[CHG] Device A0:E4:53:A3:D0:75 Connected: no
[NEW] Device 04:A8:2A:F1:11:CA Nokia C2-01
[bluetooth]# 


```

---

### Post by jeremy31 on 2018-05-14
Try ```
connect A0:E4:53:A3:D0:75
```
If might be something that isn't connected constantly unless you are doing a file transfer to the phone

---

### Post by Durabys on 2018-05-15
> **jeremy31 said:**
> Try ```
connect A0:E4:53:A3:D0:75
```
If might be something that isn't connected constantly unless you are doing a file transfer to the phone

This happened:
```
xxxx-linux:~$ bluetoothctl
[NEW] Controller 74:DA:38:9A:85:63 BLACK-DEMON-LINUX [default]
[NEW] Device 23:64:E5:90:99:0B 23-64-E5-90-99-0B
[NEW] Device A0:E4:53:A3:D0:75 TJ Xperia
Agent registered
[NEW] Device 40:CB:C0:B9:56:1E 40-CB-C0-B9-56-1E
[bluetooth]# connect A0:E4:53:A3:D0:75
Attempting to connect to A0:E4:53:A3:D0:75
Failed to connect: org.bluez.Error.Failed

```

---

### Post by Durabys on 2018-05-16
Hello? The Bluetooth is still not woking as I pointed above. Please help.

---

### Post by jeremy31 on 2018-05-16
File a bug report.  Start at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by tony-whelan on 2018-07-01
[QUOTE=Durabys;13765618]Wifi now works. But I have multiple identical Edimax WiFi tabs. It seems conflicting driver installations...blacklist? But how?

This relates to your duplicate Wifi tabs. I found this 'fix' but have lost the URL for it, sorry.

Before you run the "make" command, edit the file called Makefile.
Put a # in front of the line that says "EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE"
This will disable concurrent mode (no, I don't know what that is).

Save the changes, and then run the make command etc.

When you restart, there should only be one Edimax wifi instead of the two you had before.

That's working for me on Mint 18.3 so hopefully will work for you.

EDIT: just realised this had already been suggested earlier in this thread and worked for the OP.

---

### Post by njrob on 2018-11-05
Hello there,

Sorry to barge into the thread mid trip, but I am also having a related issue.  I don't know how to use the forum as well as might be expected, so please bear with me.

Strangely, I have bluetooth detected by Ubuntu 18.04, but not wifi.  I haven't tried connecting a bluetooth device however, so I don't know whether it's functional.

If somebody could please direct me to where this "sticky thread" is that I use to output my machine status I would appreciate it.

Thanks!

---

### Post by chili555 on 2018-11-05
> **njrob said:**
> Hello there,

Sorry to barge into the thread mid trip, but I am also having a related issue.  I don't know how to use the forum as well as might be expected, so please bear with me.

Strangely, I have bluetooth detected by Ubuntu 18.04, but not wifi.  I haven't tried connecting a bluetooth device however, so I don't know whether it's functional.

If somebody could please direct me to where this "sticky thread" is that I use to output my machine status I would appreciate it.

Thanks!Here it is: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

