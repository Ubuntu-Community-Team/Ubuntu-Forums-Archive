---
title: "HP Pavillion Gaming 15 Wifi Issue"
date: 2020-10-05
forum: Networking &amp; Wireless
---

### Post by sediizz on 2020-10-05
Dear ALl,

I have an issure with my laptop cannot see the wireless network. Update kernel did fix my issue. However, I need to keep this kernel version, so I re-install my ubuntu and got this issue again.

Here is my wifi script output,

```


########## wireless info START ##########

Report from: 05 Oct 2020 18:47 +07 +0700

Booted last: 05 Oct 2020 00:00 +07 +0700

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-118-generic #119-Ubuntu SMP Tue Sep 8 12:30:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, rd.driver.blacklist=grub.nouveau, rcutree.rcu_idle_gp_delay=1, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822]
    Subsystem: Hewlett-Packard Company Device [103c:85f7]

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 16)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:86d5]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0408:5365 Quanta Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b00c Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 258a:1007  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 hp_wmi,wmi_bmof

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
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 161.200.88.189/25 brd 161.200.88.255 scope global dynamic noprefixroute eno1
       valid_lft 14372sec preferred_lft 14372sec
    inet6 fe80::4f66:71c0:1e2f:7ccc/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF2]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

docker0   no wireless extensions.

eno1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 161.200.88.254 dev eno1 proto dhcp metric 100 
161.200.88.128/25 dev eno1 proto kernel scope link src 161.200.88.189 metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search eng.chula.ac.th

##### network managers ##################

Installed:

    NetworkManager

Running:

root       866     1  0 18:46 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.7/0000:04:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0689be88-d3f4-33f8-ba99-0ecbf9b87d63
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         161.200.88.189/25
IP4.GATEWAY:                            161.200.88.254
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 161.200.88.254, mt = 100
IP4.ROUTE[2]:                           dst = 161.200.88.128/25, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             161.200.80.1
IP4.DOMAIN[1]:                          eng.chula.ac.th
DHCP4.OPTION[1]:                        network_number = 161.200.88.128
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        domain_name = eng.chula.ac.th
DHCP4.OPTION[10]:                       next_server = 192.168.81.54
DHCP4.OPTION[11]:                       broadcast_address = 161.200.88.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       dhcp_lease_time = 14400
DHCP4.OPTION[15]:                       ip_address = 161.200.88.189
DHCP4.OPTION[16]:                       expiry = 1601912817
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.128
DHCP4.OPTION[19]:                       requested_subnet_mask = 1
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       routers = 161.200.88.254
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       domain_name_servers = 161.200.80.1
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.81.54
IP6.ADDRESS[1]:                         fe80::4f66:71c0:1e2f:7ccc/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0689be88-d3f4-33f8-ba99-0ecbf9b87d63 | Wired connection 1

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       130e6553-c14c-49d5-aa66-6cc99be95d93
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.17.0.0/16, nh = 0.0.0.0, mt = 0
IP6.GATEWAY:                            --
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   130e6553-c14c-49d5-aa66-6cc99be95d93 | docker0

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

Region: Asia/Bangkok (based on set time zone)

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

docker0   no frequency information.

eno1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

docker0   Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/blacklist-nouveau.conf]
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

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

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/rtl8822bu-pm.conf]
options 88x2bu rtw_power_mgnt=0 rtw_enusbss=0

[/etc/modprobe.d/rtlwifi-new.conf]
options rtl8188ee swenc=1 ips=0 fwlps=0
options rtl8192ce swenc=1 ips=0 fwlps=0
options rtl8192cu swenc=1
options rtl8192de swenc=1 ips=0 swlps=0
options rtl8192ee swenc=1 ips=0 fwlps=0
options rtl8192se swenc=1 ips=0 swlps=0
options rtl8723ae swenc=1 ips=0 fwlps=0
options rtl8723be swenc=1 ips=0 fwlps=0 ant_sel=2
options rtl8723de swenc=1 ips=0 fwlps=0 ant_sel=2
options rtl8821ae swenc=1 ips=0 fwlps=0
options rtl8822be swenc=1 ips=0 fwlps=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    5.977352] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    6.026711] r8169 0000:04:00.0 eno1: link down (repeated 2 times)
[    6.026819] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    7.639532] r8169 0000:04:00.0 eno1: link up
[    7.639541] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[    9.322094] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready

########## wireless info END ############



```

---

### Post by QIII on 2020-10-05
Hello.


When posting terminal commands and their results, please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by jeremy31 on 2020-10-05
In terminal do 
```
sudo apt install git dkms
git clone https://github.com/lwfinger/rtw88.git
sudo dkms add ./rtw88
sudo dkms install rtlwifi-new/0.6
```

Reboot

---

### Post by sediizz on 2020-11-14
Sorry, for left the forum too long. Your solution is solver my problem thank you so much.

---

### Post by didierm on 2020-12-27
hello
Strange but the WiFi was working when I boot on USB Key to install Ubuntu 20.04 :o

When the install finish, I reboot and the network list is empty :(

```

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:0726]
        Kernel driver in use: rtl8723ae
```


I try to install driver rtw88.
This solution is working for me too (Ubuntu 20.04) :p
THANKS :D

---

