---
title: "Wifi adapter not found on Ubuntu 18.04.4 LTS"
date: 2020-05-28
forum: Networking &amp; Wireless
---

### Post by rach88 on 2020-05-28
Hi guys,
So I installed Ubuntu 18.04.4 LTS (my first time using Ubuntu) on **Asus VivoBook Max F541NA**, and I can't connect to wifi at all, it says Adapter not found.
I know it's not an uncommon problem but I tried many solutions from the internet.
Here the wireless inf log :

```
########## wireless info START ##########

Report from: 29 May 2020 01:11 MSK +0300

Booted last: 29 May 2020 00:00 MSK +0300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 04f2:b52b Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:b721 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 0fce:71e0 Sony Ericsson Mobile Communications AB 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

asus_nb_wmi            28672  0
asus_wmi               32768  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  2 asus_wmi,i915

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
2: enp0s21f0u2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s21f0u2' [IF1]> brd <MAC address>
    inet 192.168.42.140/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s21f0u2
       valid_lft 4056sec preferred_lft 4056sec
    inet6 fe80::ec72:d3c2:c79d:325e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp0s21f0u2  no wireless extensions.

##### route #############################

default via 192.168.42.129 dev enp0s21f0u2 proto dhcp metric 100 
169.254.0.0/16 dev enp0s21f0u2 scope link metric 1000 
192.168.42.0/24 dev enp0s21f0u2 proto kernel scope link src 192.168.42.140 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       736     1  0 00:18 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s21f0u2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Sony
GENERAL.PRODUCT:                        F5122
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s21f0u2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.0/net/enp0s21f0u2
GENERAL.IP-IFACE:                       enp0s21f0u2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
GENERAL.CON-UUID:                       4d78fb02-3f85-3bce-bc15-1badbbbb51ec
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.140/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.140
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 6300
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       dhcp_renewal_time = 3600
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1590707917
DHCP4.OPTION[20]:                       host_name = elouaer-X541NA
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       dhcp_lease_time = 7200
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::ec72:d3c2:c79d:325e/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4d78fb02-3f85-3bce-bc15-1badbbbb51ec | &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1

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

Region: Europe/Moscow (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s21f0u2  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s21f0u2  Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   15.640697] rndis_host 1-2:1.0 enp0s21f0u2: renamed from usb0
[   15.656226] Bluetooth: hci0: RTL: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   15.657188] Bluetooth: hci0: RTL: rtl: loading rtl_bt/rtl8723b_fw.bin
[   15.735705] Bluetooth: hci0: RTL: rtl: loading rtl_bt/rtl8723b_config.bin
[   15.735752] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2

########## wireless info END ############

```


I think the wifi device is : [B]Integrated Wi-Fi 4 (802.11 b/g/n)

[/B]*Thanks,*

---

### Post by chili555 on 2020-05-28
We see no wireless device at all. Is it enabled or disabled in the BIOS/EFI?

---

### Post by rach88 on 2020-05-29
I checked twice, it's enabled, the wifi worked under Win10 before it crashed

---

### Post by rach88 on 2020-05-29
I checked my wifi adapter, it normally connected, i plugged then unplugged it, it's [SIZE=3][B]wcbn611lh-ad(1a) 


[/B][IMG][[IMG]https://image.noelshack.com/minis/2020/22/5/1590754928-dsc-0939.png[/IMG]]("https://www.noelshack.com/2020-22-5-1590754928-dsc-0939.jpg")[/IMG][/SIZE]

---

### Post by chili555 on 2020-05-29
Does it now appear here?

```
lspci -nnk 
```

---

### Post by rach88 on 2020-05-29
> elouaer@elouaer-X541NA:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge [8086:5af0] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge [1043:16a0]
00:00.1 Signal processing controller [1180]: Intel Corporation Device [8086:5a8c] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16a0]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5a85] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device [1043:16a0]
    Kernel driver in use: i915
    Kernel modules: i915
00:0e.0 Audio device [0403]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster [8086:5a98] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster [1043:12e0]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, sof_pci_dev
00:0f.0 Communication controller [0780]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine [8086:5a9a] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine [1043:16a0]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:12.0 SATA controller [0106]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller [8086:5ae3] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller [1043:16a0]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:15.0 USB controller [0c03]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI [8086:5aa8] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI [1043:16a0]
    Kernel driver in use: xhci_hcd
00:16.0 Signal processing controller [1180]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #1 [8086:5aac] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller [1043:16a0]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:17.0 Signal processing controller [1180]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #5 [8086:5ab4] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller [1043:16a0]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:1f.0 ISA bridge [0601]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface [8086:5ae8] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface [1043:16a0]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.1 SMBus [0c05]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller [8086:5ad4] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller [1043:16a0]
    Kernel modules: i2c_i801


I think it doesn't, please double check

---

### Post by jeremy31 on 2020-05-29
Is it enabled in BIOS?  Try a BIOS reset to defaults and see if it works

---

### Post by chili555 on 2020-05-30
We still see no wireless device. If it is for sure enabled in the BIOS/EFI then we must suspect that either the device or the PCI bus is defective.

---

### Post by praseodym on 2020-06-01
Please show

```
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by rach88 on 2020-06-01
> elouaer@elouaer-X541NA:~$ cat /sys/bus/sdio/devices/*
cat: '/sys/bus/sdio/devices/*': &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
elouaer@elouaer-X541NA:~$ cat /sys/bus/sdio/devices/*/uevent
cat: '/sys/bus/sdio/devices/*/uevent': &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;


It says: no such file or catalogue in Russian

---

