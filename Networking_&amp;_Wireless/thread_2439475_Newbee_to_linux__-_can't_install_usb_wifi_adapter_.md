---
title: "Newbee to linux  - can't install usb wifi adapter driver"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by jamiehollis83 on 2020-03-28
Hi everyone.

I installed Ubuntu on my Dell desktop and have enjoyed learning something new.

However, not being overly technical have I made a mistake?

I bought a usb wifi adapter from Amazon - but try as I might I can't install the driver that came with it on a CD (RTL88x2BU_WiFi_linux_v5.3.1)

https://www.amazon.co.uk/dp/B07XCMBLBJ/ref=cm_sw_r_apa_i_5Q1FEbCG1EPD2
(Says Linux compatible - but can see it's not in the communities supported device list). 

I've extracted the driver to desktop and opened a console in the directory the install.sh lives.

run: "sudo bash install.sh" (as google advised)

It runs for some time.....

then I get: Compile make driver error: 2
Please check error Mesg


They seem to be

/home/jamie/Desktop/RTL88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/driver/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/os_dep/osdep_service.c: In function ‘isFileReadable’:
/home/jamie/Desktop/RTL88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/driver/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/os_dep/osdep_service.c:2190:10: error: implicit declaration of function ‘get_ds’; did you mean ‘get_da’? [-Werror=implicit-function-declaration]
   set_fs(get_ds());
          ^~~~~~
          get_da
/home/jamie/Desktop/RTL88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/driver/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/os_dep/osdep_service.c:2190:10: error: incompatible type for argument 1 of ‘set_fs’
In file included from ./include/linux/uaccess.h:11:0,
                 from ./include/linux/sched/task.h:11,
                 from ./include/linux/sched/signal.h:9,
                 from /home/jamie/Desktop/RTL88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/driver/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/include/osdep_service.h:47,
                 from /home/jamie/Desktop/RTL88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/driver/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/include/drv_types.h:27,
                 from /home/jamie/Desktop/RTL88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/driver/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959/os_dep/osdep_service.c:19:
./arch/x86/include/asm/uaccess.h:29:20: note: expected ‘mm_segment_t {aka struct <anonymous>}’ but argument is of type ‘int’
 static inline void set_fs(mm_segment_t fs)
                    ^~~~~~


Any ideas? Thanks so much.

---

### Post by jeremy31 on 2020-03-28
Jamie please see the wireless script link in my signature and post results

---

### Post by jamiehollis83 on 2020-03-28
Thanks Jeremy. I've ran the commands and it's produced the wirelss-info.txt doc as below. Any useful clues in there to the knowing eye?


```
########## wireless info START ##########

Report from: 28 Mar 2020 13:04 GMT +0000

Booted last: 28 Mar 2020 00:00 GMT +0000

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-42-generic #34~18.04.1-Ubuntu SMP Fri Feb 28 13:42:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville) [1028:052c]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 002: ID 1a2c:0e24 China Resource Semico Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

mxm_wmi                16384  1 nouveau
dell_wmi               20480  0
dell_smbios            28672  1 dell_wmi
wmi_bmof               16384  0
sparse_keymap          16384  1 dell_wmi
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
video                  49152  2 dell_wmi,nouveau
wmi                    32768  6 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor,mxm_wmi,nouveau

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
    inet 192.168.1.96/24 brd 192.168.1.255 scope global noprefixroute eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::7770:a139:90b:8763/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eno1 proto dhcp metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.96 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search broadband

##### network managers ##################

Installed:

    NetworkManager

Running:

root       702     1  0 11:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection (Lewisville)
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
GENERAL.CON-UUID:                       5db82ccf-f6b3-3292-8f22-7822e9bebfe8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.96/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          broadband
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        expiry = 1585394596
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        host_name = Jamies-PC
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       domain_name = broadband
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[29]:                       ip_address = 192.168.1.96
IP6.ADDRESS[1]:                         fe80::7770:a139:90b:8763/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::22b0:1ff:feaa:8f4e
DHCP6.OPTION[1]:                        dhcp6_info_refresh_time = 600
DHCP6.OPTION[2]:                        dhcp6_client_id = 0:4:14:ac:6c:97:3b:a1:5b:24:a9:a:53:73:46:e6:48:3e
DHCP6.OPTION[3]:                        dhcp6_name_servers = fe80::22b0:1ff:feaa:8f4e
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = broadband.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:20:b0:1:aa:8f:4e
DHCP6.OPTION[9]:                        dhcp6_inf_max_rt = 60
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5db82ccf-f6b3-3292-8f22-7822e9bebfe8 | Wired connection 1

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

Region: Europe/London (based on set time zone)

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

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

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

[/etc/udev/rules.d/70-snap.network-manager.rules]
# network-manager
KERNEL=="rfkill", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="ppp", TAG+="snap_network-manager_networkmanager"
# ppp
KERNEL=="tty[a-zA-Z]*[0-9]*", TAG+="snap_network-manager_networkmanager"
TAG=="snap_network-manager_networkmanager", RUN+="/usr/lib/snapd/snap-device-helper $env{ACTION} snap_network-manager_networkmanager $devpath $major:$minor"

##### dmesg #############################

[   10.171168] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   10.171228] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2020-03-28
Please check here: [https://askubuntu.com/questions/1175702/trouble-installing-drivers-for-wifi-dongle-compile-make-driver-error-1](https://askubuntu.com/questions/1175702/trouble-installing-drivers-for-wifi-dongle-compile-make-driver-error-1)

---

### Post by jamiehollis83 on 2020-03-28
It works! Thank you so much both of you!

My Ubuntu journey can continue - I honestly thought I was going to have to throw the towel in.

Have a great weekend & stay safe!

---

### Post by chili555 on 2020-03-28
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

