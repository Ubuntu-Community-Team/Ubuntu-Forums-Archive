---
title: "no wifi adapter found"
date: 2017-11-23
forum: Networking &amp; Wireless
---

### Post by betaitam12 on 2017-11-23
Hi, im totaly beginer of ubuntu. i have 17.10 vers. and this is my first Ubuntu.
Generaly almost all works. I have problem with wi-fi.
i have info that "no wifi adapter found". Additional driver are ok (i think so) but wifi still not works.
could sb help?

ps. Laptop Acer Aspire ES1-421

---

### Post by Geoffrey_Arndt on 2017-11-23
What wifi do you have?    If you install "Inxi" and then in a terminal run "inxi -Fx" and post results, it will tell us exactly.

Also, there is a distributor of wifi adapters that work very well with Ubuntu . . . plug it in and select your network.    These adapters are from Panda.   The small laptop nano sized one (Panda Ultra 150 b/g/n) is about $10 on Amazon.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by Norm24 on 2017-11-24
> **Geoffrey_Arndt said:**
> Also, there is a distributor of wifi adapters that work very well with Ubuntu . . . plug it in and select your network.    These adapters are from Panda.   The small laptop nano sized one (Panda Ultra 150 b/g/n) is about $10 on Amazon.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

They used to be around $10 but now they're $40 on Amazon.Newegg has it for$ 23.

Maybe wait for "Cyber Monday" and you could score one cheaper.

---

### Post by jeremy31 on 2017-11-24
*Thread moved to **Networking & Wireless**.*
Post the requested info or see the wireless script link in my signature and post results

---

### Post by betaitam12 on 2017-11-25
Okay....

---

### Post by betaitam12 on 2017-11-25
> **jeremy31 said:**
> *Thread moved to **Networking & Wireless**.*
Post the requested info or see the wireless script link in my signature and post results



```
########## wireless info START ##########


Report from: 25 Nov 2017 20:36 WIB +0700


Booted last: 25 Nov 2017 00:00 WIB +0700


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful


##### kernel ############################


Linux 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu on Xorg


##### lspci #############################


01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1017]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e092]
	Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:57b3 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0489:e096 Foxconn / Hon Hai 
Bus 001 Device 003: ID 1d57:fa20 Xenta 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
wmi_bmof               16384  0
bcma                   53248  0
wmi                    24576  2 wmi_bmof,acer_wmi
video                  40960  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.13  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::8a89:947e:7c3a:f457  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 3867  bytes 2554191 (2.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2816  bytes 363826 (363.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 336  bytes 26576 (26.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 336  bytes 26576 (26.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0f1  no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0f1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0f1


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       697     1  0 20:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp1s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.1/net/enp1s0f1
GENERAL.IP-IFACE:                       enp1s0f1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       93972508-0bbb-3f09-80cc-094d895f4c0f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   93972508-0bbb-3f09-80cc-094d895f4c0f | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.13/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1511702462
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.13
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_lease_time = 86400
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::8a89:947e:7c3a:f457/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = fe80::1/128, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:6:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_info_refresh_time = 86400
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:ce:34:fc:da:78:d3:69:a1:80:dd:d1:bd:84:1a:46:f0


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


##### iw reg get ########################


Region: Asia/Jakarta (based on set time zone)


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


enp1s0f1  no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0f1  Interface doesn't support scanning.


##### module infos ######################


[bcma]
filename:       /lib/modules/4.13.0-17-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F6A6506E1E268D8370FD29D
depends:        
intree:         Y
name:           bcma
vermagic:       4.13.0-17-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


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


##### dmesg #############################


[   13.271366] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   13.271375] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found


########## wireless info END ############
```

---

### Post by jeremy31 on 2017-11-25
You may need to go into BIOS/UEFI settings and disable Secure Boot if your computer has it.  In terminal
```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
Reboot

---

### Post by betaitam12 on 2017-11-28
> **jeremy31 said:**
> You may need to go into BIOS/UEFI settings and disable Secure Boot if your computer has it.  In terminal
```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
Reboot


Thanks Brada, Wifi is ready

---

