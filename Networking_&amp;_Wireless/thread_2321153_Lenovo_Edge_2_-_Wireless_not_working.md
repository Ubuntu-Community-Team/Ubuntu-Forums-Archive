---
title: "Lenovo Edge 2 - Wireless not working"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by onlinecloud1 on 2016-04-20
I have a Lenovo edge 2, And the wireless is not working. The wireless card is a intel dual band wireless ac b260. It just does not show up in the network settings. It does show up in lspci

---

### Post by RobGoss on 2016-04-20
Hello and welcome, You can add additional drivers by accessing the **Software & Updates - **choose**Additional Drivers **it will scan for the necessary drives needed.

Make sure you have a wired connection to complete this task

---

### Post by onlinecloud1 on 2016-04-20
I have tried that, The only things that show up are intel-microcode and the NVidia drivers

---

### Post by RobGoss on 2016-04-20
What distro are you currently using?

---

### Post by onlinecloud1 on 2016-04-20
Ubuntu

---

### Post by RobGoss on 2016-04-20
> **onlinecloud1 said:**
> Ubuntu

Is it the 14.04, 16.04 which one there are many

You might also want to post the specs for that machine it will help to get you the best solution and fixes

---

### Post by onlinecloud1 on 2016-04-20
15.10

---

### Post by RobGoss on 2016-04-20
Do you see the wireless icon at the top of your **dash** and if so is your wireless connection among that list?

---

### Post by onlinecloud1 on 2016-04-20
No I don't

---

### Post by Hadaka on 2016-04-20
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is ***wireless-info.txt***
Next.
From your directory please copy,paste and post the [B][I]wireless-info.txt

[/I][/B][CODE Tags] ...how to -> [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
thanks.

---

### Post by onlinecloud1 on 2016-04-20
```
########## wireless info START ##########

Report from: 21 Apr 2016 00:27 UTC +0000

Booted last: 21 Apr 2016 00:00 UTC +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/preseed/ubuntu.seed, boot=casper, quiet, splash, ---

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1130]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3835]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 06cb:7b0f Synaptics, Inc. 
Bus 001 Device 003: ID 174f:14e6 Syntek 
Bus 001 Device 002: ID 154b:005d PNY 
Bus 001 Device 007: ID 04e8:6864 Samsung Electronics Co., Ltd GT-I9070 (network tethering, USB debugging enabled)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
video                  36864  3 i915,ideapad_laptop,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enx020800083861 Link encap:Ethernet  HWaddr <MAC 'enx020800083861' [IF]>  
          inet addr:192.168.42.2  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx020800083861' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67647 (67.6 KB)  TX bytes:25768 (25.7 KB)

##### iwconfig ##########################

enx020800083861  no wireless extensions.

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enx020800083861
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx020800083861
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enx020800083861

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1365     1  0 00:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx020800083861
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx020800083861' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enx020800083861
GENERAL.IP-IFACE:                       enx020800083861
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       015366e8-0faf-40ce-8afe-afd9e9523c0a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   015366e8-0faf-40ce-8afe-afd9e9523c0a | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.42.2/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.2
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1461202017
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = ubuntu
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'enx020800083861' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enx020800083861  no frequency information.

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enx020800083861  Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  224.868663] rndis_host 1-2:1.0 enx020800083861: renamed from usb0
[  224.890553] IPv6: ADDRCONF(NETDEV_UP): enx020800083861: link is not ready

########## wireless info END ############
```

---

### Post by wildmanne39 on 2016-04-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by onlinecloud1 on 2016-04-20
> **Wild Man said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Okay.

---

### Post by wildmanne39 on 2016-04-21
Are you running ubuntu from a cd like it looks? If you are just install 15.10 and it should work 15.10 fixes the issues that your wifi card has with ubuuntu.
Thanks

---

### Post by jeremy31 on 2016-04-21
Once installed this can be fixed but try 16.04 as it should work and has long term support

---

### Post by onlinecloud1 on 2016-04-22
I have installed Ubuntu 15.10, but after installation I have the same problem.

---

### Post by onlinecloud1 on 2016-04-22
Well after a while of fiddling I got the wifi working. I upgraded the kernel and installed/upgraded the linux-firmware and the linux-firmware-nonfree packages.

---

