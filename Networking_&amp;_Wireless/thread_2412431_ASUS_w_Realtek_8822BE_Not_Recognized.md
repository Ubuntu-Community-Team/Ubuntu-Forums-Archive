---
title: "ASUS w Realtek 8822BE Not Recognized"
date: 2019-02-13
forum: Networking &amp; Wireless
---

### Post by rick1270 on 2019-02-13
I have tried everything... Dual boot with Windows 10... no problem using  the wireless through windows.... connects fine through wired  connections... could really use some help... thanks.

```

########## wireless info START ##########

Report from: 12 Feb 2019 21:14 PST -0800

Booted last: 12 Feb 2019 00:00 PST -0800

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse:  /etc/modprobe.d/r8822be.conf line 1: ignoring bad line starting with  'optionsr882be'

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
    Subsystem: AzureWave Device [1a3b:2950]
    Kernel modules: r8822be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3526 IMC Networks 
Bus 001 Device 003: ID 13d3:5a01 IMC Networks 
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

mac80211              778240  0
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
cfg80211              622592  1 mac80211
mxm_wmi                16384  1 nouveau
wmi                    24576  4 asus_wmi,wmi_bmof,mxm_wmi,nouveau
video                  45056  3 asus_wmi,i915,nouveau

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.1.79/24 brd 192.168.1.255 scope global dynamic noprefixroute enp2s0
       valid_lft 86173sec preferred_lft 86173sec
    inet6 2600:1700:5390:3890::48/128 scope global dynamic noprefixroute 
       valid_lft 3374sec preferred_lft 3374sec
    inet6 2600:1700:5390:3890:2cdc:d4c3:f358:7d6b/64 scope global temporary dynamic 
       valid_lft 3406sec preferred_lft 3406sec
    inet6 2600:1700:5390:3890:270b:f17f:47d5:d9e5/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3406sec preferred_lft 3406sec
    inet6 fe80::a344:96b2:d3d2:c286/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

##### route #############################

default via 192.168.1.254 dev enp2s0 proto dhcp metric 20100 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.1.0/24 dev enp2s0 proto kernel scope link src 192.168.1.79 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       799     1  0 21:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       bdb987f0-8f45-3de1-b27b-c0cec8019536
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.79/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 20100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        ip_address = 192.168.1.79
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = -28800
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.254
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = attlocal.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1550121042
DHCP4.OPTION[22]:                       vendor_unknown_3561 =  4:6:30:30:31:45:34:36:5:e:52:39:31:4e:48:38:4d:51:34:30:33:38:38:33:6:a:42:47:57:32:31:30:2d:37:30:30
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 0.0.0.0
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       requested_host_name = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2600:1700:5390:3890::48/128
IP6.ADDRESS[2]:                         2600:1700:5390:3890:2cdc:d4c3:f358:7d6b/64
IP6.ADDRESS[3]:                         2600:1700:5390:3890:270b:f17f:47d5:d9e5/64
IP6.ADDRESS[4]:                         fe80::a344:96b2:d3d2:c286/64
IP6.GATEWAY:                            fe80::4e12:65ff:fe8c:d530
IP6.ROUTE[1]:                           dst = 2600:1700:5390:3890::/60, nh = fe80::4e12:65ff:fe8c:d530, mt = 100
IP6.ROUTE[2]:                           dst = 2600:1700:5390:3890::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ::/0, nh = fe80::4e12:65ff:fe8c:d530, mt = 20100
IP6.ROUTE[4]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[6]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[7]:                           dst = 2600:1700:5390:3890::48/128, nh = ::, mt = 100
IP6.DNS[1]:                             2600:1700:5390:3890::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:9a:c3:50:d2:38:e9:25:b5:7e:a2:7e:9d:b8:1f:4e:1c
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        dhcp6_name_servers = 2600:1700:5390:3890::1
DHCP6.OPTION[4]:                        rebind = 2880
DHCP6.OPTION[5]:                        max_life = 3600
DHCP6.OPTION[6]:                        preferred_life = 3600
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1550033549
DHCP6.OPTION[10]:                       ip6_address = 2600:1700:5390:3890::48
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       dhcp6_domain_search = attlocal.net.
DHCP6.OPTION[13]:                       renew = 1800
DHCP6.OPTION[14]:                       dhcp6_server_id = 0:1:0:1:23:aa:9d:64:4c:12:65:8c:d5:30
DHCP6.OPTION[15]:                       iaid = 92:35:9f:8c
DHCP6.OPTION[16]:                       starts = 1550033549
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bdb987f0-8f45-3de1-b27b-c0cec8019536 | Wired connection 1

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

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

lo        no frequency information.

enp2s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.15.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     10B87D6D65DDD085D1326C9
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-45-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:grin:efault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-45-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:grin:isable 40MHz support in the 2.4GHz band (bool)

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/r8822be.conf]
optionsr882be aspm=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    8.298351] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    8.346580] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[    8.346681] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   11.524570] r8169 0000:02:00.0 enp2s0: link up
[   11.524577] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2019-02-13
Please run the terminal command:```

sudo modprobe r8822be && dmesg | grep r88
```Next, post the result.

--------------------

Possible reference: [https://askubuntu.com/questions/1099200/wi-fi-stopped-working-on-ubuntu-18-10-with-linux-4-18-0-12/1099438#1099438](https://askubuntu.com/questions/1099200/wi-fi-stopped-working-on-ubuntu-18-10-with-linux-4-18-0-12/1099438#1099438)

---

### Post by rick1270 on 2019-02-13
Secure Boot is disabled...

rick1270@rick1270-X705UNR:~$ sudo modprobe r8822be && dmesg | grep r88
[sudo] password for rick1270: 
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/r8822be.conf line 1: ignoring bad line starting with 'optionsr882be'
modprobe: ERROR: could not insert 'r8822be': Required key not available

---

### Post by chili555 on 2019-02-13
You are apparently also subject to the bug I referenced above. I suggest that you disable secure boot in the BIOS/EFI and remove the faulty file:```
sudo rm /etc/modprobe.d/r8822be.conf 
```Your wireless should then be working.

---

### Post by rick1270 on 2019-02-13
No luck... ran the code and restarted... still not seeing wireless adapter

---

### Post by chili555 on 2019-02-13
> **rick1270 said:**
> No luck... ran the code and restarted... still not seeing wireless adapterAnd what about secure boot?

---

### Post by rick1270 on 2019-02-13
That worked! I had disabled Fast Boot but not Secure Boot... Thank you very much

---

