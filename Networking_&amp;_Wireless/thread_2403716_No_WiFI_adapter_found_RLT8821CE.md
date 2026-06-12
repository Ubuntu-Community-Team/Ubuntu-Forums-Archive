---
title: "No WiFI adapter found RLT8821CE"
date: 2018-10-15
forum: Networking &amp; Wireless
---

### Post by v7xda on 2018-10-15
I have a HP Laptop 15g-dr0xxx (4ZD61PA#ACJ) on Ubuntu 18.04.
I can't access WIFI.It shows no WIFI driver found.
I have a RealTek RTL8821CE Wifi adapter.

I tried the solution given in this link but it's not working.
[https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336)

My network info is attached below.

```

########## wireless info START ##########

Report from: 15 Oct 2018 19:16 IST +0530

Booted last: 15 Oct 2018 00:00 IST +0530

Script from: 06 Oct 2018 06:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84a7]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
    Kernel modules: 8821ce

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f2:b65d Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 2a70:f00e  
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

cfg80211              622592  0
hp_wmi                 16384  0
wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
sparse_keymap          16384  2 intel_vbtn,hp_wmi
mxm_wmi                16384  1 nouveau
wmi                    24576  5 wmi_bmof,intel_wmi_thunderbolt,mxm_wmi,nouveau,hp_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp0s20f0u3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.219  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 2405:204:d088:5796:d59b:cad0:4668:8238  prefixlen 64  scopeid 0x0<global>
        inet6 2405:204:d088:5796:fc34:b06a:26dd:d9ad  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::f4a4:3ce7:eed0:41b9  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 25451  bytes 24124661 (24.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16399  bytes 2896872 (2.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2370  bytes 191992 (191.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2370  bytes 191992 (191.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

eno1      no wireless extensions.

enp0s20f0u3  no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20f0u3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20f0u3
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20f0u3

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       944     1  0 19:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20f0u3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         OnePlus
GENERAL.PRODUCT:                        OnePlus
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/net/enp0s20f0u3
GENERAL.IP-IFACE:                       enp0s20f0u3
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       62dbcac8-9058-37ce-ae3b-5fe58467545f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.219/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.219
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1539614203
DHCP4.OPTION[20]:                       host_name = fr3domseeker-HP-Laptop-15g-dr0xxx
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2405:204:d088:5796:d59b:cad0:4668:8238/64
IP6.ADDRESS[2]:                         2405:204:d088:5796:fc34:b06a:26dd:d9ad/64
IP6.ADDRESS[3]:                         fe80::f4a4:3ce7:eed0:41b9/64
IP6.GATEWAY:                            fe80::ec9c:e4ff:fe3b:ef77
IP6.ROUTE[1]:                           dst = 2405:204:d088:5796::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::ec9c:e4ff:fe3b:ef77, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2405:204:d088:5796::bc
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   62dbcac8-9058-37ce-ae3b-5fe58467545f | Wired connection 2

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/eno1
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

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

[[/etc/NetworkManager/system-connections/ADYYYWFyeWE]] (600 root)
[connection] id=ADYYYWFyeWE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ADYYYWFyeWE
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

enp0s20f0u3  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

enp0s20f0u3  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-36-generic SMP mod_unload 
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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   18.416356] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   19.510596] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=826c lmp_ver=08 lmp_subver=a99e
[   19.510598] Bluetooth: hci0: rtl: assuming no firmware upload needed

########## wireless info END ############

```

Secure boot is disabled in BIOS settings.

---

### Post by chili555 on 2018-10-15
What is the exact response to the terminal command:```
sudo modprobe 8821ce
```Is it that the required key is missing? If so, as we suspect, then please check the link you posted where it says:> You also want to make sure SecureBoot is Disabled in the BIOS settings or it won't let you load the unsigned self-complied kernel module.

---

### Post by v7xda on 2018-10-16
> **chili555 said:**
> What is the exact response to the terminal command:```
sudo modprobe 8821ce
```Is it that the required key is missing? If so, as we suspect, then please check the link you posted where it says:

This is the output

```
modprobe: ERROR: could not insert '8821ce': Exec format error
```

SecureBoot is already disabled in the BIOS settings.

---

### Post by chili555 on 2018-10-16
Please try:```
cd rtl8821ce
sudo ./dkms-remove.sh
sudo make clean
git pull
sudo ./dkms-install.sh
sudo modprobe 8821ce
```Is there any improvement?

---

### Post by devenderbhella on 2018-12-28
$ cd rtl8821ce
bash: cd: rtl8821ce: No such file or directory



Device info:
Lenovo AMD® A9-9425 radeon r5, 5 compute cores 2c+3g × 2 

GNOME: 3.30.1
64 bits

---

### Post by chili555 on 2018-12-28
> **devenderbhella said:**
> $ cd rtl8821ce
bash: cd: rtl8821ce: No such file or directory



Device info:
Lenovo AMD® A9-9425 radeon r5, 5 compute cores 2c+3g × 2 

GNOME: 3.30.1
64 bitsPlease start your own new thread and tell us everything you have done so far.

---

