---
title: "No Wi-Fi adapter found"
date: 2018-02-23
forum: Networking &amp; Wireless
---

### Post by ricardosilva on 2018-02-23
Hello!
I'm new to Ubuntu. I have installed version 17.10 on my laptop, but I can only acess internet via cable.
In Settings - Wi-Fi there is a message No Wi-Fi Adapter Found

How can I know which Wi-Fi adapter drivers I need (assuming that is the problem), and how do I install them?

I am using a dual boot, and Windows 10 works fine.
I am sorry if this is already answered somewhere else and I am starting a new thread, please just move this message then, it is also my first time using these forums.

---

### Post by wildmanne39 on 2018-02-23
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by Clickster on 2018-02-23
What is the wireless adapter? (name, model) During the setup/update portion of the install - did you check the box for third party software/drivers?

---

### Post by ricardosilva on 2018-02-23
```
########## wireless info START ##########

Report from: 23 Feb 2018 16:24 WET +0000

Booted last: 23 Feb 2018 00:00 WET +0000

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful

##### kernel ############################

Linux 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:832b]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
	Subsystem: Hewlett-Packard Company Device [103c:8319]
	Kernel modules: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05c8:03ac Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

wl                   6447104  0
cfg80211              614400  1 wl
hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  3 intel_hid,intel_vbtn,hp_wmi
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
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.196.19/24 brd 192.168.196.255 scope global dynamic eno1
       valid_lft 344sec preferred_lft 344sec
    inet6 fe80::1b89:dc0c:b360:c5d9/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.196.254 dev eno1 proto static metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.196.0/24 dev eno1 proto kernel scope link src 192.168.196.19 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

search labmat

##### network managers ##################

Installed:

	NetworkManager

Running:

root       923     1  0 16:14 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f1cd1a63-237c-343e-b135-cbb8cff4ae76
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f1cd1a63-237c-343e-b135-cbb8cff4ae76 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.196.19/24
IP4.GATEWAY:                            192.168.196.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.196.254
IP4.DOMAIN[1]:                          labmat
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1519403407
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.196.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.196.19
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = labmat
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.196.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 600
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.196.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.196.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.196.254
IP6.ADDRESS[1]:                         fe80::1b89:dc0c:b360:c5d9/64
IP6.GATEWAY:                            --

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

Region: Europe/Lisbon (based on set time zone)

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

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.13.0-36-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     E179A1F6EAA13B7BC9AF7C6
depends:        cfg80211
name:           wl
vermagic:       4.13.0-36-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-36-generic SMP mod_unload 
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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-snap.network-manager.rules]
# network-manager
KERNEL=="rfkill", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="ppp", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="tty[A-Z]*[0-9]*", TAG+="snap_network-manager_networkmanager"
TAG=="snap_network-manager_networkmanager", RUN+="/lib/udev/snappy-app-dev $env{ACTION} snap_network-manager_networkmanager $devpath $major:$minor"

##### dmesg #############################

[   26.121336] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   26.271044] r8169 0000:02:00.0 eno1: link down (repeated 2 times)
[   26.271194] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   28.099961] r8169 0000:02:00.0 eno1: link up
[   28.099979] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   28.946305] r8169 0000:02:00.0 eno1: link down
[   30.567881] r8169 0000:02:00.0 eno1: link up
[   36.615935] r8169 0000:02:00.0 eno1: link down
[   38.247582] r8169 0000:02:00.0 eno1: link up
[   39.094706] r8169 0000:02:00.0 eno1: link down
[   40.715839] r8169 0000:02:00.0 eno1: link up
[   41.552108] r8169 0000:02:00.0 eno1: link down
[   43.184111] r8169 0000:02:00.0 eno1: link up
[   47.523078] r8169 0000:02:00.0 eno1: link down
[   49.155098] r8169 0000:02:00.0 eno1: link up
[   52.812056] r8169 0000:02:00.0 eno1: link down
[   54.443646] r8169 0000:02:00.0 eno1: link up
[   55.290414] r8169 0000:02:00.0 eno1: link down
[  106.591722] r8169 0000:02:00.0 eno1: link up

########## wireless info END ############
```

---

### Post by wildmanne39 on 2018-02-23
Please do:
```
sudo apt purge bcmwl-kernel-source
```
That command is to remove the driver that you installed for a broadcom device but yours is a realtek device.
To install the driver you need run the following commands one line at a time.

```
git clone https://github.com/smlinux/rtl8723de.git -b 4.11-up
dkms add ./rtl8723de
dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
depmod -a
reboot
```

---

### Post by ricardosilva on 2018-02-23
Problem solved!
I was able to find a solution at HP support
[https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-Linux-driver-available-now-Ubuntu/m-p/6478751#M146150](https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-Linux-driver-available-now-Ubuntu/m-p/6478751#M146150)

Thank you so much for your help, anyway!

---

### Post by ricardosilva on 2018-02-23
I believe it is similar to what you suggested, since I used the same:
dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

command line

---

### Post by ricardosilva on 2018-02-23
sorry, I tried that before seeing your reply

---

### Post by wildmanne39 on 2018-02-23
Looks like the same solution. Please use thread tools at the top of the page to mark the thread solved.

Thanks

---

