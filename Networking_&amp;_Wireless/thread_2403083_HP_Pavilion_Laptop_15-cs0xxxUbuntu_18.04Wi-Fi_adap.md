---
title: "HP Pavilion Laptop 15-cs0xxx|Ubuntu 18.04|Wi-Fi adapter not found"
date: 2018-10-07
forum: Networking &amp; Wireless
---

### Post by muchog on 2018-10-07
I got Ubuntu 18.04 dual boot using a USB but I keep getting that message "Wi-Fi adapter not found". I've searched all over the forums for answers my they are not fixing anything so I decided to post my pc model, I also ran the wi-fi troubleshooting script:

```
########## wireless info START ##########

Report from: 07 Oct 2018 15:39 WEST +0100

Booted last: 07 Oct 2018 00:00 WEST +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84bf]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 05c8:03bc Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
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
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.1.102/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 2841sec preferred_lft 2841sec
    inet6 fe80::3614:c3d:bdb:298e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.254 dev eno1 proto dhcp metric 100 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.102 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       734     1  0 15:26 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ligação com fios 1
GENERAL.CON-UUID:                       c4facd78-18ce-39bb-af00-09d4cb1d8ac3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.102/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_domain_name_servers = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        expiry = 1538925992
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       domain_name = lan
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       ip_address = 192.168.1.102
DHCP4.OPTION[16]:                       requested_subnet_mask = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_netbios_scope = 1
DHCP4.OPTION[19]:                       dhcp_lease_time = 3600
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_static_routes = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::3614:c3d:bdb:298e/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::a6b1:e9ff:fe50:7006
DHCP6.OPTION[1]:                        dhcp6_name_servers = fe80::a6b1:e9ff:fe50:7006
DHCP6.OPTION[2]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:a4:b1:e9:50:70:6
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:17:34:b7:74:a7:d0:b1:f8:c3:a5:7f:e7:1b:5f:fb:a5
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c4facd78-18ce-39bb-af00-09d4cb1d8ac3 | Ligação com fios 1

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
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/hci0.conf]
blacklist hci0

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

[    4.334716] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    4.382611] r8169 0000:03:00.0 eno1: link down (repeated 2 times)
[    4.382719] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    6.299313] r8169 0000:03:00.0 eno1: link up
[    6.299319] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############

```

Can anyone help me? I've been dealing with this issue for days.

---

### Post by jeremy31 on 2018-10-07
Have you tried [https://github.com/RangeeGmbH/rtl8821ce](https://github.com/RangeeGmbH/rtl8821ce)

---

### Post by muchog on 2018-10-07
Yeah I downloaded and rebooted but I still get the same issue

---

### Post by jeremy31 on 2018-10-07
Downloaded, did make and sudo make install?

---

### Post by muchog on 2018-10-07
Yes and now Ubuntu doesn't load, it just stays on the loading screen

---

### Post by jeremy31 on 2018-10-07
Press ESC to see what is holding it up

---

### Post by praseodym on 2018-10-07
SecureBoot is deactivated?

---

### Post by muchog on 2018-10-07
I pressed ESC and it does nothing, it just stay frozen on the screen saying Linux and the 5 little balls underneath

---

### Post by muchog on 2018-10-07
It's my first experience with Linux I don't really know what that is...

---

### Post by jeremy31 on 2018-10-07
Reboot, edit grub to add ```
module_blacklist=8821ce
```
On the line with quiet splash and see if it boots

---

### Post by muchog on 2018-10-07
Where do I do that? On Windows? I can't load Linux so I can't do it there. On the boot menu I don't see any option to edit grub. Sorry in advance, I'm really new at this.

---

### Post by jeremy31 on 2018-10-07
Is the boot menu grub or BIOS/EFI?
If it says Grub then press the e key to edit, scroll down and right to quiet splash and add the rest

---

### Post by muchog on 2018-10-07
It's grub

Basically, I managed to get to the edit part and added what you said, the line ends in "quiet splash $vt_handoff" and I added what you said in the end of this line
I press f10 like they say and Ubuntu does load, but it still says adapter not found. When I go back to the edit menu the line I wrote it's not there and if I do nothing Ubuntu does not load.
Do you know what I'm doing wrong? It's am I writing it in the wrong place or am I not saving it?

---

### Post by jeremy31 on 2018-10-08
What is the result for ```
mokutil --sb-state
```

---

### Post by muchog on 2018-10-08
On the grub command line it says that the command mokutil does not exist.

---

### Post by jeremy31 on 2018-10-08
Change the line in grub so it boots, then in terminal run the ```
mokutil --sb-state
``` command  post results, then do
```
cd rtl8821ce
sudo make uninstall
```
Then you should be able to boot normally

---

### Post by muchog on 2018-10-08
It says "SecureBoot disabled"

Now I'm able to boot normally, but am I not back to the beginning? Still can't get working wifi.

---

### Post by jeremy31 on 2018-10-08
I would do ```
rm -rf rtl8821ce
```
Then try other source code from [https://github.com/search?q=rtl8821ce&ref=opensearch](https://github.com/search?q=rtl8821ce&ref=opensearch)
See if you can find one that works.  I know the one I suggested worked in the past

---

### Post by muchog on 2018-10-08
The first one worked, thank you so much, been dealing with this problem for days. Thanks for the help and patience.

---

