---
title: "Ubuntu 16.04 wifi card is not recognized RTL8723de"
date: 2018-01-02
forum: Networking &amp; Wireless
---

### Post by gunther-rules on 2018-01-02
Hi there,
I've just finished installing the recently published driver for the rtl8723de wifi/bluetooth card on my hp bw 064ng laptop. But this did not solve my problem. I am still missing any options for a wireless connection. Pleas help. I hope you find all the required information below:

```
  
########## wireless info START ##########

Report from: 02 Jan 2018 16:40 CET +0100

Booted last: 02 Jan 2018 00:00 CET +0100

Script from: 05 Dec 2017 03:13 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8332]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    DeviceName:  
    Subsystem: Hewlett-Packard Company Device [103c:8319]

##### lsusb #############################

Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0408:5220 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
ndiswrapper           286720  0
wmi                    16384  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.178.32  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: 2003:c5:dbd4:2d00:75ec:c358:5103:791b/64 Scope:Global
          inet6 addr: 2003:c5:dbd4:2d00:5584:bdd9:2790:7ecd/64 Scope:Global
          inet6 addr: fe80::da54:5ae:98ae:3051/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209874757 (209.8 MB)  TX bytes:6429067 (6.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:157736 (157.7 KB)  TX bytes:157736 (157.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root       784     1  0 16:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kabelnetzwerkverbindung 1
GENERAL.CON-UUID:                       7c629ced-6be6-3060-8e7c-c78ad1703888
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7c629ced-6be6-3060-8e7c-c78ad1703888 | Kabelnetzwerkverbindung 1
IP4.ADDRESS[1]:                         192.168.178.32/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.32
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1515770464
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         2003:c5:dbd4:2d00:5584:bdd9:2790:7ecd/64
IP6.ADDRESS[2]:                         2003:c5:dbd4:2d00:75ec:c358:5103:791b/64
IP6.ADDRESS[3]:                         fe80::da54:5ae:98ae:3051/64
IP6.GATEWAY:                            fe80::3631:c4ff:febc:7fb4
IP6.ROUTE[1]:                           dst = 2003:c5:dbd4:2d00::/56, nh = fe80::3631:c4ff:febc:7fb4, mt = 100
IP6.DNS[1]:                             fd00::3631:c4ff:febc:7fb4
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd00::3631:c4ff:febc:7fb4
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_unknown_86 = 20:3:0:c5:db:d4:2d:0:36:31:c4:ff:fe:bc:7f:b4
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:a9:10:48:10:5f:ed:a1:53:40:99:dd:55:88:4:a6:d0

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[ndiswrapper]
filename:       /lib/modules/4.10.0-42-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     7E15A641541A01799F6564A
depends:        
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

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

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008179sv00008179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000E08Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000818Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000819Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv00008753sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00000812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00006108sd0000168Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00008812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A817sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000B812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000D822sd00007392bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008813sv00008813sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008813sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00008821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A802sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A804sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000B821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00000733sd00002A6Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002483sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002A59sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B001sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E089sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B821sv0000B821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B123sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B125sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B822sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C811sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C823sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000C82Bsv0000C82Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C82Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv0000D723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   18.832769] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   18.832773] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   18.832776] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   18.832778] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   18.832781] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   18.832783] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   18.832786] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   18.832788] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlane'
[   18.833580] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlane; check system log for messages from 'loadndisdriver'
[   19.150109] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   19.150112] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   19.150132] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   19.150134] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   19.150137] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   26.981790] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   27.088339] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   27.088433] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   30.108805] r8169 0000:01:00.0 enp1s0: link up
[   30.108820] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready

########## wireless info END ############


```

sorry, if it shows wrong. This is my first post.
Thanks^^

---

### Post by chili555 on 2018-01-02
What is the exact response to the terminal command:```
sudo modprobe 8723de
```

---

### Post by gunther-rules on 2018-01-02
Hello chili555,
the output is:
```
modprobe: FATAL: Module 8723de not found in directory /lib/modules/4.10.0-42-generic
```

---

### Post by chili555 on 2018-01-02
> I've just finished installing the recently published driver for the rtl8723de wifi/bluetooth cardDo you mean with that low-down, dirty, no good rat called ndiswrapper? You have a little train wreck here:> [   18.832769] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   18.832773] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   18.832776] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   18.832778] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   18.832781] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   18.832783] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   18.832786] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   18.832788] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlane'
[   18.833580] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlane; check system log for messages from 'loadndisdriver'Please confirm that is the driver you meant to install so we can rip it out by its roots and start over.

---

### Post by gunther-rules on 2018-01-02
[https://forum.ubuntuusers.de/topic/ubuntu-findet-keine-drahtlosnetzwerke/2/#post-8917818](https://forum.ubuntuusers.de/topic/ubuntu-findet-keine-drahtlosnetzwerke/2/#post-8917818)

These are the instructions I used. However I have tried to use ndiswrapper before without any succes

---

### Post by jeremy31 on 2018-01-02
Hi, what results for ```
sudo modprobe rtl8723de
```
Using dkms instructions changes the module name

---

### Post by chili555 on 2018-01-02
Please open a terminal and do:```
sudo apt-get purge ndiswrapper*
```Then show us:```
sudo modprobe rtl8723de
```My German is a little rusty.

---

### Post by gunther-rules on 2018-01-02
Well that worked perfectly! I now can select a wireless connection and will never use ndiswrapper again :)
Thank you very much <3

---

### Post by ajaishwal3 on 2018-01-08
gunther-rules I'm facing the same problem on my HP laptop hvng Realtek RTL8723DE. Plz help, how to get wifi?

---

### Post by jeremy31 on 2018-01-08
```
sudo apt-get install git build-essential dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6

```
Reboot

---

### Post by ajaishwal3 on 2018-01-08
#Jeremi31...

I hv already tried that. But still no wifi.

---

### Post by ajaishwal3 on 2018-01-08
#Gunther-rules.. How did u get wifi? Plz explain I hv the same Wireless adapter!

---

### Post by jeremy31 on 2018-01-08
> **ajaishwal3 said:**
> #Jeremi31...

I hv already tried that. But still no wifi.

The question is when did you run those commands?  That github was updated in the past 4 days to support this wireless device
Post results for
```
modinfo rtl8723de
```

---

### Post by chili555 on 2018-01-08
We'd also like to see the exact result of:```
sudo modprobe rtl8723de
```

---

### Post by ajaishwal3 on 2018-01-09
> **jeremy31 said:**
> The question is when did you run those commands?  That github was updated in the past 4 days to support this wireless device
Post results for
```
modinfo rtl8723de
```


 modinfo rtl8723de
modinfo: ERROR: Module rtl8723de not found.

---

### Post by ajaishwal3 on 2018-01-09
sudo modprobe rtl8723de
modprobe: FATAL: Module rtl8723de not found in directory /lib/modules/4.10.0-28-generic

---

### Post by ajaishwal3 on 2018-01-09
> **jeremy31 said:**
> ```
sudo apt-get install git build-essential dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6

```
Reboot



After running above commands, I hv got a wifi option but i'm unable to enable it.

---

### Post by jeremy31 on 2018-01-09
See the wireless script link in my signature and post results

---

### Post by ajaishwal3 on 2018-01-09
> **jeremy31 said:**
> See the wireless script link in my signature and post results

Plz post which cmmand i hv to run... I'm new to linux

---

### Post by jeremy31 on 2018-01-09
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Then run ```
cat wireless-info | nc termbin.com 9999
```
Post the URL that shows in terminal

---

### Post by ajaishwal3 on 2018-01-09
> **jeremy31 said:**
> See the wireless script link in my signature and post results
```

########## wireless info START ##########

Report from: 09 Jan 2018 17:09 IST +0530

Booted last: 09 Jan 2018 00:00 IST +0530

Script from: 05 Dec 2017 03:13 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8328]

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
	DeviceName: WLAN
	Subsystem: Hewlett-Packard Company Device [103c:8319]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2c9b Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 008: ID 2717:ff80  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
rtl8723de              90112  0
btcoexist             425984  1 rtl8723de
phydm_mod             860160  1 rtl8723de
rtl8723_common         24576  1 rtl8723de
rtl_pci                32768  1 rtl8723de
rtlwifi               159744  5 phydm_mod,rtl_pci,btcoexist,rtl8723_common,rtl8723de
mac80211              782336  2 rtl_pci,rtlwifi
cfg80211              602112  2 mac80211,rtlwifi
sparse_keymap          16384  3 intel_hid,intel_vbtn,hp_wmi
wmi                    16384  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp0s20f0u3 Link encap:Ethernet  HWaddr <MAC 'enp0s20f0u3' [IF2]>  
          inet addr:192.168.42.166  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: 2405:204:c284:6a4c:28b2:2bfd:4ea3:e03c/64 Scope:Global
          inet6 addr: 2405:204:c284:6a4c:fc39:b58d:aab:5d4f/64 Scope:Global
          inet6 addr: fe80::9bf:d050:30f3:41af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23612444 (23.6 MB)  TX bytes:3739251 (3.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:278520 (278.5 KB)  TX bytes:278520 (278.5 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eno1      no wireless extensions.

enp0s20f0u3  no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20f0u3
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20f0u3

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       822     1  0 16:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20f0u3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Android
GENERAL.PRODUCT:                        Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20f0u3' [IF2]>
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
GENERAL.CON-UUID:                       36f008b6-c1f9-3c65-8ed3-ce9211bf6f1a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   36f008b6-c1f9-3c65-8ed3-ce9211bf6f1a | Wired connection 2
IP4.ADDRESS[1]:                         192.168.42.166/24
IP4.GATEWAY:                            192.168.42.129
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.166
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 2970
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1620
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1515501330
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = ankit-HP
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         2405:204:c284:6a4c:28b2:2bfd:4ea3:e03c/64
IP6.ADDRESS[2]:                         2405:204:c284:6a4c:fc39:b58d:aab:5d4f/64
IP6.ADDRESS[3]:                         fe80::9bf:d050:30f3:41af/64
IP6.GATEWAY:                            fe80::e9ee:fb6f:b107:cde2
IP6.DNS[1]:                             2405:200:800::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2405:200:800::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:2:50:f3:0:5:1
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:91:6c:f9:51:b4:58:19:96:ae:bd:53:8b:e5:e6:91:3b

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eno1
GENERAL.IP-IFACE:                       
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        Sunrise Point-LP PCI Express Root Port
GENERAL.DRIVER:                         rtl8723de
GENERAL.DRIVER-VERSION:                 4.10.0-42-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

enp0s20f0u3  no frequency information.

lo        no frequency information.

wlo1      13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

wlo1      Interface doesn't support scanning : Network is down

enp0s20f0u3  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723de]
filename:       /lib/modules/4.10.0-42-generic/updates/dkms/rtl8723de.ko
firmware:       rtlwifi/rtl8723defw.bin
description:    Realtek 8723DE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     DB5F059D138EB4060ED55A0
depends:        rtlwifi,rtl_pci,btcoexist,rtl8723-common,phydm_mod
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           dma64:bool
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.10.0-42-generic/updates/dkms/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     5AAF25B4699EF07310A021A
depends:        rtlwifi
vermagic:       4.10.0-42-generic SMP mod_unload 

[rtl_pci]
filename:       /lib/modules/4.10.0-42-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     945FC18DC4434E09F7DEF48
depends:        mac80211,rtlwifi
vermagic:       4.10.0-42-generic SMP mod_unload 

[rtlwifi]
filename:       /lib/modules/4.10.0-42-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     230F50EDC03ADF8FF651BD8
depends:        mac80211,cfg80211
vermagic:       4.10.0-42-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.10.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723de]
ant_sel: 0
aspm: 0
debug_level: 0
debug_mask: 18446744073709551615
disable_watchdog: N
dma64: N
fwlps: N
ips: Y
msi: Y
swenc: N
swlps: N

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   11.090241] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   11.638873] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   11.677825] rtl8723de 0000:02:00.0: Direct firmware load for rtlwifi/rtl8723defw.bin failed with error -2
[   11.677828] rtlwifi: Selected firmware is not available
[   11.704879] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.705185] rtlwifi: rtlwifi: wireless switch is on
[   12.697514] rtl8723de 0000:02:00.0 wlo1: renamed from wlan0
[   12.784584] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   12.784585] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   12.784597] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   12.784598] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   12.784601] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   21.217037] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   21.443673] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   21.597374] r8169 0000:01:00.0 eno1: link down
[   21.597456] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  106.207417] rndis_host 1-3:1.0 enp0s20f0u3: renamed from usb0
[  106.234384] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u3: link is not ready
[ 1552.973910] rndis_host 1-3:1.0 enp0s20f0u3: unregister 'rndis_host' usb-0000:00:14.0-3, RNDIS device
[ 1614.457813] rndis_host 1-3:1.0 enp0s20f0u3: renamed from usb0
[ 1614.494822] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u3: link is not ready

########## wireless info END ############
```

---

### Post by vasa1 on 2018-01-09
> **ajaishwal3 said:**
> Plz post which cmmand i hv to run... I'm new to linux
Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) carefully. It gives you more details.

---

### Post by ajaishwal3 on 2018-01-09
> **vasa1 said:**
> Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) carefully. It gives you more details.

I hv posted my all wireless info... Plz help me ...
I'm a noob..

---

### Post by chili555 on 2018-01-09
> 
[   11.638873] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   11.677825] rtl8723de 0000:02:00.0: Direct firmware load for rtlwifi/rtl8723defw.bin failed with error -2
[   11.677828] rtlwifi: Selected firmware is not available
You need but lack the needed firmware. I believe that it exists in the driver file that you cloned. Let's have a look:```
cd rtlwifi_new/firmware/rtlwifi
sudo cp  *  /lib/firmware/rtlwifi/
```If there are no errors, reboot.

If there are errors, post them here.

---

### Post by ajaishwal3 on 2018-01-09
I hv found this link in facebook group of ubuntu....
[https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-Linux-driver-available-now-Ubuntu/td-p/6477307](https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-Linux-driver-available-now-Ubuntu/td-p/6477307)


The above link works.... Now wifi is wrkng without any problem...

---

### Post by alphacentauri82 on 2018-01-18
It didn't work for me HP 240 G6 Celeron.

---

### Post by chili555 on 2018-01-18
> **alphacentauri82 said:**
> It didn't work for me HP 240 G6 Celeron.Instead of adding to the end of an already long thread, I suggest that you start a new question and add the diagnostic information from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by vvmspace on 2018-10-30
Fixed for Ubuntu 18.10 and earlier:

[https://github.com/vvmspace/rtl8723de.git](https://github.com/vvmspace/rtl8723de.git)
> sudo apt-get install git dkms libelf-dev
git clone [https://github.com/vvmspace/rtl8723de.git](https://github.com/vvmspace/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
sudo reboot

---

